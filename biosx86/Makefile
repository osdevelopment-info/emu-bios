NASM = /usr/bin/nasm
NASM_OPTS = -f bin

all: license bios86 bios286 bios386 pdf

license: biosx86.nw
	notangle -Rlicense biosx86.nw > LICENSE

bios86.asm: biosx86.nw
	notangle -Rbios86.asm biosx86.nw > bios86.asm

bios86: bios86.asm
	$(NASM) $(NASM_OPTS) bios86.asm -l bios86.lst -o bios86

bios286.asm: biosx86.nw
	notangle -Rbios286.asm biosx86.nw > bios286.asm

bios286: bios286.asm
	$(NASM) $(NASM_OPTS) bios286.asm -l bios286.lst -o bios286

bios386.asm: biosx86.nw
	notangle -Rbios386.asm biosx86.nw > bios386.asm

bios386: bios386.asm
	$(NASM) $(NASM_OPTS) bios386.asm -l bios386.lst -o bios386

pdf: biosx86.nw
	nodefs biosx86.nw | sort -u > biosx86.defs
	noweave -indexfrom biosx86.defs -delay biosx86.nw > biosx86.tex
	xelatex -8bit biosx86
	splitindex biosx86.idx
	makeglossaries biosx86
	xelatex -8bit biosx86
	xelatex -8bit biosx86

clean:
	rm -f *~
	rm -f *.acn
	rm -f *.acr
	rm -f *.alg
	rm -f *.aux
	rm -f *.defs
	rm -f *.glg
	rm -f *.glo
	rm -f *.gls
	rm -f *.glsdefs
	rm -f *.idx
	rm -f *.ilg
	rm -f *.ind
	rm -f *.ins-glg
	rm -f *.ins-glo
	rm -f *.ins-gls
	rm -f *.ist
	rm -f *.log
	rm -f *.out
	rm -f *.tex
	rm -f *.toc
	rm -f *.lst
