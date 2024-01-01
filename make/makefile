
sources = $(wildcard ../oscar64/*.cpp)
objects = $(patsubst ../oscar64/%.cpp,%.o,$(sources))

CXX = c++
CPPFLAGS = -g -O2 -std=c++11 -Wno-switch

%.o: ../oscar64/%.cpp
	$(CXX) -c $(CPPFLAGS) $< -o $@

%.d: ../oscar64/%.cpp
	@set -e; rm -f $@; \
	$(CC) -MM $(CPPFLAGS) $< > $@.$$$$; \
	sed 's,\($*\)\.o[ :]*,\1.o $@ : ,g' < $@.$$$$ > $@; \
	rm -f $@.$$$$

../bin/oscar64 : $(objects)
	mkdir -p ../bin
	$(CXX) $(CPPFLAGS) $(objects) -o ../bin/oscar64

.PHONY : clean
clean :
	-rm -f *.o *.d ../bin/oscar64

-include $(objects:.o=.d)
