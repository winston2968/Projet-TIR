# --- Configuration ---
PDF_NAME = poster
LATEX_ENGINE = pdflatex
POSTER_DIR = .
MAIN_FILE = $(PDF_NAME).tex

# --- Règles ---

# La première règle est celle par défaut
all: $(POSTER_DIR)/$(PDF_NAME).pdf

# Règle de compilation principale
# Correction : indentation par TAB obligatoire
$(POSTER_DIR)/$(PDF_NAME).pdf: $(MAIN_FILE)
	@echo "==> Compilation du rapport avec latexmk..."
	latexmk -$(LATEX_ENGINE) -pdf -f -interaction=nonstopmode \
		-output-directory=$(POSTER_DIR) $(MAIN_FILE)

# Nettoyage des fichiers auxiliaires
clean:
	@echo "==> Nettoyage des fichiers temporaires..."
	@rm -f *.aux *.log *.out *.toc *.lof *.lot *.bbl *.blg *.maf *.mtc* *.thm *.synctex.gz
	@rm -f *.ptc* *.fls *.fdb_latexmk *.bcf *.run.xml *.run*.xml *.synctex*
	@rm -f $(POSTER_DIR)/*.aux $(POSTER_DIR)/*.log $(POSTER_DIR)/*.out $(POSTER_DIR)/*.toc
	@rm -f $(POSTER_DIR)/*.bcf $(POSTER_DIR)/*.run.xml $(POSTER_DIR)/*.fdb_latexmk $(POSTER_DIR)/*.fls

# Nettoyage complet
cleanall: clean
	@echo "==> Suppression du PDF..."
	@rm -f $(POSTER_DIR)/$(PDF_NAME).pdf