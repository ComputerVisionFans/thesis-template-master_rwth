LATEX := pdflatex
LATEXPARAM :=
BIBTEX := bibtex
BIBTEXPARAM :=

TARGET := thesis.pdf
SOURCES := titlepage.tex assertion.tex $(shell find latex/*.tex)
BIBTEX_SOURCES := $(TARGET:.pdf=.bib) abbrev.bib
IMAGES := $(shell find images -iname "*.{pdf,png,jpg}")

all: $(TARGET) application.pdf

application.pdf: application.tex
	$(LATEX) $<
	$(LATEX) $<

%.pdf: %.tex $(BIBTEX_SOURCES) $(SOURCES) $(IMAGES)
	$(LATEX) $<
	$(BIBTEX) $(@:.pdf=)
	$(LATEX) $<
	$(LATEX) $<

clean:
	rm -f $(TARGET) $(TARGET:.pdf=.aux) $(TARGET:.pdf=.log) $(TARGET:.pdf=.toc) $(TARGET:.pdf=.bbl) $(TARGET:.pdf=.blg) $(TARGET:.pdf=.out) $(TARGET:.pdf=.lox)
	rm -f application.aux application.log application.pdf
	rm -f latex/*.aux

.PHONY: all clean

