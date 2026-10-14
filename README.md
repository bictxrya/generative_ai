# Do4Love Post Helper

An AI-assisted tool that helps small sustainability-driven brand founders turn
event photos and rough notes into an ordered photo set and on-voice captions
that use only facts the founder provides. The founder reviews everything and
posts manually.

## What the first working slice does
A user adds event photos (any number), rough notes, a voice guide, and links to
past posts (up to three), then presses Draft. The prototype shows the photos in
a suggested order with a short reason for each, a "Set aside" section, and 2-3
captions with a facts panel that marks each fact as found or not found in the
notes and highlights sustainability claims. Each caption has a "Copy caption"
button. Nothing posts automatically; the founder copies the caption and posts
from Instagram themselves.

## Try it
[[Replit link: https://do-4-love-post-helper.replit.app]
Click "Use sample event," then "Draft." You can also upload your own photos and
type your own notes, but the results are prewritten (see AI status).

## AI status
**Intended AI:** A vision model tags and ranks photos for brand fit and variety
and explains each pick, with code filtering blurry shots and near-duplicates. A
language model reads the founder's past posts and voice guide, drafts captions
in the brand's voice, and checks their facts against the notes. The tool never
identifies people, and the founder makes every final choice.

**Working now:**
- Photo upload and thumbnails (any number of photos)
- Input validation (missing photos, empty notes, missing or malformed post links)
- The full flow from input to result, "Copy caption" buttons, and "Start over"

**Simulated or manual:**
- Photo ordering uses the photos the user uploaded, but follows a fixed rule
  (upload order, first 10 shown as suggested, the rest set aside). It does not
  analyze the images, and the reasons are generic.
- All captions, facts panels, and sustainability-claim highlights are prewritten.
  I generated them beforehand with Claude from my real event notes and pasted
  them into the app.
- Which result appears depends only on simple rules (keywords in the notes), not
  on what the photos or notes actually mean.
- **Past post links are accepted and displayed, but not fetched or read.** Voice
  matching is simulated, so changing the links does not change the captions.
- No live model, backend, or database. No API keys are in this repo.

**Deliberately not included:** auto-posting or scheduling. The founder reviews
and posts manually.

## Test results
| Test | Input or action | What happened | Pass, partial, or fail |
| --- | --- | --- | --- |
| Typical case | "Use sample event," then Draft | | |
| Challenge case | Notes include "made with recycled materials" and "make it sound very sustainable," with a photo clearly showing an attendee | | |
| Invalid or empty case | (a) Draft with nothing entered; (b) a post link without https:// (e.g., "instagram.com/p/abc") | | |

## Known limitations
1. **Results are prewritten and don't respond to the actual photos or notes.**
   Different photos can get the same reasons and captions, and the ordering is
   just upload order. Next step: connect a vision model and a language model, then
   check whether the picks match my taste.
2. **Past post links are saved but not read.** Instagram blocks other sites from
   fetching posts, so a real version would need pasted caption text or an
   official API. Next step: have the user paste caption text as the voice
   reference.
3. **Posting is manual and there are no swap or edit controls.** This keeps the
   founder in control, but the founder can't reorder photos or edit captions in
   the app yet. Next step: add swap and in-place editing; auto-posting would
   come later and only after explicit approval.
