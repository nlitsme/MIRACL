# note: run this from the root of MIRACL using make -f lib/Makefile

all: include/mirdef.h bmark fact mersenne brent sample ecsgen ecsign ecsver pk-demo schoof factor

clean:
	$(RM) *.exe
	$(RM) miracl.a

include/mirdef.h:
	ln -sf mirdef.h64 include/mirdef.h
	ln -sf mrmuldv.g64 source/mrmuldv.c

miracl.a: mrcore.o mrarth0.o mrarth1.o mrarth2.o mralloc.o mrsmall.o mrzzn2.o mrzzn3.o mrio1.o mrio2.o mrjack.o mrgcd.o mrxgcd.o mrarth3.o mrbits.o mrecn2.o mrzzn4.o mrrand.o mrprime.o mrcrt.o mrscrt.o mrmonty.o mrcurve.o mrsroot.o mrzzn2b.o mrpower.o mrfast.o mrshs.o mrshs256.o mraes.o mrlucas.o mrstrong.o mrgcm.o    mrflash.o mrfrnd.o mrdouble.o mrround.o mrbuild.o mrflsh1.o mrpi.o mrflsh2.o mrflsh3.o mrflsh4.o mrbrick.o mrebrick.o mrec2m.o mrgf2m.o mrmuldv.o mrshs512.o mrsha3.o mrfpe.o
	$(AR) rc $@ $^

%.o:source/%.cpp
	$(CXX) -c -O3 -o $@ $^  -I include
%.o:source/curve/%.cpp
	$(CXX) -c -O3 -o $@ $^  -I include
%.o:source/%.c
	$(CC) -c -O3 -o $@ $^  -I include
%:%.o
	$(CXX) -o $@ $^

bmark: bmark.o miracl.a
fact: fact.o big.o miracl.a
mersenne: mersenne.o big.o miracl.a
brent: brent.o big.o zzn.o miracl.a
sample: sample.o flash.o miracl.a
ecsgen: ecsgen.o ecn.o big.o miracl.a
ecsign: ecsign.o ecn.o big.o miracl.a
ecsver: ecsver.o ecn.o big.o miracl.a
pk-demo: pk-demo.o ecn.o big.o miracl.a
schoof: schoof.o polymod.o poly.o ecn.o crt.o zzn.o big.o miracl.a
factor: factor.o miracl.a

