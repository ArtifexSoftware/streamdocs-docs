# StreamDocs Online documentation

Welcome to the StreamDocs Online documentation. This documentation relies on [Sphinx](https://www.sphinx-doc.org/en/master/) to publish HTML docs from markdown files written with [restructured text](https://en.wikipedia.org/wiki/ReStructuredText) (RST).

## Sphinx version

This README assumes you have [Sphinx v5.0.2 installed](https://www.sphinx-doc.org/en/master/usage/installation.html) on your system.


## Updating the documentation

Within `docs` update the associated restructured text (`.rst`) files. These files represent the corresponding document pages.



## Building HTML documentation

- Ensure you have the `sphinx-rtd-theme` installed:


`python -m pip install sphinx-rtd-theme`


- From the root location run:

`sphinx-build -b html src build`

This then creates the HTML documentation within `build/html`.


## Building PDF documentation


- First ensure you have [rst2pdf](https://pypi.org/project/rst2pdf/) installed:


`python -m pip install rst2pdf`


- Then run:


`sphinx-build -b pdf source build/pdf`

This will then generate a single PDF for all of the documentation within `build/pdf`.






## Editing the documentation


Within this `src` folder update the associated `.rst` files which are in restructured text format. These files represent the corresponding document pages.


### Some notes on syntax


- Use `for inline code` or `computer/technical terminology`

- Use Prism HTML constructs for embedded code samples

- For names use :title:`StreamDocs` , e.g. :title:`PDF`

- For headers underline text with ==== for h1 level, ---- for h2, ~~~~ for h3 & """" for h4


For full details on RST syntax, see: https://www.sphinx-doc.org/en/master/usage/restructuredtext/


---





