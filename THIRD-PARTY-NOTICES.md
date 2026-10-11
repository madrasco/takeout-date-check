# Third-party notices

## GooglePhotosTakeoutHelper_Neo: translated "-edited" suffixes

`index.html` contains a short list of translated file-name suffixes that Google Photos adds to edited copies (for example `-edited`, `-bearbeitet`, `-modifié`). The list is partly derived from GooglePhotosTakeoutHelper_Neo, file `lib/common/constants/extra_formats.dart` (https://github.com/Xentraxx/GooglePhotosTakeoutHelper_Neo), licensed under the Apache License, Version 2.0. A copy of that licence is in `LICENSE-APACHE-2.0.txt`.

Changes: the suffixes were selected, some were added from other sources, and they were rewritten as a JavaScript array (`EDITED_SUFFIXES`). Seven entries match the upstream file as read on 2026-10-08 (blob eedadb60ba718289710692e74b34eefed208e4a1): `-edited`, `-bearbeitet`, `-modifié`, `-bewerkt`, `-modificato`, `-editado`, `-編集済み`. The upstream project publishes no NOTICE file.

Everything else in this repository is MIT-licensed (see `LICENSE`).
