CXX = g++
CXXVER = $(shell $(CXX) --version | grep -P '\d+.\d+.\d+' -o)
CXXVER_MAJOR = $(shell $(CXX) --version | grep -P '\d+.\d+.\d+' -o | cut -d'.' -f1)
CXXVER_MINOR = $(shell $(CXX) --version | grep -P '\d+.\d+.\d+' -o | cut -d'.' -f2)
CXXVER_PATCH = $(shell $(CXX) --version | grep -P '\d+.\d+.\d+' -o | cut -d'.' -f3)

ifneq ($(CXXVER_MAJOR),8)
$(error "g++ version >= 8 required")
endif

SRC = $(shell ls ./Source/*.cpp)
# SRC = $(shell cd ./Source && ls *.cpp)
OBJ = $(patsubst %.cpp, %.o, $(SRC))

CFLAGS = -std=c++17 -I ./Include -L /mingw64/lib/gcc/x86_64-w64-mingw32/8.3.0 -Wno-narrowing
# LDFLAGS = -lstdc++fs
LDFLAGS = -lstdc++ -lstdc++fs

.PHONY: mcdc clean debug

mcdc: $(OBJ)
	$(CXX) $(OBJ) $(CFLAGS) $(LDFLAGS) -o mcdc

%.o: %.cpp
# .cpp.o:
	$(CXX) -c $(CFLAGS) $< -o $@

clean:
	rm -f prog $(OBJ)

debug:
	@echo $(SRC)
	@echo $(OBJ)
	@echo $(CXXVER)
	@echo $(CXXVER_MAJOR)
	@echo $(CXXVER_MINOR)
	@echo $(CXXVER_PATCH)

