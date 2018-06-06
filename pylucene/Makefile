TAG = coady/pylucene

all:
	docker build -t $(TAG) -t $(TAG):6 -t $(TAG):6.5 -t $(TAG):6.5.0 .

check: all
	docker run --rm $(TAG) python -c 'import lucene; assert lucene.initVM()'

3.6 2:
	docker build --build-arg VERSION=$@ -t $(TAG):py$@ .
