# Configuration
PDF_NAME = main
LATEX_ENGINE = pdflatex
MAIN_FILE = $(PDF_NAME).tex

.PHONY: all clean setup

# Commande par défaut : compile le projet
all: $(PDF_NAME).pdf

# Règle de compilation principale
$(PDF_NAME).pdf: $(MAIN_FILE) $(REPORT_DIR)/references.bib
	@echo "==> Compilation du rapport..."
	latexmk -$(LATEX_ENGINE) -f -interaction=nonstopmode \
		-output-directory=$(REPORT_DIR) $(MAIN_FILE)

# Nettoyage des fichiers auxiliaires
clean:
	@echo "==> Nettoyage des fichiers temporaires..."
	@rm -f *.run.xml *.bbl *.blg *.aux *.log *.out *.toc *.fdb_latexmk *.fls *.synctex.gz *.thm

# Nettoyage complet (y compris le PDF final)
distclean: clean
	@rm -f $(REPORT_DIR)/$(PDF_NAME).pdf