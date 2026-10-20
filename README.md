# CSL styles for IPB PPKI (4th edition)

> [!NOTE]
> This repository is a fork of [auriza/csl-ipb-ppki](https://github.com/auriza/csl-ipb-ppki), the original IPB PPKI
> style by Auriza Rahmad Akbar and M. Rachmatarramadhan. The fork exists mainly for the **English version**,
> `ipb_en.csl`. The Bahasa Indonesia style, `ipb.csl`, is kept here too, with the same fixes as the English one.
> Those fixes are not in the original repository, so download both styles from this one.

[Citation Style Language](https://citationstyles.org/) (CSL) styles for the IPB University thesis writing guide,
*Pedoman Penulisan Karya Ilmiah* (PPKI), 4th edition.

The repository has two styles:

| File | Language | Use it for | Download |
|:-----|:---------|:-----------|:---------|
| [`ipb.csl`](ipb.csl) | Bahasa Indonesia | Theses and papers written in Indonesian. The original style, with this fork's fixes. | [ipb.csl](https://raw.githubusercontent.com/bennyistanto/csl-ipb/master/ipb.csl) |
| [`ipb_en.csl`](ipb_en.csl) | English | Theses and papers written in English, such as international programs and journal manuscripts. | [ipb_en.csl](https://raw.githubusercontent.com/bennyistanto/csl-ipb/master/ipb_en.csl) |

Both styles follow the same PPKI rules. The English style translates the labels ("dan" becomes "and", "Di dalam"
becomes "In", "hlm" becomes "pp", "diakses" becomes "accessed on", and so on) and uses English month names, following
the English edition of the guide. The original list of translated terms is in
[this gist](https://gist.github.com/bennyistanto/ef6b1a2bb1ed303a7832f789ac7e7a70).

Each style has its own ID, based on this repository (`https://github.com/bennyistanto/csl-ipb/ipb.csl` and
`.../ipb_en.csl`). You can install both side by side and switch between them per document, and they do not replace
the *Institut Pertanian Bogor* style from the Zotero Style Repository if you already have it. If you installed an
earlier version of these files, which used the Zotero repository ID, remove it after installing the new one.

How a citation style fits in:

```mermaid
flowchart LR
    meta["Reference metadata<br/>(BibTeX, RIS, CSL JSON)"] --> proc(["Citation processor<br/>(Zotero, Mendeley, Pandoc)"])
    style["Citation style<br/>(ipb.csl or ipb_en.csl)"] --> proc
    proc --> out["Citations and<br/>reference list"]
```

## Installation

### Zotero (version 7)

1. Download the `.csl` file you need from the table above. In the browser, use "Save link as" so the file keeps
   its `.csl` extension.
2. In Zotero, open **Edit > Settings** (on macOS, **Zotero > Settings**) and go to the **Cite** pane.
3. Under **Styles**, click **+** and select the downloaded file.
4. In Word or LibreOffice, open the Zotero toolbar, click **Document Preferences**, and choose
   *Institut Pertanian Bogor: Pedoman Penulisan Karya Ilmiah Edisi ke-4*, followed by *(Indonesian)* or
   *(English)*.

See also the Zotero documentation: [Citation styles](https://www.zotero.org/support/styles).

### Mendeley Reference Manager and Mendeley Cite

In the Word add-in Mendeley Cite, open the **Citation Settings** tab, choose **Add a custom style**, and paste the
download link from the table above. Mendeley's help page:
[changing the citation style in Mendeley Cite](https://service.elsevier.com/app/answers/detail/a_id/28708/).

### Mendeley Desktop (legacy)

1. Go to **View > Citation Style > More Styles...**.
2. Open the **Get More Styles** tab, paste the download link into **Download Style**, and click **Download**.

### Pandoc, R Markdown and Quarto

Put the `.csl` file next to your document and reference it in the YAML header:

```yaml
bibliography: references.bib
csl: ipb_en.csl   # or ipb.csl for Bahasa Indonesia
```

To render from the command line:

```bash
pandoc paper.md --citeproc -o paper.docx
```

## Preparing your Zotero library

The style can only format what is in the item metadata. Fill in the Zotero fields as follows so the output matches
PPKI. Zotero reads `Extra` one line at a time, so put each `Key: value` entry on its own line.

| Item | What to enter in Zotero |
|:-----|:------------------------|
| **General** | |
| Book title | *Title Case* |
| Journal or proceedings name | *Title Case* |
| Article title | *Sentence case* |
| Italic words in a title | Wrap them in `<i>...</i>`, for example `<i>Oryza sativa</i>` |
| **Journal article** | |
| Abbreviated journal name | `Journal Abbr` field |
| No author | In `Short Title`, enter the first word of the title |
| Organization as author | Enter the abbreviation as the author (single-field mode), and add a line to `Extra`: `Authority: Scandinavian Society for Clinical Chemistry and Clinical Physiology`. The reference list shows `[SSCCCP] Scandinavian Society ...`, and the citation shows `(SSCCCP 1976)` |
| Article type: editorial, review, ... | `Extra` field, as a plain line with no `Key:`, for example `editorial`. It prints in square brackets after the title |
| Supplement or special issue | `Issue` field |
| English translation of the title | `Extra` field, as a plain line with no `Key:`. It prints in square brackets after the title |
| Reprinted article | Add a line to `Extra`: `References: J Nutr. 1990;120(1):20-35`. The entry ends with `Cetak ulang dalam ...` (`Reprinted in ...` in English) |
| Accepted, not yet published | Leave `Volume`, `Issue` and `Pages` empty. The entry ends with `siap terbit` (`forthcoming` in English) |
| Article from the internet | `Accessed` field. The access date prints before the DOI, as in the PPKI examples. Clear `Accessed` if you cite the printed version |
| **Book** | |
| US state code | `Place` field, for example `New York (NY)` |
| Book with editor | Add the person as `Editor` |
| Translated book | Add the person as `Translator` |
| Organization as author | Same as for journal articles: abbreviation as the author, full name in `Extra` as `Authority: Institut Pertanian Bogor` |
| Multi-volume book, same title for each volume | `Volume` field |
| Multi-volume book, different title for each volume | `Volume` field, as `number: volume title` |
| Chapter in a book | Use the item type `Book Section` |
| **Conference proceedings** | |
| Conference date | In `Extra`, add a line `Event Date: YYYY-MM-DD/YYYY-MM-DD` |
| Conference location | Leave `Place` empty. In `Extra`, add `Event Place:` and `Publisher Place:` lines |
| Paper from the internet | `URL` and `Accessed` fields |
| Abstract number | Add a line to `Extra`: `Number: 12`. Prints as `No abstr 12` (`Abstract no 12` in English) |
| **Thesis** | |
| Type: undergraduate thesis (skripsi), master's thesis (tesis), dissertation (disertasi) | `Type` field |

**Indonesian titles in the English style.** CSL applies title case only to items it treats as English. The English
style is set to English, so it capitalizes every word of Indonesian book titles (for example, "Politik Kelautan
*Dan* Perikanan"). To keep a title as entered, set the item's `Language` field to `id`.

**Labels you type yourself are not translated.** Article types in `Extra` (such as `[catatan penelitian]`) and
thesis types in `Type` (such as `disertasi`) print exactly as entered. For an English document, enter them in English:
`research note`, `undergraduate thesis`, `master's thesis`, `dissertation`.

## How the two styles differ

The examples below come from rendering the test pages in [`test/`](test/) with each style (see [Testing](#testing)).
The English wording follows the English edition of the guide, *Guidelines for Writing Scientific Paper*.

| | `ipb.csl` (Bahasa Indonesia) | `ipb_en.csl` (English) |
|:--|:--|:--|
| In-text citation | (Sutiawan dan Hernowo 2017) | (Sutiawan and Hernowo 2017) |
| Chapter in a book | Di dalam: ... editor. ... hlm 290–300. | In: ... editors. ... pp 290–300. |
| Edition | Ed ke-4. | 4th ed. |
| Volume | Volume ke-1. | Volume 1. |
| Translator | ..., penerjemah. | ..., translator. |
| Conference date | 2010 Okt 4–7 | 2010 Oct 4–7 |
| Article not yet published | Ocean Coast Manag., siap terbit. | Ocean Coast Manag., forthcoming. |
| Access date | [diakses 2017 Nov 29]. https://... | [accessed on 2017 Nov 29]. https://... |
| Reprinted article | Cetak ulang dalam J Nutr. ... | Reprinted in J Nutr. ... |
| Abstract number | No abstr 12 | Abstract no 12 |
| Book titles | as entered | Title Case (see the note above on Indonesian titles) |

Apart from these and the [Known issues](#known-issues) below, the two styles behave the same way:

- citations ordered by year, with year suffixes written as `2023a`, `2023b` and the reference list ordered by title
  within the same author and year
- organization authors as `[ABBR] Full Name`
- initials without hyphens (`Hsu KL`, not `Hsu K-L`) and a comma before *et al.*
- article type and translated title in square brackets
- journal abbreviations without periods
- the access date before the DOI, with no URL, for journal articles
- the DOI printed for books, chapters, proceedings and reports as well
- a hanging indent in the reference list

## Known issues

These come from comparing the two styles on the test library, and `ipb_en.csl` with the reference list of an
accepted IPB thesis.

**Both styles:**

- **Total page count of a whole book or report.** PPKI writes it as `525 p`. The styles print a report's `Pages`
  field as a page range (`pp 143` or `hlm 143`), and never print a book's `# of Pages`.
- **Datasets, software and preprints** print without a publisher or repository, for example
  `Huffman GJ. 2023. GPM IMERG Final Precipitation L3 V07. [accessed on ...]. doi:...`.
- **Proceedings from the internet.** PPKI puts a semicolon before the access date (`pp 37-45; [accessed on ...]`).
  The styles use a period.
- **Review article with no editor.** The `[review]` (`[ulasan]`) label is not printed.
- **Periods inside a container name are removed** along with abbreviation periods, so `Tirto.id` prints as `Tirtoid`.
- **A URL at the end of an entry** is followed by a period in `ipb.csl` but not in `ipb_en.csl`. The guide's own
  examples do both.

**`ipb_en.csl` only:**

- **Editor and translator order.** `ipb.csl` gives `Achmadi SS, penerjemah; Safitri A, editor.`; `ipb_en.csl`
  gives `Safitri A, editor; Achmadi SS, translator.`
- **Volume in a chapter** prints as `Vol. 3: Strengthening the Family.` instead of `Volume 3: ...`.
- **Issue numbers.** A text issue keeps parentheses, `1(Sisipan 3)` instead of `1 Sisipan 3`, and an issue range
  keeps its hyphen, `140(3-4)` instead of `140(3–4)`.
- **Article with no author.** The short title in the citation has no ellipsis: `(Tren 2006)` instead of
  `(Tren… 2006)`.

Issues and pull requests are welcome.

## Testing

The test library has one example for each PPKI case:

- Bibliography: [YAML](test/ppki4.yaml), [BibTeX](test/ppki4.bib), [RIS](test/ppki4.ris), [EndNote XML](test/ppki4.xml)
- Test page in Bahasa Indonesia, using `ipb.csl`: [Markdown](test/ppki4.md), output [HTML](test/ppki4.html)
- Test page in English, using `ipb_en.csl`: [Markdown](test/ppki4_en.md), output [HTML](test/ppki4_en.html)

The library was exported from Zotero as "Better CSL YAML". Both test pages use the same library, and each page names
its style in its YAML header. To render them, run this from the `test/` folder:

```bash
pandoc ppki4_en.md --citeproc -s -o ppki4_en.html
```

Use `ppki4.md` and `ppki4.html` for the Bahasa Indonesia page.

Before submitting a change to a style, check it with the [CSL validator](https://validator.citationstyles.org/).

## Credits and license

- `ipb.csl`: Auriza Rahmad Akbar and M. Rachmatarramadhan, with fixes in this fork by Benny Istanto.
- `ipb_en.csl`: English translation by Benny Istanto, based on the
  [Institut Pertanian Bogor style](https://www.zotero.org/styles/institut-pertanian-bogor) in the Zotero Style
  Repository.
- PPKI guide, English version: [IPB University](https://kmm.ipb.ac.id/ppki-edisi4-eng/).

Both styles are licensed under
[Creative Commons Attribution-ShareAlike 3.0](https://creativecommons.org/licenses/by-sa/3.0/).
