TARGET = gnu_make_example

CC = g++
CFLAGS = -g -Wall -Wfatal-errors -std=c++17
OBJ = main.o answer.o

.DEFAULT_GOAL = $(TARGET)

.PHONY: $(TARGET) clean

%.o: %.c $(DEPS)
	$(CC) -c -o $@ $< $(CFLAGS)

$(TARGET): $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS)
	
clean:
	rm -f *.o $(TARGET)