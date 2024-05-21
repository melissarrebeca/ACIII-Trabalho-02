SOURCES = instructions.c register_status.c reorder_buffer.c reservation_station.c simulator.c

export CFLAGS = -Wall -Wextra -Werror

.PHONY: initializer


all: initializer run clean

initializer:
	gcc $(CFLAGS) $(SOURCES) -o out

run:
	@./out

clean:
	@rm -f out
