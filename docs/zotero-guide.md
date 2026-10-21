# Preparing your Zotero library

[Back to README](../README.md)

A style can only format what is in the item metadata. Fill in the Zotero fields as below so the output matches PPTA.
Zotero reads `Extra` one line at a time, so put each `Key: value` entry on its own line.

## Field guide

| Item | What to enter in Zotero |
|:-----|:------------------------|
| **General** | |
| Book title | *Title Case*, except function words |
| Journal or proceedings name | *Title Case* |
| Article title | *Sentence case*, keeping capitals for names, acronyms and taxa. The style prints titles as entered |
| Subtitle after a colon | PPTA starts it with a capital: `Avian leukemia virus OK 10: Analysis of ...` |
| Italic words in a title | Wrap them in `<i>...</i>`, for example `<i>Oryza sativa</i>` |
| Publisher | Abbreviated, as in [PPTA Supplement 9](https://ipb.link/suplemen-ppta): `Cambridge Univ Pr`, `CRC Pr`. The place of publication is not printed, except for theses and reports |
| **Journal article** | |
| Abbreviated journal name | `Journal Abbr` field, without periods: `J Appl Pharm Sci` |
| No author | In `Short Title`, enter the first word of the title. It is cited as `(Tren… 2026)` |
| Organization as author | The abbreviation as the author (single-field mode): `CPPS. 2019.` |
| Organization with its full name (optional) | Also add a line to `Extra`: `Authority: Scandinavian Society for Clinical Chemistry and Clinical Physiology`. The reference list then shows `[SSCCCP] Scandinavian Society ...`, and the citation stays `(SSCCCP 1976)`. PPTA itself prints the abbreviation only |
| Article type: editorial, review, ... | `Extra`, as a plain line with no `Key:`, for example `editorial`. It prints in square brackets after the title |
| English translation of the title | `Extra`, as a plain line with no `Key:`. It prints in square brackets after the title |
| Supplement or special issue | `Issue` field, for example `3 Supl 1`, which prints as `4(3 Supl 1)` |
| Accepted, not yet published | Leave `Volume`, `Issue` and `Pages` empty. The entry ends with `siap terbit` (`forthcoming` in English) |
| Reprinted article | Add a line to `Extra`: `References: J Nutr. 1990;120(1):20-35`. The entry ends with `Cetak ulang dalam ...` (`Reprinted in ...`) |
| **Book** | |
| Edition | `Edition` field as a number: `2` prints as `Ed 2` |
| Book with editor | Add the person as `Editor` |
| Translated book | Add the person as `Translator` |
| Organization as author | As for journal articles: `IPB. 2026.` |
| Multi-volume book, different title for each volume | `Volume` field, as `number: volume title`, which prints as `Vol 6: ...` |
| Chapter in a book | Use the item type `Book Section` |
| **Conference proceedings** | |
| Conference date | In `Extra`, add a line `Event Date: YYYY-MM-DD/YYYY-MM-DD` |
| Conference location | In `Extra`, add `Event Place: Bogor, Indonesia` |
| Paper from the internet | `URL` and `Accessed` fields. It prints `hlm 167-175; [diakses 2026 Mei 12]. https://....` |
| Abstract number | Add a line to `Extra`: `Number: 12`. Prints as `No abstrak 12` (`Abstract no 12` in English) |
| **Thesis** | |
| Type: skripsi, tesis, disertasi | `Type` field. Keep `Place` and `University`: `Bogor: Institut Pertanian Bogor` |

## Things the style cannot fix for you

**Indonesian titles in the English style.** CSL applies title case only to items it treats as English, and the
English style is set to English. Without help it prints Indonesian book titles as "Politik Kelautan *Dan*
Perikanan". To keep a title as entered, set the item's `Language` field to `id`.

**Labels you type are not translated.** Article types in `Extra` (such as `catatan penelitian`) and thesis types in
`Type` (such as `disertasi`) print exactly as entered. For an English document, enter them in English:
`research note`, `undergraduate thesis`, `master's thesis`, `dissertation`.

**Access dates.** PPTA prints an access date only for sources read online that have no DOI, such as proceedings and
web pages. Journal articles with a DOI never show one, so you do not need to clear `Accessed` on them.
