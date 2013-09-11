SRC=./COMBINE-python-workshop-flyer.md
BASENAME=`basename ${SRC} .md`
DEPLOYDIR=~/Dropbox/Public/COMBINE/docs

all: prereqs html pdf txt

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
	pandoc ${SRC} -o ${BASENAME}.html -f markdown+multiline_tables

pdf: ${SRC} 
	pandoc ${SRC} -o ${BASENAME}.pdf \
		-f markdown+multiline_tables -H ${BASENAME}.preamble \
		--variable geometry:margin=15mm --variable fontsize=11pt \
		--variable geometry:a4paper

txt: ${SRC}
	pandoc ${SRC} -o ${BASENAME}.txt -f markdown+multiline_tables -t plain

deploy: all
	( if [ ! -d ${DEPLOYDIR} ] ; then mkdir -vp ${DEPLOYDIR} ; fi )
	( cp ./${BASENAME}.html ./${BASENAME}.pdf ./${BASENAME}.txt ${DEPLOYDIR} )
	( cp -rp ./images/ ${DEPLOYDIR} )


clean:
	\rm -rf ./*.pdf ./*.aux ./*.out ./*.nav ./*.snm ./*.toc ./*.fls ./*.log
	\rm -rf ./*.html
