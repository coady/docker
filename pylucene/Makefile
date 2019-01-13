TAG = coady/pylucene

all:
	docker build -t $(TAG) -t $(TAG):7 -t $(TAG):7.6 -t $(TAG):7.6.0 .

check: all
	docker run --rm $(TAG) python -c 'import lucene; assert lucene.initVM()'
