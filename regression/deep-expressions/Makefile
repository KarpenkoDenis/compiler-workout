TESTS=$(basename $(wildcard generated*.expr))

RC = ../../src/rc.opt

.PHONY: check $(TESTS)

check: $(TESTS)

$(TESTS): %: %.expr
	cat $@.input | $(RC) -i $< > $@.log && diff $@.log orig/$@.log
	cat $@.input | $(RC) -s $< > $@.log && diff $@.log orig/$@.log

clean:
	find . -maxdepth 1 -name "*.log" -delete
	rm -f *.s *~ $(TESTS)
