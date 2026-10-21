# Testing and examples

[Back to README](../README.md)

## PPTA test library

[`test/ppta.json`](../test/ppta.json) holds one CSL JSON item for each journal, book, proceedings and thesis case in PPTA
Chapter VII, taken from the guide's own examples. Two test pages cite every item:

| Page | Style | Output |
|:--|:--|:--|
| [`test/ppta.md`](../test/ppta.md) | `ipb.csl` | [HTML](../test/ppta.html) |
| [`test/ppta_en.md`](../test/ppta_en.md) | `ipb_en.csl` | [HTML](../test/ppta_en.html) |

Three items come from the PPKI 4 library instead, because PPTA gives no full example for them:
`sscccp_recommended_1976` (the optional `[ABBR] Full Name` form for organizations), `rifai_penggodokan_1992` (an insert
issue, `1(Sisipan 3)`) and `young1987` (a reprinted article).

## PPKI 4 test library

The original test library from PPKI 4 is kept as a regression set, exported from Zotero in several formats:
[YAML](../test/ppki4.yaml), [BibTeX](../test/ppki4.bib), [RIS](../test/ppki4.ris),
[EndNote XML](../test/ppki4.xml). Its pages, [`ppki4.md`](../test/ppki4.md) and
[`ppki4_en.md`](../test/ppki4_en.md), now render with the PPTA rules.

## Real papers

| Folder | Style | Content | Output |
|:--|:--|:--|:--|
| [`tesis/`](../tesis/) | `ipb.csl` | Auriza Rahmad Akbar's undergraduate paper on parallel pairwise alignment (2014), in Bahasa Indonesia, from the original repository | [HTML](../tesis/paper.html) |
| [`tesis_en/`](../tesis_en/) | `ipb_en.csl` | An excerpt of Benny Istanto's MSc thesis on bias correction of satellite precipitation (2026): the opening of the Summary and the Background section, with 28 references | [HTML](../tesis_en/paper.html) |

`tesis_en/references.json` was converted from the thesis BibTeX file and cleaned: access dates written as ISO dates,
journal-article titles in sentence case, and a few author names corrected.

## Rendering

Each page names its style and bibliography in its YAML header. Run pandoc from the page's folder:

```bash
pandoc ppta_en.md --citeproc -s -o ppta_en.html
```

For the papers in `tesis/` and `tesis_en/`, add `--mathjax`.

## Checking a change

1. Validate the style against the CSL 1.0.2 schema with the [CSL validator](https://validator.citationstyles.org/).
2. Render both PPTA test pages and compare the reference list with the examples in the guide.
3. Render the PPKI 4 pages and the two papers, and check that nothing else changed.

Zotero and Mendeley use the citeproc-js engine, while pandoc uses its own. Most output is the same, but check
important changes in Zotero as well.
