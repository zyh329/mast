
## Manual pages
man_MANS = \
	mast_info.1 \
	mast_cast.1 \
	mast_filecast.1 \
	mast_rawcast.1 \
	mast_record.1 \
	mast_rawrecord.1
	

HTMLPAGES =  README.html INSTALL.html TODO.html
HTMLMANPAGES = $(man_MANS:%=%.html)
XMLMANPAGES = $(man_MANS:%=%.xml)
ASCMANPAGES = $(man_MANS:%=%.asc)


## Tool Configuration
ASCIIDOC = @ASCIIDOC@ \
	-a revision="@PACKAGE_VERSION@" \
	-a theme=mast \
	-a linkcss \
	-a stylesdir=. 
XMLTO = @XMLTO@


## Only re-build documentation if tools are available
if BUILD_DOC 

INSTALL.html: ../INSTALL
	$(ASCIIDOC) -d article -b xhtml11 -o $@ $<

README.html: ../README
	$(ASCIIDOC) -d article -b xhtml11 -o $@ $<

TODO.html: ../TODO
	$(ASCIIDOC) -d article -b xhtml11 -o $@ $<

$(HTMLMANPAGES): %.html: %.asc
	$(ASCIIDOC) -d manpage -b xhtml11 -o $@ $<

$(XMLMANPAGES): %.xml: %.asc
	$(ASCIIDOC) -d manpage -b docbook -o $@ $<

$(man_MANS): %: %.xml
	$(XMLTO) man $<

endif



dist_doc_DATA = $(HTMLPAGES) $(HTMLMANPAGES)
DISTCLEANFILES = $(man_MANS) $(HTMLPAGES) $(HTMLMANPAGES)
CLEANFILES = $(XMLMANPAGES) manpage.links manpage.refs
EXTRA_DIST = $(ASCMANPAGES) $(man_MANS) $(HTMLPAGES) $(HTMLMANPAGES)
