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
# On ajoute le dossier REPORT_DIR pour être sûr de tout supprimer
>>>>>>> Stashed changes
clean:
	find . -type f \( \
		-name "*.aux" -o -name "*.log" -o -name "*.out" -o -name "*.toc" \
		-o -name "*.lof" -o -name "*.lot" -o -name "*.bbl" -o -name "*.blg" \
		-o -name "*.maf" -o -name "*.mtc*" -o -name "*.thm" -o -name "*.synctex.gz" \
		-o -name "*.ptc*" -o -name "*.fls" -o -name "*.fdb_latexmk" \
		-o -name "*.bcf" -o -name "*.run.xml" \
	\) -delete

# Nettoyage complet
cleanall: clean
	@echo "==> Suppression du PDF..."
	@rm -f $(PDF_NAME).pdf