FILE=ml_intro
PANDOC_CMD=pandoc --shift-heading-level-by=-1 -t slidy -s $(FILE).md -o $(FILE).html

all:
	$(PANDOC_CMD)
self-contained:
	$(PANDOC_CMD) --embed-resources
preview: all
	gio open $(FILE).html
clean:
	rm -rf $(FILE).html
open:
	gio open `git remote get-url origin`
