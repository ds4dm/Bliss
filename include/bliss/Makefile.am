header-links: remove-links
	HEADERLIST="$(top_srcdir)/bliss_*.h $(top_srcdir)/*.hh" ; \
	for hh in $$HEADERLIST; do \
		BASENAME=`basename $$hh`; \
		test -e $$BASENAME || $(LN_S) $$hh $$BASENAME; \
	done

remove-links:
	$(RM) bliss_*.h *.hh

all-local: header-links

clean-local: remove-links
