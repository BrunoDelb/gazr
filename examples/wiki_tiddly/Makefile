.PHONY: wiki-tiddly

WIKI_TIDDLY_PORT_WR=8889
WIKI_TIDDLY_PORT_RO=8888
WIKI_TIDDLY_USERNAME="bruno"
WIKI_TIDDLY_PASSWORD="mypassword"
WIKI_TIDDLY_PORT=8889

wiki-tiddly-create:
	docker run -d --rm -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki agilelabtest/tiddlywiki init-wiki

wiki-tiddly-open-wr:
	open "http://localhost:${WIKI_TIDDLY_PORT_WR}"

wiki-tiddly-open-ro:
	open "http://localhost:${WIKI_TIDDLY_PORT_RO}"

wiki-tiddly:
	docker run -d -p $(WIKI_TIDDLY_PORT_WR):8081 --restart=always -e PORT=8081 -e USERNAME=$(WIKI_TIDDLY_USERNAME) -e PASSWORD=$(WIKI_TIDDLY_PASSWORD)  -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki-w agilelabtest/tiddlywiki write-wiki $(WIKI_TIDDLY_USERNAME) $(WIKI_TIDDLY_PASSWORD)

wiki-tiddly-ro:
	docker run -d -p $(WIKI_TIDDLY_PORT_RO):8080 --restart=always -e PORT=8080 -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki-r agilelabtest/tiddlywiki readonly-wiki
