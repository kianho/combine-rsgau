# DEPENDENCIES
# 	pandoc version >= 1.10.1
# 		NOTE: the version in your Ubuntu APT repository may be too old, visit 
# 		http://johnmacfarlane.net/pandoc/installing.html#all-platforms for
# 		instructions on installing the latest stable version. 
# 	latex
# 		Installable via the conventional Ubuntu 'apt-get install' command-line
# 		program.

SRC=./COMBINE-python-workshop-flyer.md
BASENAME=`basename ${SRC} .md`
DEPLOYDIR=~/Dropbox/Public/COMBINE/docs

all: html pdf txt

html: ${SRC}
	pandoc ${SRC} -o ${BASENAME}.html -f markdown+multiline_tables

pdf: ${SRC} 
	pandoc ${SRC} -o ${BASENAME}.pdf \
		-f markdown+multiline_tables -H ${BASENAME}.preamble \
		--variable geometry:margin=35mm --variable fontsize=12pt \
		--variable geometry:a3paper

txt: ${SRC}
	pandoc ${SRC} -o ${BASENAME}.txt -f markdown+multiline_tables -t plain

deploy: all
	( if [ ! -d ${DEPLOYDIR} ] ; then mkdir -vp ${DEPLOYDIR} ; fi )
	( cp ./${BASENAME}.html ./${BASENAME}.pdf ./${BASENAME}.txt ${DEPLOYDIR} )
	( cp -rp ./images/ ${DEPLOYDIR} )


clean:
	\rm -rf ./*.pdf ./*.aux ./*.out ./*.nav ./*.snm ./*.toc ./*.fls ./*.log
