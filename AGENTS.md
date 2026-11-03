# W3C meeting minutes generation

Generate HTML minutes for a W3C group meeting from raw IRC logs and (optionally) a VTT transcription.

## Input

- The W3C **group shortname** (`SHORTNAME`), e.g. `webmachinelearning`. All filenames and URLs below substitute this shortname.
- The target meeting **date** (`YYYY-MM-DD`). All filenames and URLs below substitute this date.
- If either the shortname or date is ambiguous or missing, ask before proceeding.

## Prerequisites

- `curl` (for fetching remote resources) and internet access.
- `git` and Perl (for running scribe2). Clone https://github.com/w3c/scribe2 locally if not already present and install any Perl module dependencies it requires.
- Expected/derived local files (all in the working directory):
  - `YYYY-MM-DD-SHORTNAME-irc.txt` — raw IRC minutes (copied).
  - `YYYY-MM-DD-SHORTNAME.vtt` — transcription (optional, provided if available).
  - `YYYY-MM-DD-SHORTNAME-irc-edited.txt` — working edited minutes.
  - `YYYY-MM-DD-SHORTNAME-minutes-edited.html` — final output.

## Steps

> **Preserve resolutions.** Lines annotated with `RESOLUTION:` in the raw minutes are human-generated and authoritative. Never edit, reword, reformat, or remove them during any post-processing step — copy them through verbatim, including the leading IRC handle (keep the exact handle on these lines for clear attribution rather than replacing it with a name).

> **Preserve bot and system lines.** Keep lines from automated agents verbatim — especially the GitHub bot `gb`, whose `-> Issue N ...` / `-> PR N ...` expansion lines scribe2 renders as issue/PR boxes (e.g. `<gb> https://github.com/ORG/REPO/issues/252 -> Issue 252 ... (by author)`). Do not delete these lines or replace their handles with participant names. This also applies to `RRSAgent` and `Zakim` lines. Handle replacement (step 4) applies only to human speakers.

1. **Fetch raw minutes.** Copy the original raw IRC minutes from
   `https://www.w3.org/YYYY/MM/DD-SHORTNAME-irc`
   to `YYYY-MM-DD-SHORTNAME-irc.txt`, e.g.:
   ```
   curl -fsS https://www.w3.org/YYYY/MM/DD-SHORTNAME-irc -o YYYY-MM-DD-SHORTNAME-irc.txt
   ```
   These contain agenda topics, human-written minutes with resolutions, and timestamps where the chair acknowledges a speaker (`ack IRC_handle`).
   If the fetch is not HTTP 200 (e.g. 404), stop and report — the minutes may not be published yet.

2. **Create the working copy.** Copy the raw file to
   `YYYY-MM-DD-SHORTNAME-irc-edited.txt`. All edits happen here; leave the raw file untouched.

3. **Merge transcription (if VTT available).** Merge `YYYY-MM-DD-SHORTNAME.vtt` into the edited copy to fill in missing speaker transcription:
   - Align VTT timestamps with the IRC `ack IRC_handle` markers to attribute spoken passages to the acknowledged speaker.
   - "Missing" means substantive discussion present in the VTT that has no corresponding scribed line in the IRC log — add it, attributed to the correct speaker.
   - Do not duplicate content already captured by the human scribe.
   - If no VTT is available, skip this step and generate minutes without transcription.
   - Never modify existing `RESOLUTION:` lines while merging.

4. **Replace IRC handles with real names.** Use the participants lists to map IRC handles to real names. This applies only to human speakers — never rename or remove bot/system handles such as `gb`, `RRSAgent`, or `Zakim` (see the preservation note above). Check both groups, since meeting attendees may belong to either:
   - Working Group: `https://www.w3.org/groups/wg/SHORTNAME/participants/`
   - Community Group: `https://www.w3.org/groups/cg/SHORTNAME/participants/`
   - In the minutes body (speaker labels and their scribed lines), use the short `Firstname:` form for brevity — e.g. `John:` rather than `John_Doe:`.
   - If two or more attendees share the same first name, disambiguate by appending the first letter of the last name as `FirstnameL` — e.g. `JaneD` for Jane Doe when another Jane attends.
   - Reserve the full `Firstname_Lastname` form for the `Present+` attendance list (step 5).
   - For handles with no match, leave the handle as-is and flag it for manual review.

5. **Record attendance.** In the edited minutes, mark each attendee with a `Present+ Firstname_Lastname` command:
   - Use the full `Firstname_Lastname` form here (not the short body form), taken from the participants list.
   - Remove duplicate entries for the same person — e.g. when both an IRC handle and its correlated `Firstname_Lastname` would appear, keep only the `Firstname_Lastname` entry.

6. **Generate HTML.** Convert the edited minutes to HTML using scribe2
   (https://github.com/w3c/scribe2) and save as
   `YYYY-MM-DD-SHORTNAME-minutes-edited.html`, e.g.:
   ```
   perl scribe2/scribe.perl --final --minutes=https://www.w3.org/YYYY/MM/DD-SHORTNAME-minutes.html YYYY-MM-DD-SHORTNAME-irc-edited.txt > YYYY-MM-DD-SHORTNAME-minutes-edited.html
   ```
   Report the exact scribe2 command used and any warnings it emits.

7. **Verify the output.** Open `YYYY-MM-DD-SHORTNAME-minutes-edited.html` and spot-check before the files are shared or committed:
   - The attendee list, agenda topics, and every `RESOLUTION:` line render correctly.
   - Speaker labels use the short `Firstname:` form, and no IRC handles leak into the body — except the preserved handles on `RESOLUTION:` lines.
   - Report any unresolved handles or scribe2 warnings for human review.
