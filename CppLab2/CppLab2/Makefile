CXX = g++
CXXFLAGS = -Wall -g
LIBS = -lsqlite3

SRCDIR = .
INCDIR = .
BUILDDIR = build
BINDIR = bin

TARGET = $(BINDIR)/my_program
SOURCES = $(wildcard $(SRCDIR)/*.cpp)
OBJECTS = $(patsubst $(SRCDIR)/%.cpp, $(BUILDDIR)/%.o, $(SOURCES))
DEPS = $(OBJECTS:.o=.d)

.PHONY: all clean

all: $(TARGET)

$(TARGET): $(OBJECTS)
	@mkdir -p $(BINDIR)
	$(CXX) $(CXXFLAGS) $^ -o $@ $(LIBS)

$(BUILDDIR)/%.o: $(SRCDIR)/%.cpp
	@mkdir -p $(BUILDDIR)
	$(CXX) $(CXXFLAGS) -I$(INCDIR) -MMD -MP -c $< -o $@

clean:
	rm -rf $(BUILDDIR) $(BINDIR)

-include $(DEPS)