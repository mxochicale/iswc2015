
fileinfo := LaTeX Makefile
author := Miguel Angel Perez-Xochicale
version := alpha1

#References
#http://tex.stackexchange.com/questions/40738/how-to-properly-make-a-latex-project
#https://danielkaes.wordpress.com/2009/03/14/compiling-latex-documents-using-makefiles/
#http://www.cs.berkeley.edu/~jaein/notes/Makefile.pdflatex

# TODO:
# *add some of the following tools http://www.cs.berkeley.edu/~jaein/notes/Makefile.pdflatex 
#

# CHANGES:
# MAPX (2015-03-24):
# * Bumped version to alpha1
# * added LATEX, BIB variables

# IMPORTANT!
#
#
#


FILENAME = article
LATEX = pdflatex -shell-escape -interaction=nonstopmode -file-line-error
BIB = bibtex

all: 
	$(LATEX) $(FILENAME).tex
	$(LATEX) $(FILENAME).tex
	$(BIB) $(FILENAME)
	$(BIB) $(FILENAME)
	$(LATEX) $(FILENAME).tex
	$(LATEX) $(FILENAME).tex
	evince $(FILENAME).pdf &

clean:         
	rm -f *~
	rm -rf *.backup
	rm -f `ls $(FILENAME).* | grep -v .tex | grep -v .pdf`
	echo "Cleaning complete!"



