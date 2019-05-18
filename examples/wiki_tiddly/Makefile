WIKI_TIDDLY_PORT_WR=8889
WIKI_TIDDLY_PORT_RO=8888
WIKI_TIDDLY_USERNAME="myuser"
WIKI_TIDDLY_PASSWORD="mypassword"

wiki-tiddly-create:
	docker run -d --rm -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki agilelabtest/tiddlywiki init-wiki

wiki-tiddly-open:
	open "http://localhost:${WIKI_TIDDLY_PORT_WR}"

wiki-tiddly-open-ro:
	open "http://localhost:${WIKI_TIDDLY_PORT_RO}"

wiki-tiddly:
	docker run -d -p $(WIKI_TIDDLY_PORT_WR):8081 --restart=always -e PORT=8081 -e USERNAME=$(WIKI_TIDDLY_USERNAME) -e PASSWORD=$(WIKI_TIDDLY_PASSWORD)  -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki-w agilelabtest/tiddlywiki write-wiki $(WIKI_TIDDLY_USERNAME) $(WIKI_TIDDLY_PASSWORD)

wiki-tiddly-ro:
	docker run -d -p $(WIKI_TIDDLY_PORT_RO):8080 --restart=always -e PORT=8080 -v `pwd`/wiki:/var/lib/tiddlywiki/wiki --name tiddlywiki-r agilelabtest/tiddlywiki readonly-wiki

.PHONY: wiki-tiddly-create wiki-tiddly-open wiki-tiddly-open-ro wiki-tiddly wiki-tiddly-ro
