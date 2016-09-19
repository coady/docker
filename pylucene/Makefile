TAG = coady/pylucene

all:
	docker build -t $(TAG) -t $(TAG):6 -t $(TAG):6.2 -t $(TAG):6.2.0 .

check: all
	docker run --rm $(TAG) python -c 'import lucene; assert lucene.initVM()'
