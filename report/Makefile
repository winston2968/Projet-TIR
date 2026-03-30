# --- Configuration ---
PDF_NAME = main
LATEX_ENGINE = pdflatex
# Si tes fichiers sont à la racine, utilise . sinon mets le chemin (ex: report)
REPORT_DIR = .
MAIN_FILE = $(PDF_NAME).tex

# --- Règles ---

# La première règle est celle par défaut
all: $(REPORT_DIR)/$(PDF_NAME).pdf

# Règle de compilation principale
# Correction : indentation par TAB obligatoire
$(REPORT_DIR)/$(PDF_NAME).pdf: $(MAIN_FILE)
	@echo "==> Compilation du rapport avec latexmk..."
	latexmk -$(LATEX_ENGINE) -pdf -f -interaction=nonstopmode \
		-output-directory=$(REPORT_DIR) $(MAIN_FILE)

# Nettoyage des fichiers auxiliaires
clean:
	@echo "==> Nettoyage des fichiers temporaires..."
	@rm -f *.aux *.log *.out *.toc *.lof *.lot *.bbl *.blg *.maf *.mtc* *.thm *.synctex.gz
	@rm -f *.ptc* *.fls *.fdb_latexmk *.bcf *.run.xml *.run*.xml *.synctex*
	@rm -f $(REPORT_DIR)/*.aux $(REPORT_DIR)/*.log $(REPORT_DIR)/*.out $(REPORT_DIR)/*.toc
	@rm -f $(REPORT_DIR)/*.bcf $(REPORT_DIR)/*.run.xml $(REPORT_DIR)/*.fdb_latexmk $(REPORT_DIR)/*.fls

# Nettoyage complet
cleanall: clean
	@echo "==> Suppression du PDF..."
	@rm -f $(REPORT_DIR)/$(PDF_NAME).pdf