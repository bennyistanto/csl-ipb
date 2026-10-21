# Style notes

[Back to README](../README.md)

## Source

Both styles follow IPB's *Pedoman Penyajian Tugas Akhir* (PPTA, 2026), Chapter VII, which bases its name-year system
on the CSE style, 9th edition (2024):

- Bahasa Indonesia: [dtptp.ipb.ac.id/ppta-ipb](https://dtptp.ipb.ac.id/ppta-ipb/)
- English: [dtptp.ipb.ac.id/ppta-english](https://dtptp.ipb.ac.id/ppta-english/)
- Supplements, including author names (8) and publisher abbreviations (9): [ipb.link/suplemen-ppta](https://ipb.link/suplemen-ppta)

## Guide versions

The styles follow the current guide. If your study program still uses PPKI 4, download the styles from the last
commit that follows it.

| Guide | Year | Bahasa Indonesia | English | Styles in this repository |
|:--|:--|:--|:--|:--|
| **PPTA**, *Pedoman Penyajian Tugas Akhir* | 2026 | [dtptp.ipb.ac.id/ppta-ipb](https://dtptp.ipb.ac.id/ppta-ipb/) | [dtptp.ipb.ac.id/ppta-english](https://dtptp.ipb.ac.id/ppta-english/) | current `master` |
| **PPKI 4**, *Pedoman Penulisan Karya Ilmiah*, 4th edition | 2019 | [Panduan_31.pdf](https://simak.ipb.ac.id/Foto/Panduan/Panduan_31.pdf) | [kmm.ipb.ac.id/ppki-edisi4-eng](https://kmm.ipb.ac.id/ppki-edisi4-eng/) | commit [`67d44ca`](https://github.com/bennyistanto/csl-ipb/tree/67d44ca3852af818db601aa1fe3f6c86ee7768ed): [`ipb.csl`](https://raw.githubusercontent.com/bennyistanto/csl-ipb/67d44ca3852af818db601aa1fe3f6c86ee7768ed/ipb.csl), [`ipb_en.csl`](https://raw.githubusercontent.com/bennyistanto/csl-ipb/67d44ca3852af818db601aa1fe3f6c86ee7768ed/ipb_en.csl) |

## How the two styles differ

Only the labels and month names differ. The examples come from the [PPTA test pages](testing.md), except
the abstract number, which no PPTA example has.

| | `ipb.csl` (Bahasa Indonesia) | `ipb_en.csl` (English) |
|:--|:--|:--|
| In-text citation | (Rusmana dan Nedwell 2024) | (Rusmana and Nedwell 2024) |
| Chapter in a book | Di dalam: ... editor. ... hlm 290–300. | In: ... editor. ... p 290–300. |
| Translator | ..., penerjemah. | ..., translator. |
| Dates | 2015 Okt 19–20, 2026 Mei 12 | 2015 Oct 19–20, 2026 May 12 |
| Not yet published | Chem Biodivers., siap terbit. | Chem Biodivers., forthcoming. |
| Access date | [diakses 2026 Mei 12] | [accessed on 2026 May 12] |
| Reprinted article | Cetak ulang dalam J Nutr. ... | Reprinted in J Nutr. ... |
| Abstract number | No abstrak 12 | Abstract no 12 |
| Book titles | as entered | Title Case, unless the item's `Language` is `id` |

Both styles share everything else:

- in-text citations ordered by year, with year suffixes `2025a`, `2025b`, and the reference list ordered by author,
  year, then title
- up to 5 authors listed; more than 5 become the first 5 followed by *et al.*
- initials without periods or hyphens (`Lee HS`), and a comma before *et al.*
- journal abbreviations without periods, issues in parentheses with ranges as `140(3–4)`
- the DOI for every type that has one; no access date for journal articles
- `Ed 2`, `Vol 6:`, and no place of publication except for theses and reports
- proceedings as `Title; 2015 Okt 19–20; Bogor, Indonesia. Publisher. hlm 37–42.`
- a hanging indent in the reference list

## What changed from PPKI 4

| | PPKI 4 (2019) | PPTA (2026) |
|:--|:--|:--|
| Basis | CSE (2014) | CSE 9th edition (2024) |
| Authors before *et al.* | 10 | 5 |
| Place of publication | `Bogor: IPB Press.` | `IPB Press.` (kept for theses) |
| Edition | `Ed ke-4` / `4th ed` | `Ed 4` |
| Volume | `Volume ke-1` | `Vol 1` |
| Access date on journal articles | printed before the DOI | not printed |
| Proceedings from the internet | `hlm 37-45. [diakses ...]. URL` | `hlm 37-45; [diakses ...]. URL.` |
| English page label | `pp` | `p` |
| English editor label | `editors` for several | `editor` for any number |
| Organization author | `[PFI] Perhimpunan Fitopatologi Indonesia.` | `PFI.` (full name in the body text) |

This repository keeps the `[ABBR] Full Name` form as an option for organizations, through Extra `Authority:`. See the
[Zotero guide](zotero-guide.md).

## Where PPTA is inconsistent, and what the styles do

- **Authors before *et al.*** The rule in 7.2.1.1 says more than 5 authors become 5 + *et al.*, and the Pezzino
  example follows it. The Riyanto and Resmeiliana examples list 10 authors, and Supplement 8 cuts only at 11. The
  styles follow the stated rule.
- **Access date for internet proceedings.** The Indonesian edition prints `hlm 167-175; [diakses 2026 Mei 12]. URL.`;
  the English edition leaves the date out. Both styles print it.
- **Page ranges** mix hyphens and en dashes in the examples. The styles always use an en dash, the standard typographic mark for a range.
- **Doubled punctuation** in a few examples (`et al.. 2026`, `Syartinilia., penerjemah`) is treated as a typo.

## Known issues

- **Total page count of a whole book or report.** PPTA writes it as `525 hlm` or `525 p`. The styles print a
  report's `Pages` field as a range (`hlm 143`, `p 143`) and never print a book's `# of Pages`.
- **New source types in PPTA 7.2.5** have no dedicated layout yet: patents, printed and online newspapers, documents
  on CD, and legal documents (`Permen ... 2025`).
- **Datasets, software and preprints** print without a publisher or repository.
- **Review article with no editor.** The `[ulasan]` / `[review]` label is not printed.
- **Periods inside a container name are removed** along with abbreviation periods, so `Tirto.id` prints as `Tirtoid`.

Issues and pull requests are welcome.
