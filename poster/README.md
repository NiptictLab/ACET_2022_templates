# CADT Latex Poster Template

For your convenience, we prepared a beamer poster style latex template (default to A0 size) for the ACET Conference 2022.  

Written by Ye Kyaw Thu, Affiliate Professor, CADT, Cambodia  
Last updated: 28 June 2022  
email: yktnlp@gmail.com  

Based on the oxford-poster (https://github.com/gbaydin/oxford-poster)  
Based on the I6pd2 style created by Thomas Deselaers an Philippe Dreuw.  

## How to Compile and Open the PDF Poster

After you update the source latex (acet_poster.tex) and bibtex (acet_poster.bib) files, type following commands:  

```bash
make
make view
```

## Makefile

The source of the Makefile is as follows and update the latex compiler and PDF viewer etc. based on your requirements:  

```
.PHONY: all old view clean clean_all

LATEX=pdflatex
BIBTEX=bibtex
FILENAME=acet_poster_landscape
#FILENAME=acet_poster_portrait
SOURCES=$(FILENAME).tex

OLD_SOURCES=old.tex
PDF_VIEWER=evince

all:
	$(LATEX) $(SOURCES)
	$(BIBTEX) $(FILENAME)
	$(LATEX) $(SOURCES)
	$(LATEX) $(SOURCES)

old:
	$(LATEX) $(OLD_SOURCES)
	$(LATEX) $(OLD_SOURCES)
	$(LATEX) $(OLD_SOURCES)

view:
	$(PDF_VIEWER) $(FILENAME).pdf

clean:
	@rm -vf $(FILENAME).aux $(FILENAME).log $(FILENAME).nav $(FILENAME).out $(FILENAME).snm $(FILENAME).toc $(FILENAME).vrb
	@echo "Removed LaTeX buildfiles."

clean_all: clean
	@rm -vf $(FILENAME).pdf
	@echo "Removed PDF."

```

## File Information

File information:  

- acet_poster_portrait.tex (latex source for portrait layout)
- acet_poster_landscape.tex (latex source for landscape layout)
- beamerthemeACET.sty (modified version of Oxford style file)
- [acet_poster.bib](https://github.com/NiptictLab/ACET_2022_templates-/blob/main/poster/acet_poster.bib) (BibTex file for citations)
- [Makefile](https://github.com/NiptictLab/ACET_2022_templates-/blob/main/poster/Makefile) (make utility for automation of the latex compilation)
- fig/ (a folder for figures)
- [acet_poster_portrait.pdf](https://github.com/NiptictLab/ACET_2022_templates-/blob/main/poster/acet_poster_portrait.pdf) (compiled portrait PDF poster file)  
- [acet_poster_landscape.pdf](https://github.com/NiptictLab/ACET_2022_templates-/blob/main/poster/acet_poster_landscape.pdf) (compiled landscape PDF poster file)  

## Reference

https://mirror.kku.ac.th/CTAN/macros/latex/contrib/beamer/doc/beameruserguide.pdf  
https://www.r-bloggers.com/2011/11/create-your-own-beamer-template/  
https://www.overleaf.com/learn/latex/Posters  
https://github.com/deselaers/latex-beamerposter  
https://github.com/deselaers/latex-beamerposter/blob/master/themes/beamerthemeI6pd2.sty  

