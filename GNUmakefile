################################################################################
# GNUmakefile
#
# Makefile for all the scripts...
################################################################################

TAG = $(shell git describe --tags --always --dirty)

%.sh: %.sh.in
	sed -e "s/__VERSION__/\"${TAG}\"/" $^ >$@
	chmod 755 $@

%.py: %.py.in
	sed -e "s/__VERSION__/\"${TAG}\"/" $^ >$@
	chmod 755 $@

%.sh.d: %.sh.in
	@echo "$(shell echo $@ | sed -e 's/.d//') : $^" >$@

%.py.d: %.py.in
	@echo "$(shell echo $@ | sed -e 's/.d//') : $^" >$@

SHELL_IN := $(shell find . -name '*.sh.in')
PYTHON_IN := $(shell find . -name '*.py.in')
TARGETS = $(SHELL_IN:.sh.in=.sh) $(PYTHON_IN:.py.in=.py)
deps = $(SHELL_IN:.sh.in=.sh.d) $(PYTHON_IN:.py.in=.py.d)

all: $(TARGETS)

clean:
	rm -f *~ $(TARGETS) *.d

-include $(deps)
