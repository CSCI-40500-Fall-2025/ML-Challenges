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
deploy: all
	scp -J Raffi.Khatchadourian99@eniac.cs.hunter.cuny.edu $(FILE).html khatchad@compsci.hunter.cuny.edu:~/public_html/media/$(FILE)
	scp -J Raffi.Khatchadourian99@eniac.cs.hunter.cuny.edu -r graphics khatchad@compsci.hunter.cuny.edu:~/public_html/media/$(FILE)
