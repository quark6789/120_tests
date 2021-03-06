# Makefile to compile Umix Programming Assignment 2 (pa2)

LIBDIR = $(UMIXPUBDIR)/lib
PA2DIR = $(HOME)/pa2

CC 	= cc 
FLAGS 	= -g -L$(LIBDIR) -lumix2

TESTS = t1 t2 t3 t4
TESTDEPS = t1.c t2.c t3.c t4.c t4count.sh t4output1.txt schedarbitrary.h schedfifo.h schedlifo.h schedroundrobin.h schedproportional.h

test:  $(TESTS)

$(PA2DIR)/mycode2arbitrary.o:	$(PA2DIR)/mycode2.c $(PA2DIR)/aux.h $(PA2DIR)/sys.h $(PA2DIR)/mycode2.h schedarbitrary.h
	@cp schedarbitrary.h $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o mycode2arbitrary.o -c mycode2.c -include schedarbitrary.h

$(PA2DIR)/mycode2fifo.o:	$(PA2DIR)/mycode2.c $(PA2DIR)/aux.h $(PA2DIR)/sys.h $(PA2DIR)/mycode2.h schedfifo.h
	@cp schedfifo.h $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o mycode2fifo.o -c mycode2.c -include schedfifo.h

$(PA2DIR)/mycode2lifo.o:	$(PA2DIR)/mycode2.c $(PA2DIR)/aux.h $(PA2DIR)/sys.h $(PA2DIR)/mycode2.h schedlifo.h
	@cp schedlifo.h $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o mycode2lifo.o -c mycode2.c -include schedlifo.h
	
$(PA2DIR)/mycode2roundrobin.o:	$(PA2DIR)/mycode2.c $(PA2DIR)/aux.h $(PA2DIR)/sys.h $(PA2DIR)/mycode2.h schedroundrobin.h
	@cp schedroundrobin.h $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o mycode2roundrobin.o -c mycode2.c -include schedroundrobin.h
	
$(PA2DIR)/mycode2proportional.o:	$(PA2DIR)/mycode2.c $(PA2DIR)/aux.h $(PA2DIR)/sys.h $(PA2DIR)/mycode2.h schedproportional.h
	@cp schedproportional.h $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o mycode2proportional.o -c mycode2.c -include schedproportional.h

t1:	t1.c $(PA2DIR)/aux.h $(PA2DIR)/umix.h $(PA2DIR)/mycode2fifo.o
	@cp t1.c $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o t1 t1.c mycode2fifo.o
	cd $(PA2DIR) && \
	  ./t1

t2:	t2.c $(PA2DIR)/aux.h $(PA2DIR)/umix.h $(PA2DIR)/mycode2lifo.o
	@cp t2.c $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o t2 t2.c mycode2lifo.o
	cd $(PA2DIR) && \
	  ./t2
	
t3:	t3.c $(PA2DIR)/aux.h $(PA2DIR)/umix.h $(PA2DIR)/mycode2roundrobin.o
	@cp t3.c $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o t3 t3.c mycode2roundrobin.o
	cd $(PA2DIR) && \
	  ./t3
	
t4:	t4.c $(PA2DIR)/aux.h $(PA2DIR)/umix.h $(PA2DIR)/mycode2proportional.o
	@cp t4.c $(PA2DIR)
	@cp t4count.sh $(PA2DIR)
	@cd $(PA2DIR) && \
	  $(CC) $(FLAGS) -o t4 t4.c mycode2proportional.o
	cd $(PA2DIR) && \
	  ./t4

clean:
	@cd $(PA2DIR) && \
	  rm -f *.o $(TESTS) $(TESTDEPS)
