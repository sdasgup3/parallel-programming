CHARMC=~/charm/net-linux-x86_64/bin/charmc $(OPTS)
TEST=fib

all: $(TEST)

$(TEST):   $(TEST).o
	$(CHARMC) -tracemode projections $(TEST).o -o $(TEST) -language charm++ 

$(TEST).o : $(TEST).C $(TEST).def.h $(TEST).decl.h
	$(CHARMC) -I../../../src/charj/libs/ -c $(TEST).C

$(TEST).def.h $(TEST).decl.h : $(TEST).ci
	$(CHARMC) $(TEST).ci

test: all
	./charmrun +p4 $(TEST) 9   ++local

clean:
	rm -f conv-host *.o charmrun $(TEST)
	rm -f *.def.h *.decl.h
	rm -f *.log.gz *.projrc *.topo *.sts log

