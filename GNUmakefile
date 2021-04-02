IMGUI    := imgui
SRC      := $(IMGUI)/imgui.cpp \
            $(IMGUI)/imgui_demo.cpp \
            $(IMGUI)/imgui_draw.cpp \
            $(IMGUI)/imgui_tables.cpp \
            $(IMGUI)/imgui_widgets.cpp \
            $(IMGUI)/backends/imgui_impl_glfw.cpp \
            $(IMGUI)/backends/imgui_impl_opengl3.cpp \
            main.cpp
OBJ      := $(patsubst %.cpp, %.o, $(SRC))
CXXFLAGS := -std=c++17 -I/usr/local/include -I$(IMGUI) -I$(IMGUI)/backends -g -Wall -Wformat
LDFLAGS  := -framework OpenGL -framework Cocoa -framework IOKit -framework CoreVideo -L/usr/local/lib -lglfw -lGLEW
PROG     := imgui-test

all: $(IMGUI) $(PROG)

$(PROG): $(OBJ)
	$(CXX) $(CXXFLAGS) $^ $(LDFLAGS) -o $@

%.o: $(SRC)/%cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

$(IMGUI):
	git submodule update --init --recursive

clean:
	rm -f $(OBJ) $(PROG) *.ini
