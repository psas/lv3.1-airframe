.DEFAULT_GOAL := bendAnalysis.pdf
P := %

%.pdf: %.Rmd
	Rscript -e 'rmarkdown::render("$^", output_file="$@")'

.PHONY: clean watch

clean:
	-rm *.pdf

watch: bendAnalysis.Rmd
	# This kind of sucks because the way to exit out is with `pkill make`
	while true ; do \
		watch -g -t stat -c $PY $^ && make $(.DEFAULT_GOAL) ; \
	done 
