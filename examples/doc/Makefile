.PHONY: doc

doxygen:
	# Le fichier Doxyfile doit avoir la configuration suivante :
	# - PROJECT_NAME contient le nom du projet
	# - INPUT pointe vers le répertoire d'entrée
	# - FILE_PATTERNS contient la liste des extensions (exemple : "*.java *.kt")
	# - RECURSIVE = YES
	@ DOXYFILE=Doxyfile DOC_HTML=doc_html.zip DOC_RTF=doc_rtf.zip DOC_XML=doc_xml.zip docker run --rm -it --name doxygen -v $(pwd)/src:/src -v $(pwd)/report/:/report agilelabtest/doxygen /run-doxygen.sh

feature-book:
	# Le répertoire ./src doit pointer vers le répertoire où se trouvent les fichiers features et de configuration FeatureBook
	docker run --rm -it --name feature_book -e REPORT_FILE=feature_book.pdf -v $(pwd)/src:/src -v $(pwd)/report/:/report agilelabtest/feature_book get_feature_book
	ls ./report/
