#
# maketex
#

TEX=mac-024-slides
LATEX=pdflatex
PDFLATEX=pdflatex
BIBTEX=bibtex
XDVI=xdvi
XPDF= evince
DVIPDF=dvipdf
DVIPS=dvips
PS2PDF=ps2pdf

$(TEX).aux:	$(TEX).tex *.tex
	echo $(AUX).tex
	$(LATEX) $(TEX)

dvipdf:    
	$(DVIPS) -t letter -o $(TEX).ps $(TEX).dvi
	$(PS2PDF)  $(TEX).ps  $(TEX).pdf
	rm  $(TEX).ps

bib:
	$(BIBTEX) $(TEX)

clean:
	rm -f *.aux  *.lot *.bbl *.blg *.log *.dvi  *.ps *.toc *.out *.snm *.nav rss RSS *.nav *.out *.snm 

cleanup:	clean
	rm -f *~ *.gz *.backup

dvi:	
	$(XDVI) $(TEX)&

view:
	$(XDVI) $(TEX)&


pdf:
	$(XPDF)  $(TEX).pdf &

all: 
	$(LATEX)  $(TEX)
#	$(BIBTEX) $(TEX)
#	$(LATEX)  $(TEX)
	$(LATEX)  $(TEX)

edit:
#	emacs -rv  $(TEX).tex&
	kile  $(TEX).tex&

complete: clean all dvipdf pdf

tar: cleanup
	tar -zcvf   $(TEX).tar.gz *

beam:
	$(LATEX)  #cil28-0398pres.tex 
	$(DVIPDF) # cil28-0398pres
pres:
	$(XPDF) #cil28-0398pres.pdf

mail: tar # envia um e-mail com a data e hora para $(MAILADRESS)
	date | mail  -s  $(TEX):06:tgz  -a  $(TEX).tar.gz  goliatt@gmail.com
