TAG = coady/pylucene

all:
	docker build -t $(TAG) .

check: all
	docker run --rm $(TAG) python -c 'import lucene; assert lucene.initVM()'
