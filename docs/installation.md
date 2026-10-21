# Installation

[Back to README](../README.md)

Download links:

- Bahasa Indonesia: [`ipb.csl`](https://raw.githubusercontent.com/bennyistanto/csl-ipb/master/ipb.csl)
- English: [`ipb_en.csl`](https://raw.githubusercontent.com/bennyistanto/csl-ipb/master/ipb_en.csl)

In the browser, use "Save link as" so the file keeps its `.csl` extension.

Each style has its own ID based on this repository (`https://github.com/bennyistanto/csl-ipb/ipb.csl` and
`.../ipb_en.csl`). You can install both side by side and switch between them per document. They do not replace the
*Institut Pertanian Bogor* style from the Zotero Style Repository, which still follows PPKI 3 (2016). If you
installed an earlier version of these files that used the Zotero repository ID, remove it after installing the new
one.

## Zotero (version 7)

1. Download the `.csl` file you need.
2. In Zotero, open **Edit > Settings** (on macOS, **Zotero > Settings**) and go to the **Cite** pane.
3. Under **Styles**, click **+** and select the downloaded file.
4. In Word or LibreOffice, open the Zotero toolbar, click **Document Preferences**, and choose
   *Institut Pertanian Bogor: Pedoman Penyajian Tugas Akhir*, followed by *(Bahasa Indonesia)* or *(English)*.

Zotero documentation: [Citation styles](https://www.zotero.org/support/styles).

## Mendeley Reference Manager and Mendeley Cite

In the Word add-in Mendeley Cite, open the **Citation Settings** tab, choose **Add a custom style**, and paste a
download link from above. Mendeley's help page:
[changing the citation style in Mendeley Cite](https://service.elsevier.com/app/answers/detail/a_id/28708/).

## Mendeley Desktop (legacy)

1. Go to **View > Citation Style > More Styles...**.
2. Open the **Get More Styles** tab, paste a download link into **Download Style**, and click **Download**.

## Pandoc, R Markdown and Quarto

Put the `.csl` file next to your document and name it in the YAML header:

```yaml
bibliography: references.bib
csl: ipb_en.csl   # or ipb.csl for Bahasa Indonesia
```

To render from the command line:

```bash
pandoc paper.md --citeproc -o paper.docx
```
