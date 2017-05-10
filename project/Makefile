CXX = g++
CXXFLAGS = -O2 -Wall -std=c++11 -Iinclude
LDFLAGS =
 
EXE = main
SRCDIR = src
BINDIR = bin
 
OBJECTS = $(patsubst $(SRCDIR)/%.cpp,$(BINDIR)/%.o,$(wildcard $(SRCDIR)/*.cpp))
 
all: $(EXE)
 
$(EXE): $(BINDIR) $(OBJECTS)
	$(CXX) $(OBJECTS) -o $(EXE) $(LDFLAGS)
 
$(BINDIR)/%.o: $(SRCDIR)/%.cpp
	$(CXX) $(CXXFLAGS) -c -MMD -o $@ $<
 
include $(wildcard $(BINDIR)/*.d)
 
$(BINDIR):
	mkdir -p $(BINDIR)

val_check:
	g++ -I ./include -g $(CXXFLAGS) src/main.cpp
	valgrind --tool=memcheck --track-origins=yes --error-limit=no --leak-check=full --show-leak-kinds=all ./a.out roslaunch agitr example.launch
 
clean:
	rm -rf $(BINDIR) $(EXE)
 
.PHONY: clean all
