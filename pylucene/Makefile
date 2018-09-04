TAG = coady/pylucene

all:
	docker build -t $(TAG) -t $(TAG):7 -t $(TAG):7.4 -t $(TAG):7.4.0 .

check: all
	docker run --rm $(TAG) python -c 'import lucene; assert lucene.initVM()'

3.7 3.6 2:
	docker build --build-arg VERSION=$@ -t $(TAG):py$@ .
