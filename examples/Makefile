all: example.pdf

# If desired, the base class for this CustomLexer can be changed.
#export PYGMENTS_CUSTOM_BASE_LEXER  := CppLexer

# This module uses Environment Variables to add keywords for syntax
# highlighting. All are optional. Note that this maps strings to
# subtypes of Token.Keyword. (No regular expressions.)
export PYGMENTS_CUSTOM_TYPE        := [ "vec3", "Atom", "System" ]
export PYGMENTS_CUSTOM_CONSTANT    := [ 'M_PI', 'Tau' ]
export PYGMENTS_CUSTOM_KEYWORD     := [ 'xyzzy', 'plugh' ]
export PYGMENTS_CUSTOM_DECLARATION := [ 'def', 'fn' ]
export PYGMENTS_CUSTOM_NAMESPACE   := [ 'using', 'hello_my_name_is' ]
export PYGMENTS_CUSTOM_PSEUDO      := [ 'let' ]
export PYGMENTS_CUSTOM_RESERVED    := [ 'POKE' ]
export PYGMENTS_CUSTOM_REMOVED     := [ 'removed' ]


# Pattern rule for building the pdf from latex and C source files.
# Note 1: $< represents the latex filename.
# Note 2: The date embedded in the pdf is set to the last modification
#         time of the latex file according to the git commit log or
#         the file timestamp.
%.pdf: %.ltx %.c FORCE
	SOURCE_DATE_EPOCH=`(git log -1 --format=%at $< 2>/dev/null; \
			    date +%s -r $<) | head -1` \
		pdflatex -shell-escape $< 

# Always re-create the pdf at each `make`.
FORCE:

.PHONY: clean
clean:
	rm -rf *.aux *.log *.out.pyg  _minted-* *~
