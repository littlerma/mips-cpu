
#
# How to make the check file
#
#   $ ./main_tb > main_tb.check
#
# How to check using the check file
#   $ diff main_tb.out main_tb.check

OBJS =	main_tb

all: $(OBJS)

%: %.v
	iverilog -I../ -I../../ -g2005 -o$@ $<

main_tb.v: main.hex
	../bin/gen_cpu_tb $< > $@

main_tb.vcd: main_tb
	./$<

test: main_tb
	./$< > main_tb.out
	diff main_tb.out main_tb.check

clean:
	-rm -f $(OBJS)
	-rm -f main_tb.out
	-rm -f main_tb.v
