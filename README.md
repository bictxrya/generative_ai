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
[[Replit link: (https://do-4-love-post-helper.replit.app/do4love-post-helper/)]
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
| Typical case | Clicked "Use sample event," then Draft | The full flow worked: three captions appeared with "Copy caption" buttons and the "Nothing posts automatically" line. However, every fact in the facts panel was marked "Not in notes" and the captions were generic, so the panel did not demonstrate the facts check. | Partial |
| Challenge case | Notes included "made with recycled materials" and a request to make it "very sustainable," with an attendee visible in a photo | The sustainability claim was kept as written with "no numbers added," was visibly highlighted, and was not upgraded. One photo was flagged "person prominent, not identified." Unsupported statements such as "shared a meal" were marked "Not in notes." However, the captions repeated my notes word for word, and some filler statements did not fit the event. | Partial |
| Invalid or empty case | (a) Draft with every field empty; (b) "instagram.com/p/abc" as a post link | (a) Stayed on the input screen and showed three inline errors (notes, photos, past post link). No dead end. (b) The error "Paste a full link starting with https://" appeared under Sample post 1. | Pass |

## Known limitations
1. **Sample captions are generic.** The typical case marks every fact "Not in notes," so it doesn't show a "Found in notes" result. Next step: write the sample captions from my real event notes.
2. **Results are prewritten and don't respond to the actual photos or notes.** The photo order is just upload order. Next step: connect a vision model and a language model.
3. **Past post links are saved but not read.** Instagram blocks fetching posts, so a real version would need pasted caption text. Next step: use pasted caption text as the voice reference.
