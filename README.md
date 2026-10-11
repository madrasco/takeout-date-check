# Takeout Date Check

A single HTML file that tells you which photos and videos in a Google Photos Takeout export are missing a date, and whether that date can be recovered from Google's `.json` files or from the file name. It only reads: it holds no code that can change, move or upload a file. It lists up to 200,000 files of any kind in the folder and reads every photo and video among them.

## Why

Google Takeout often puts a photo's date in a separate `.json` file next to the photo, so after you move the files elsewhere many of them sort by download day instead of the day they were taken. Before you fix anything, it helps to know how many files are affected, which ones, and whether their dates are recoverable. This check answers that for your whole export.

## How to use it

1. Download `index.html` from this repository (or the whole repository as a ZIP).
2. Open it in desktop Google Chrome or Microsoft Edge (version 86 or later). Other browsers lack the folder access it needs.
3. Unzip your Takeout download, click **Select your Takeout folder**, and choose the unzipped folder (the one containing `Google Photos`, or the top `Takeout` folder).
4. Read the report: how many files already have a date, how many would get one from a `.json` file or a recognised file name, and how many can't be fixed (for example, empty or damaged files). Under **Which files** you can open the list of file names in each group.

Your files stay on your computer. The page makes no network request while it checks, and it works offline.

## What it checks, and its limits

- Photos and videos: JPEG, PNG, MP4 and MOV dates are read. Other formats (HEIC, 3GP and so on) are counted as not fixable by this tool.
- Sidecar names: the classic `photo.jpg.json`, the newer `photo.jpg.supplemental-metadata.json`, duplicates such as `photo(1).jpg` and edited copies.
- It reports; it doesn't write. To put the dates back, see "Fixing the dates" below.

How it was tested (by AI agents, October 2026): on public Google Takeout samples from the [immich-go](https://github.com/simulot/immich-go) project's test data (two sample exports with 8 and 3 real photos and videos, all of which already had dates and were reported that way; a third sample of 3 empty files, reported as not fixable), and on 56 constructed files (dated and undated JPEG, PNG and MP4/MOV files, 26 of them deliberately damaged, using Google's documented naming patterns), where every file was classified as expected. The newer naming patterns come from user reports, not from a real export we could test. The page itself has been run in headless Chromium 156 on Linux against these files, with the folder dialog replaced by a test stand-in that hands it the same folder; the files were unchanged afterwards and the page made no network request. Google Chrome, Microsoft Edge, Windows and macOS have not been tested.

## Fixing the dates

This check doesn't write anything. Two ways to write the recovered dates:

- [GooglePhotosTakeoutHelper_Neo](https://github.com/Xentraxx/GooglePhotosTakeoutHelper_Neo): free, open source, runs from the command line.
- [Takeout Date Restorer](https://madrasco.dev/from/github/takeout): a paid browser tool (A$12 once) from the maker of this check. It writes the dates into copies of your JPEG, PNG, MP4 and MOV files and leaves your Takeout folder unchanged.

## Support

Built and maintained by AI agents run by Jack Valmadre, trading as Madrasco. Questions or problems: email support@madrasco.dev, which the owner reads and answers himself. Issues on this repository are not monitored: AI agents do not read or reply to them, so email is the way to get an answer.

## Credits

The list of translated "-edited" file-name suffixes is partly derived from [GooglePhotosTakeoutHelper_Neo](https://github.com/Xentraxx/GooglePhotosTakeoutHelper_Neo) (`extra_formats.dart`, Apache License 2.0); see `THIRD-PARTY-NOTICES.md`.

## Licence

MIT (see `LICENSE`), except the suffix list noted in `THIRD-PARTY-NOTICES.md` (Apache License 2.0, `LICENSE-APACHE-2.0.txt`). The paid tool's code that writes dates is not part of this repository.
