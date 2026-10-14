# Do4Love Post Helper

An AI-assisted tool that helps small sustainability-driven brand founders turn
event photos and rough notes into a reviewable photo selection and on-voice
captions that use only facts the founder provides.

## What the first working slice does
A user adds event photos, rough notes, a voice guide, and links to past posts
(up to three), then presses Draft. The prototype shows suggested photos in
order with a reason for each, set-aside photos with reasons, and 2-3 captions
with a facts panel that marks each fact as found or not found in the notes and
highlights sustainability claims. Nothing posts automatically.

## Try it
[Replit link]
Click "Use sample event," then "Draft." You can also upload your own photos and
type your own notes, but the results shown are prewritten (see AI status).

## AI status
**Intended AI:** A vision model tags and ranks photos, explains each pick, and
sets aside blurry shots and near-duplicates (code handles the blur and duplicate
filtering). A language model reads the founder's past posts and voice guide,
drafts captions in the brand's voice, and checks their facts against the notes.
The tool never identifies people, and the founder makes every final choice.

**Working now:**
- Photo upload and thumbnails
- Input validation (missing photos, empty notes, missing or malformed post links)
- The full flow from input to result, with a "Start over" button

**Simulated or manual:**
- All photo picks, reasons, captions, and fact checks are prewritten. I generated
  them beforehand with Claude from my real event photos and notes and pasted
  them into the app.
- Which prewritten result appears depends only on simple rules (photo count and
  keywords in the notes), not on what the photos or notes actually contain.
- **Past post links are accepted and displayed, but not fetched or read.**
  Voice matching is simulated, so changing the links does not change the captions.
- No live model, backend, or database. No API keys are in this repo.

## Test results
| Test | Input or action | What happened | Pass, partial, or fail |
| --- | --- | --- | --- |
| Typical case | "Use sample event" (25 photos, notes, 2 post links), then Draft | | |
| Challenge case | Notes include "made with recycled materials" and "make it sound very sustainable," with one photo clearly showing an attendee | | |
| Invalid or empty case | (a) Draft with nothing entered; (b) 5 photos and two lines of notes; (c) a post link without https:// (e.g., "instagram.com/p/abc") | | |

## Known limitations
1. **Results are prewritten and don't respond to the actual inputs.** Different
   photos, notes, or post links can produce the same output. Next step: connect
   a vision model and a language model and check whether the picks match my taste.
2. **Past post links are saved but not read.** Instagram blocks other sites from
   fetching posts, so a real version would need pasted caption text or an
   official API. Next step: have the user paste caption text and use it as the
   voice reference.
3. **No swap, reorder, or caption-editing controls yet.** These are central to
   the founder keeping final say. Next step: add swap and in-place editing.
