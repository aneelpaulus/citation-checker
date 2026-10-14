# Citation Checker

Paste a reference list and find out which citations are real.

Citation Checker looks up each reference in PubMed and Crossref. It tells you whether the PubMed ID (PMID) or DOI exists, and whether it points to the paper the reference describes. I built it to catch the citations AI writing tools sometimes invent, but it works on any reference list, from a grant application to a student paper.

**[Try it live](https://aneelpaulus.github.io/citation-checker/)**

## What it flags

| Result | Meaning |
|---|---|
| Verified | The ID exists and the paper's title matches your reference. |
| Found by title | No ID was given, but a title search found the paper. |
| Check | Something is close but not exact (partial title match, year off, or conflicting IDs). Open the link and confirm. |
| Wrong ID | The ID exists but belongs to a different paper. A likely intended paper is suggested when one can be found. |
| Not found | The ID does not exist, or nothing close turned up in a search. |
| Couldn't check | A lookup service did not respond. Try again later. |

Results can be filtered by status, downloaded as a CSV file, or copied as a plain text report.

## How it works

1. Splits your pasted text into individual references (numbered lists, one per line, or blank-line separated).
2. Pulls out any PMID or DOI in each reference.
3. Looks up PMIDs in PubMed (falling back to Europe PMC if PubMed is unreachable) and DOIs in Crossref.
4. Compares the real title against your reference text. A match means most of the real title's meaningful words appear in your reference.
5. For references with no ID, or with an ID that fails, searches Crossref by the reference text to suggest the paper you probably meant.

The tool runs in your browser. It has no server and no sign-in, and it stores nothing. Your references go only to the public PubMed, Europe PMC, and Crossref lookup services.

## Limitations

- Matching is automatic and can be wrong. Treat every result as a prompt to look, not a final verdict.
- Crossref covers most journal DOIs but not all. A DOI registered with another agency (such as DataCite, common for datasets) will show as not found.
- Books, guidelines, and web pages without a PMID or DOI often won't match by title search.
- Up to 150 references per run, to stay within the free services' fair-use limits.

## Run your own copy

The whole tool is one file, `index.html`. To host it free on GitHub:

1. Create a new public repository and upload `index.html`, `README.md`, and `LICENSE`.
2. In the repository, open **Settings**, then **Pages**.
3. Under "Build and deployment," choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. After a minute or two, the page shows your live link.

You can also just download `index.html` and open it in any browser.

## Roadmap

- Optional "bring your own AI key" mode that checks whether each cited paper actually supports the sentence it is attached to.
- Support for pasting references in BibTeX and RIS formats.

## Disclaimer

For research and educational use. Not a substitute for reading the papers you cite.

## License

MIT. See `LICENSE`.

Built by Aneel Paulus, MD, MS.
