---
created: 2026-09-08
---
Work on Linear issue SIL-18:

Suggested branch name: syguy2003/sil-18-settings-page-notes

<issue identifier="SIL-18">
<title>Settings Page Notes</title>
<description>
Some frontend issues about that settings page that need addressed:

1. The error dialogue underneath should have a red "dismiss" x, just like the feed page error dialogue 
2. It should be a floating window that's resizable (check the /home/cassian/projects/cpp/bible project's NET notes popout for how this popout method might work) 
3. Adding channels shouldn't require an "@" symbol at the start; that should be optional 
4. The add button in the channels and categories pages is vertically taller than the input next to it. These should be the same height 
5. The feed section looks ugly 
6. Drop downs should be completely opaque (c.f. theme and backend drop downs) 
7. "Clear Current Key" should look like a button. It just looks like text right now 

<linear-image quality="preview">{"type":"image","attrs":{"src":"https://uploads.linear.app/b5824db1-013b-4408-bca0-19ad828215b8/a0a94662-189e-4e67-9355-09ee74456c2c/1422512c-9a8d-4b5b-a8f1-94d7d848914f?signature=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJwYXRoIjoiL2I1ODI0ZGIxLTAxM2ItNDQwOC1iY2EwLTE5YWQ4MjgyMTViOC9hMGE5NDY2Mi0xODllLTRlNjctOTM1NS0wOWVlNzQ0NTZjMmMvMTQyMjUxMmMtOWE4ZC00YjViLWE4ZjEtOTRkN2Q4NDg5MTRmIiwiaWF0IjoxNzg4ODgxNDg3LCJleHAiOjE3ODg5MjQ2ODd9.RJ3ta_Gc5rF40I6QhUQjqLLOuXat3mtTorhR4-m0cGc","title":"image.png","width":1261,"height":1390}}</linear-image>
</description>
<team name="Silas Tompkins"/>
<label>UI</label>
<project name="OmaTube">A YouTube client in the style of Omarchy</project>
</issue>

<comment-thread comment-id="eba9f2a3-9b34-4ddb-be21-4e935ad3f369">
<comment author="Silas Tompkins" created-at="2026-09-02T18:28:06.571Z">
Implementation plan:

1. Convert settings from an in-window modal overlay to an independently resizable floating window while preserving both standard and simple UI modes.
2. Match existing feed error dismissal, normalize bare channel handles to `@handle`, align add controls, restyle Feed settings, make combo popups opaque, and give Clear Current Key a visible button treatment.
3. Add parser coverage, run full Qt verification, then validate standard and compact window sizes with screenshots.
</comment>
</comment-thread>

<comment-thread comment-id="c8622b18-3e58-426d-8fa6-8303610653f5">
<comment author="Silas Tompkins" created-at="2026-09-02T19:00:58.306Z">
Implemented on `syguy2003/sil-18-settings-page-notes`:

* Settings now opens as a frameless, window-modal popout with system move/resize support and a 700x500 minimum size.
* Added red error dismiss control matching feed notifications.
* Bare channel handles normalize to `@handle`; parser coverage includes bare and invalid short handles.
* Channel/category add controls now share 40px height.
* Feed filtering uses a bordered cutoff card with clearer hierarchy.
* Theme, backend, and quality menus use opaque popup/delegate backgrounds.
* Clear Current Key now has a red bordered button treatment.
* Standard and simple UI variants both updated.

Verification: `./bin/test` passed 107 tests with 0 failures; startup smoke and `git diff --check` passed. Visual validation covered 900x720, minimum 700x500, simple UI, menu opacity, key clearing, and error dismissal. Screenshots attached.
</comment>
</comment-thread>

<comment-thread comment-id="5833869e-3ce4-442d-aeaa-6af6b9639ba7">
<comment author="Silas Tompkins" created-at="2026-09-02T19:44:48.864Z">
Follow-up UI pass started:

* Remove redundant settings helper text while retaining non-obvious security and playback caveats.
* Match category name, Save, and Delete control heights.
* Rename Settings surfaces to Config and remove header subheading.
</comment>
</comment-thread>

<comment-thread comment-id="f32d1e3b-bf60-486b-9888-6900e2f50740">
<comment author="Silas Tompkins" created-at="2026-09-02T21:30:40.462Z">
Follow-up pass implemented on `syguy2003/sil-18-settings-page-notes`:

* Removed redundant helper text across Channels, Categories, Feed, Appearance, Data API, and Playback tabs in both standard and simple variants (235 fewer lines of helper copy). Kept only non-obvious behavior: plain-local-storage warning, refresh timing, Omarchy theme status, and the mpv quality fallback.
* Category rows now give the name field, Save, and Delete an equal 40px height inside a 56px row.
* Renamed Settings to Config: window title, `OMA / CONFIG` header with subheading removed, top-right `CONFIG` button, empty-feed guidance, and `s: config` keybind footer. Updated the keybind footer test expectation.

Verification: `./bin/test` passed 107 tests with 0 failures; startup smoke and `git diff --check` passed. Screenshots attached covering the trimmed Channels view, equal-height category row with seeded category, compact feed card, shortened Data API copy, and main-window Config rename.
</comment>
</comment-thread>