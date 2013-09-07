SRC=./COMBINE-python-workshop-flyer.txt

all: prereqs html pdf

# Check if 'pandoc' is installed on the system, it is needed to compile
# the various documents.
prereqs:
	@( if ! type pandoc 2> /dev/null > /dev/null ; \
	then \
		echo "ERROR: 'pandoc' is not installed ..." 1>&2 ; \
		echo "INSTALLING 'pandoc' ..." 1>&2 ; \
		sudo apt-get install pandoc ; \
	fi )

html: ${SRC}
	pandoc ${SRC} -o `basename ${SRC} .txt`.html -f markdown+multiline_tables

pdf: ${SRC} 
	pandoc ${SRC} -o `basename ${SRC} .txt`.pdf \
		-f markdown+multiline_tables \
		-H `basename ${SRC} .txt`.preamble \
		--variable geometry:margin=20mm --variable fontsize=12pt \

clean:
	\rm -rf ./*.pdf ./*.aux ./*.out ./*.nav ./*.snm ./*.toc ./*.fls ./*.log
	\rm -rf ./*.html
