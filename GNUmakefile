TAG = $(shell git describe --tags --always --dirty)

%.sh: %.sh.in
	sed -e "s/__VERSION__/\"${TAG}\"/" $^ >$@
	chmod 755 $@

%.sh.d: %.sh.in
	@echo "$(shell echo $@ | sed -e 's/.d//') : $^" >$@

SCRIPTS_IN := $(shell find . -name '*.sh.in')
TARGETS = $(SCRIPTS_IN:.sh.in=.sh)
deps = $(SCRIPTS_IN:.sh.in=.sh.d)

all: $(TARGETS)

clean:
	@rm -f *~ $(TARGETS) *.d

-include $(deps)
