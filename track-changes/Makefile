.PHONY: test clean

test: sample.md
	@pandoc -t markdown --wrap=preserve \
	        --lua-filter=track-changes.lua sample.md | \
	    diff -u - expected_accept.markdown
	@pandoc -t markdown --wrap=preserve --track-changes=reject \
	        -M trackChanges:reject --lua-filter=track-changes.lua sample.md | \
	    diff -u - expected_reject.markdown
	@pandoc -s -t latex --wrap=preserve --track-changes=all \
	        -M trackChanges:all --lua-filter=track-changes.lua sample.md | \
	    diff -u - expected_draft.tex
	@pandoc -s -t html --wrap=preserve --track-changes=all \
	        -M trackChanges:all --lua-filter=track-changes.lua sample.md | \
	    diff -u - expected_draft.html
