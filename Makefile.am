## Process this file with automake to produce Makefile.in.

# Makefile.am
# Copyright (C) 2005 Free Software Foundation, Inc.
# 
# This file is part of GNU Classpath.
# 
# GNU Classpath is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2, or (at your option)
# any later version.
#  
# GNU Classpath is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.
# 
# You should have received a copy of the GNU General Public License
# along with GNU Classpath; see the file COPYING.  If not, write to the
# Free Software Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA
# 02111-1307 USA.

AM_GCJFLAGS = --classpath=$(CLASSPATH) -fassume-compiled -I$(srcdir)/src -I$(srcdir) -I$(ANTLR_JAR) -I.

USE_JAVAC_FLAGS = -classpath $(CLASSPATH):$(srcdir)/src:$(srcdir):$(ANTLR_JAR):. $(JAVAC_FLAGS)

LIBGCJCOMPILE = $(LIBTOOL) --tag=GCJ --mode=compile $(GCJ) $(AM_GCJFLAGS) $(GCJFLAGS) -c -MD -MT $@
GCJCOMPILE = $(LIBGCJCOMPILE) -MF $(@:.o=.d)
LTGCJCOMPILE = $(LIBGCJCOMPILE) -MF $(@:.lo=.d)

jar_DATA = com-sun-javadoc-$(VERSION).jar \
	com-sun-tools-doclets-Taglet-$(VERSION).jar \
	gnu-classpath-tools-gjdoc-$(VERSION).jar
jardir =  $(datadir)/java

BUILT_SOURCES = $(jar_DATA)

CLEANFILES = $(jar_DATA)

if ENABLE_NATIVE
bin_PROGRAMS = gjdoc
lib_LTLIBRARIES = lib-com-sun-javadoc.la lib-com-sun-tools-doclets-Taglet.la \
	lib-gnu-classpath-tools-gjdoc.la
else
bin_PROGRAMS =
lib_LTLIBRARIES =
endif

gjdoc_SOURCES = 
gjdoc_LINK = $(GCJLINK) $(gjdoc_LDFLAGS)
gjdoc_LDADD = -l-com-sun-javadoc -l-com-sun-tools-doclets-Taglet \
	-l-gnu-classpath-tools-gjdoc antlr.so \
	$(jni_linkflag)

gjdoc_LDFLAGS = --main=gnu.classpath.tools.gjdoc.Main \
	-Dgnu.gcj.runtime.VMClassLoader.library_control=never
gjdoc_DEPENDENCIES = lib-com-sun-javadoc.la \
	lib-com-sun-tools-doclets-Taglet.la \
	lib-gnu-classpath-tools-gjdoc.la \
	antlr.so

lib_com_sun_javadoc_la_SOURCES = \
	src/com/sun/tools/javadoc/Main.java \
	src/com/sun/javadoc/ClassDoc.java \
	src/com/sun/javadoc/ConstructorDoc.java \
	src/com/sun/javadoc/Doc.java \
	src/com/sun/javadoc/DocErrorReporter.java \
	src/com/sun/javadoc/Doclet.java \
	src/com/sun/javadoc/ExecutableMemberDoc.java \
	src/com/sun/javadoc/FieldDoc.java \
	src/com/sun/javadoc/MemberDoc.java \
	src/com/sun/javadoc/MethodDoc.java \
	src/com/sun/javadoc/PackageDoc.java \
	src/com/sun/javadoc/ParamTag.java \
	src/com/sun/javadoc/Parameter.java \
	src/com/sun/javadoc/ProgramElementDoc.java \
	src/com/sun/javadoc/RootDoc.java \
	src/com/sun/javadoc/SeeTag.java \
	src/com/sun/javadoc/SerialFieldTag.java \
	src/com/sun/javadoc/SourcePosition.java \
	src/com/sun/javadoc/Tag.java \
	src/com/sun/javadoc/ThrowsTag.java \
	src/com/sun/javadoc/Type.java \
	src/com/sun/javadoc/TypeVariable.java

lib_com_sun_tools_doclets_Taglet_la_SOURCES = \
	src/com/sun/tools/doclets/Taglet.java

if ENABLE_XMLDOCLET
XML_SRC = \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/DocTranslet.java \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/DocTransletConfigurationException.java \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/DocTransletException.java \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/DocTransletOptions.java \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/JarClassLoader.java \
	src/gnu/classpath/tools/doclets/xmldoclet/doctranslet/OutputFileInfo.java \
	src/gnu/classpath/tools/doclets/xmldoclet/Driver.java \
	src/gnu/classpath/tools/doclets/xmldoclet/Driver1_4.java \
	src/gnu/classpath/tools/doclets/xmldoclet/TargetContext.java
else
XML_SRC =
endif

lib_gnu_classpath_tools_gjdoc_la_SOURCES = \
	$(lib_gnu_classpath_tools_gjdoc_la_BASE_SOURCES) \
	gnu/classpath/tools/gjdoc/expr/JavaLexer.java \
	gnu/classpath/tools/gjdoc/expr/JavaRecognizer.java \
	gnu/classpath/tools/gjdoc/expr/JavaTokenTypes.java

EXTRA_DIST = src/gnu/classpath/tools/gjdoc/expr/java-expression.g \
	gjdoc.manifest contrib/texi2pod.pl javadoc.manifest

SUBDIRS = docs

lib_gnu_classpath_tools_gjdoc_la_BASE_SOURCES = \
	src/gnu/classpath/tools/doclets/debugdoclet/DebugDoclet.java \
	src/gnu/classpath/tools/doclets/htmldoclet/CssClass.java \
	src/gnu/classpath/tools/doclets/htmldoclet/ExternalDocSet.java \
	src/gnu/classpath/tools/doclets/htmldoclet/HtmlDoclet.java \
	src/gnu/classpath/tools/doclets/htmldoclet/HtmlPage.java \
	src/gnu/classpath/tools/doclets/htmldoclet/HtmlTagletContext.java \
	src/gnu/classpath/tools/doclets/AbstractDoclet.java \
	src/gnu/classpath/tools/doclets/DocletConfigurationException.java \
	src/gnu/classpath/tools/doclets/DocletOption.java \
	src/gnu/classpath/tools/doclets/DocletOptionColonSeparated.java \
	src/gnu/classpath/tools/doclets/DocletOptionFile.java \
	src/gnu/classpath/tools/doclets/DocletOptionFlag.java \
	src/gnu/classpath/tools/doclets/DocletOptionString.java \
	src/gnu/classpath/tools/doclets/DocletOptionPackageWildcard.java \
	src/gnu/classpath/tools/doclets/InlineTagRenderer.java \
	src/gnu/classpath/tools/doclets/InvalidPackageWildcardException.java \
	src/gnu/classpath/tools/doclets/PackageGroup.java \
	src/gnu/classpath/tools/doclets/PackageMatcher.java \
	src/gnu/classpath/tools/doclets/StandardTaglet.java \
	src/gnu/classpath/tools/doclets/TagletPrinter.java \
	src/gnu/classpath/tools/doclets/xmldoclet/HtmlRepairer.java \
	src/gnu/classpath/tools/FileSystemClassLoader.java \
	src/gnu/classpath/tools/IOToolkit.java \
	src/gnu/classpath/tools/StringToolkit.java \
	src/gnu/classpath/tools/NotifyingInputStreamReader.java \
	src/gnu/classpath/tools/MalformedInputEvent.java \
	src/gnu/classpath/tools/MalformedInputListener.java \
	src/gnu/classpath/tools/gjdoc/AbstractTagImpl.java \
	src/gnu/classpath/tools/gjdoc/ArrayCharacterIterator.java \
	src/gnu/classpath/tools/gjdoc/ClassDocImpl.java \
	src/gnu/classpath/tools/gjdoc/ClassDocReflectedImpl.java \
	src/gnu/classpath/tools/gjdoc/ClassDocProxy.java \
	src/gnu/classpath/tools/gjdoc/ConstructorDocImpl.java \
	src/gnu/classpath/tools/gjdoc/Debug.java \
	src/gnu/classpath/tools/gjdoc/DirectoryTree.java \
	src/gnu/classpath/tools/gjdoc/DocImpl.java \
	src/gnu/classpath/tools/gjdoc/ErrorReporter.java \
	src/gnu/classpath/tools/gjdoc/ExecutableMemberDocImpl.java \
	src/gnu/classpath/tools/gjdoc/FieldDocImpl.java \
	src/gnu/classpath/tools/gjdoc/GjdocPackageDoc.java \
	src/gnu/classpath/tools/gjdoc/GjdocRootDoc.java \
	src/gnu/classpath/tools/gjdoc/InheritDocTagImpl.java \
	src/gnu/classpath/tools/gjdoc/JavadocWrapper.java \
	src/gnu/classpath/tools/gjdoc/LinkTagImpl.java \
	src/gnu/classpath/tools/gjdoc/ValueTagImpl.java \
	src/gnu/classpath/tools/gjdoc/Main.java \
	src/gnu/classpath/tools/gjdoc/MemberDocImpl.java \
	src/gnu/classpath/tools/gjdoc/MethodDocImpl.java \
	src/gnu/classpath/tools/gjdoc/PackageDocImpl.java \
	src/gnu/classpath/tools/gjdoc/ParamTagImpl.java \
	src/gnu/classpath/tools/gjdoc/ParameterImpl.java \
	src/gnu/classpath/tools/gjdoc/ParseException.java \
	src/gnu/classpath/tools/gjdoc/Parser.java \
	src/gnu/classpath/tools/gjdoc/ProgramElementDocImpl.java \
	src/gnu/classpath/tools/gjdoc/RootDocImpl.java \
	src/gnu/classpath/tools/gjdoc/SeeTagImpl.java \
	src/gnu/classpath/tools/gjdoc/SerialFieldTagImpl.java \
	src/gnu/classpath/tools/gjdoc/SourcePositionImpl.java \
	src/gnu/classpath/tools/gjdoc/TagContainer.java \
	src/gnu/classpath/tools/gjdoc/TagImpl.java \
	src/gnu/classpath/tools/gjdoc/TemporaryStore.java \
	src/gnu/classpath/tools/gjdoc/TextTagImpl.java \
	src/gnu/classpath/tools/gjdoc/ThrowsTagImpl.java \
	src/gnu/classpath/tools/gjdoc/Timer.java \
	src/gnu/classpath/tools/gjdoc/TimerDoclet.java \
	src/gnu/classpath/tools/gjdoc/TypeImpl.java \
	src/gnu/classpath/tools/gjdoc/TypeVariableImpl.java \
	src/gnu/classpath/tools/gjdoc/WritableType.java \
	src/gnu/classpath/tools/gjdoc/expr/AdditionExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/AndExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryBitwiseExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryComputationExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryEqualityExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryLogicalExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryRelationExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BinaryShiftExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/BitShiftRightExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/CircularExpressionException.java \
	src/gnu/classpath/tools/gjdoc/expr/ConditionalExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantBoolean.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantByte.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantChar.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantDouble.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantFloat.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantInteger.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantLong.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantNull.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantShort.java \
	src/gnu/classpath/tools/gjdoc/expr/ConstantString.java \
	src/gnu/classpath/tools/gjdoc/expr/Context.java \
	src/gnu/classpath/tools/gjdoc/expr/DivisionExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/EqualExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/Evaluator.java \
	src/gnu/classpath/tools/gjdoc/expr/ExclusiveOrExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/Expression.java \
	src/gnu/classpath/tools/gjdoc/expr/GreaterThanExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/GreaterThanOrEqualExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/IdentifierExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/IllegalExpressionException.java \
	src/gnu/classpath/tools/gjdoc/expr/InclusiveOrExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/LessThanExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/LessThanOrEqualExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/LogicalAndExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/LogicalNotExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/LogicalOrExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/ModuloExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/MultiplicationExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/NegateExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/NotEqualExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/NotExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/EvaluatorEnvironment.java \
	src/gnu/classpath/tools/gjdoc/expr/ShiftLeftExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/ShiftRightExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/SubtractionExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/Type.java \
	src/gnu/classpath/tools/gjdoc/expr/TypeCastExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/UnaryExpression.java \
	src/gnu/classpath/tools/gjdoc/expr/UnknownIdentifierException.java \
	src/gnu/classpath/tools/java2xhtml/Java2xhtml.java \
	src/gnu/classpath/tools/taglets/AuthorTaglet.java \
	src/gnu/classpath/tools/taglets/CodeTaglet.java \
	src/gnu/classpath/tools/taglets/CopyrightTaglet.java \
	src/gnu/classpath/tools/taglets/DeprecatedTaglet.java \
	src/gnu/classpath/tools/taglets/GenericTaglet.java \
	src/gnu/classpath/tools/taglets/GnuExtendedTaglet.java \
	src/gnu/classpath/tools/taglets/SinceTaglet.java \
	src/gnu/classpath/tools/taglets/TagletContext.java \
	src/gnu/classpath/tools/taglets/ValueTaglet.java \
	src/gnu/classpath/tools/taglets/VersionTaglet.java \
	$(XML_SRC)

lib_gnu_classpath_tools_gjdoc_la_LIBADD = \
	$(lib_gnu_classpath_tools_gjdoc_la_CSS) \
	$(lib_gnu_classpath_tools_gjdoc_la_DTDS) \
	$(lib_gnu_classpath_tools_gjdoc_la_ENTS) \
	$(lib_gnu_classpath_tools_gjdoc_la_HTML) \
	$(lib_gnu_classpath_tools_gjdoc_la_JS) \
	$(lib_gnu_classpath_tools_gjdoc_la_PNG) \
	$(lib_gnu_classpath_tools_gjdoc_la_MODS) \
	$(lib_gnu_classpath_tools_gjdoc_la_PROPERTIES) \
	$(lib_gnu_classpath_tools_gjdoc_la_RNGS) \
	$(lib_gnu_classpath_tools_gjdoc_la_XSLS) \
	$(lib_gnu_classpath_tools_gjdoc_la_XHTML) \
	$(lib_gnu_classpath_tools_gjdoc_la_TXTS) \
	version.lo

gnu_classpath_tools_gjdoc_jar_CSS = \
	doctranslets/html/res/gjdochtml-clean.css \
	doctranslets/html/res/gjdochtml-fixed.css \
	doctranslets/html/res/gjdochtml-sclara.css \
	doctranslets/html/res/gjdochtml.css \
	htmldoclet/gjdochtml-vanilla.css \
	htmldoclet/gjdochtml-clean-layout.css \
	htmldoclet/gjdochtml-clean-color1.css

gnu_classpath_tools_gjdoc_jar_DTDS = \
	htmldoclet/xhtml11-target10.dtd \
	dtd/gjdoc-alphaindex.dtd \
	dtd/gjdoc.dtd

gnu_classpath_tools_gjdoc_jar_ENTS = \
	dtd/ent/iso-amsa.ent \
	dtd/ent/iso-amsb.ent \
	dtd/ent/iso-amsc.ent \
	dtd/ent/iso-amsn.ent \
	dtd/ent/iso-amso.ent \
	dtd/ent/iso-amsr.ent \
	dtd/ent/iso-box.ent \
	dtd/ent/iso-cyr1.ent \
	dtd/ent/iso-cyr2.ent \
	dtd/ent/iso-dia.ent \
	dtd/ent/iso-grk1.ent \
	dtd/ent/iso-grk2.ent \
	dtd/ent/iso-grk3.ent \
	dtd/ent/iso-grk4.ent \
	dtd/ent/iso-lat1.ent \
	dtd/ent/iso-lat2.ent \
	dtd/ent/iso-num.ent \
	dtd/ent/iso-pub.ent \
	dtd/ent/iso-tech.ent

gnu_classpath_tools_gjdoc_jar_HTML = doctranslets/html/res/default_help_en.html

gnu_classpath_tools_gjdoc_jar_JS = \
	doctranslets/html/res/gjdoc.js \
	htmldoclet/gjdoc.js

gnu_classpath_tools_gjdoc_jar_PNG = \
	htmldoclet/inherit.png

gnu_classpath_tools_gjdoc_jar_MODS = dtd/dbcentx.mod

gnu_classpath_tools_gjdoc_jar_PROPERTIES = htmldoclet/HtmlDoclet.properties

gnu_classpath_tools_gjdoc_jar_RNGS = \
	rng/gjdoc-classdoc.rng \
	rng/gjdoc-common.rng \
	rng/gjdoc-index.rng

gnu_classpath_tools_gjdoc_jar_TXTS = \
	java.lang-classes-1.2.txt \
	java.lang-classes-1.3.txt \
	java.lang-classes-1.4.txt \
	java.lang-classes-1.5.txt

gnu_classpath_tools_gjdoc_jar_XHTML = htmldoclet/help.xhtml

gnu_classpath_tools_gjdoc_jar_XSLS = \
	doctranslets/gjdoc_common.xsl \
	doctranslets/html/about.xsl \
	doctranslets/html/allclasses.xsl \
	doctranslets/html/allpackages.xsl \
	doctranslets/html/alphaindex.xsl \
	doctranslets/html/alphaindex_chunked.xsl \
	doctranslets/html/classdoc-source.xsl \
	doctranslets/html/classdoc-uses.xsl \
	doctranslets/html/classdoc.xsl \
	doctranslets/html/deprecated.xsl \
	doctranslets/html/descriptor.xsl \
	doctranslets/html/doctranslet.xsl \
	doctranslets/html/fulltree.xsl \
	doctranslets/html/gjdoc.xsl \
	doctranslets/html/help.xsl \
	doctranslets/html/html_common.xsl \
	doctranslets/html/index_noframes.xsl \
	doctranslets/html/index.xsl \
	doctranslets/html/packageclasses.xsl \
	doctranslets/html/packagedoc.xsl

lib_gnu_classpath_tools_gjdoc_la_GENSOURCES = gnu/classpath/tools/gjdoc/expr/JavaLexer.java gnu/classpath/tools/gjdoc/expr/JavaRecognizer.java gnu/classpath/tools/gjdoc/expr/JavaTokenTypes.java

com_sun_javadoc_jar_CLASSES = $(patsubst src/%.java,classes/%.class,$(lib_com_sun_javadoc_la_SOURCES))
com_sun_tools_doclets_Taglet_jar_CLASSES = $(patsubst src/%.java,classes/%.class,$(lib_com_sun_tools_doclets_Taglet_la_SOURCES))
gnu_classpath_tools_gjdoc_jar_CLASSES = $(patsubst src/%.java,classes/%.class,$(lib_gnu_classpath_tools_gjdoc_la_BASE_SOURCES))

gnu_classpath_tools_gjdoc_jar_GENCLASSES = $(patsubst %.java,classes/%.class,$(lib_gnu_classpath_tools_gjdoc_la_GENSOURCES))
lib_gnu_classpath_tools_gjdoc_la_CSS = $(patsubst %.css,%.lo,$(gnu_classpath_tools_gjdoc_jar_CSS))
lib_gnu_classpath_tools_gjdoc_la_DTDS = $(patsubst %.dtd,%.lo,$(gnu_classpath_tools_gjdoc_jar_DTDS))
lib_gnu_classpath_tools_gjdoc_la_ENTS = $(patsubst %.ent,%.lo,$(gnu_classpath_tools_gjdoc_jar_ENTS))
lib_gnu_classpath_tools_gjdoc_la_HTML = $(patsubst %.html,%.lo,$(gnu_classpath_tools_gjdoc_jar_HTML))
lib_gnu_classpath_tools_gjdoc_la_JS = $(patsubst %.js,%.lo,$(gnu_classpath_tools_gjdoc_jar_JS))
lib_gnu_classpath_tools_gjdoc_la_MODS = $(patsubst %.mod,%.lo,$(gnu_classpath_tools_gjdoc_jar_MODS))
lib_gnu_classpath_tools_gjdoc_la_PNG = $(patsubst %.png,%.lo,$(gnu_classpath_tools_gjdoc_jar_PNG))
lib_gnu_classpath_tools_gjdoc_la_PROPERTIES = $(patsubst %.properties,%.lo,$(gnu_classpath_tools_gjdoc_jar_PROPERTIES))
lib_gnu_classpath_tools_gjdoc_la_RNGS = $(patsubst %.rng,%.lo,$(gnu_classpath_tools_gjdoc_jar_RNGS))
lib_gnu_classpath_tools_gjdoc_la_XHTML = $(patsubst %.xhtml,%.lo,$(gnu_classpath_tools_gjdoc_jar_XHTML))
lib_gnu_classpath_tools_gjdoc_la_XSLS = $(patsubst %.xsl,%.lo,$(gnu_classpath_tools_gjdoc_jar_XSLS))
lib_gnu_classpath_tools_gjdoc_la_TXTS = $(patsubst %.txt,%.lo,$(gnu_classpath_tools_gjdoc_jar_TXTS))

$(lib_gnu_classpath_tools_gjdoc_la_GENSOURCES): \
		$(srcdir)/src/gnu/classpath/tools/gjdoc/expr/java-expression.g
	test -d gnu/classpath/tools/gjdoc/expr || mkdir -p gnu/classpath/tools/gjdoc/expr
	$(ANTLR) -o gnu/classpath/tools/gjdoc/expr $<

com-sun-javadoc-$(VERSION).jar: classes $(com_sun_javadoc_jar_CLASSES)
	$(JAR) cfm $@ $(srcdir)/javadoc.manifest -C classes com/sun/javadoc -C classes com/sun/tools/javadoc

com-sun-tools-doclets-Taglet-$(VERSION).jar: classes $(com_sun_tools_doclets_Taglet_jar_CLASSES)
	$(JAR) cf $@ -C classes com/sun/tools/doclets

gjdoc_resources = $(gnu_classpath_tools_gjdoc_jar_CSS) $(gnu_classpath_tools_gjdoc_jar_DTDS) \
	$(gnu_classpath_tools_gjdoc_jar_ENTS) $(gnu_classpath_tools_gjdoc_jar_HTML) \
	$(gnu_classpath_tools_gjdoc_jar_JS) $(gnu_classpath_tools_gjdoc_jar_MODS) \
	$(gnu_classpath_tools_gjdoc_jar_PNG) $(gnu_classpath_tools_gjdoc_jar_PROPERTIES) \
	$(gnu_classpath_tools_gjdoc_jar_RNGS) $(gnu_classpath_tools_gjdoc_jar_TXTS) \
	$(gnu_classpath_tools_gjdoc_jar_XHTML) $(gnu_classpath_tools_gjdoc_jar_XSLS)

gjdoc_resources_src = $(patsubst %, $(srcdir)/src/resources/%, $(gjdoc_resources))

gnu-classpath-tools-gjdoc-$(VERSION).jar: $(srcdir)/gjdoc.manifest src/resources/version.properties $(gnu_classpath_tools_gjdoc_jar_CLASSES) $(gnu_classpath_tools_gjdoc_jar_GENCLASSES) $(gjdoc_resources_src)
	for res in $(gjdoc_resources) ; \
	do  cp -u $(srcdir)/src/resources/$$res $$res ; done
	$(JAR) cfm $@ $(srcdir)/gjdoc.manifest \
	$(gjdoc_resources) \
	-C src/resources version.properties \
	-C classes gnu

$(lib_gnu_classpath_tools_gjdoc_la_CSS): %.lo: $(srcdir)/src/resources/%.css
	test -d htmldoclet || mkdir htmldoclet
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.css $<

$(lib_gnu_classpath_tools_gjdoc_la_DTDS): %.lo: $(srcdir)/src/resources/%.dtd
	test -d doctranslets/html/res || mkdir -p doctranslets/html/res
	test -d dtd/ent || mkdir -p dtd/ent
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.dtd $<

$(lib_gnu_classpath_tools_gjdoc_la_ENTS): %.lo: $(srcdir)/src/resources/%.ent
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.ent $<

$(lib_gnu_classpath_tools_gjdoc_la_HTML): %.lo: $(srcdir)/src/resources/%.html
	test -d html/res || mkdir -p html/res
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.html $<

$(lib_gnu_classpath_tools_gjdoc_la_JS): %.lo: $(srcdir)/src/resources/%.js
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.js $<

$(lib_gnu_classpath_tools_gjdoc_la_MODS): %.lo: $(srcdir)/src/resources/%.mod
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.mod $<

$(lib_gnu_classpath_tools_gjdoc_la_PNG): %.lo: $(srcdir)/src/resources/%.png
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.png $<

$(lib_gnu_classpath_tools_gjdoc_la_PROPERTIES): %.lo: $(srcdir)/src/resources/%.properties
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.properties $<

$(lib_gnu_classpath_tools_gjdoc_la_RNGS): %.lo: $(srcdir)/src/resources/%.rng
	test -d rng || mkdir rng
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.rng $<

$(lib_gnu_classpath_tools_gjdoc_la_TXTS): %.lo: $(srcdir)/src/resources/%.txt
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.txt $<

$(lib_gnu_classpath_tools_gjdoc_la_XHTML): %.lo: $(srcdir)/src/resources/%.xhtml
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.xhtml $<

$(lib_gnu_classpath_tools_gjdoc_la_XSLS): %.lo: $(srcdir)/src/resources/%.xsl
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.xsl $<

version.lo: src/resources/version.properties
	$(LTGCJCOMPILE) -c -o $@ --resource=$*.properties $<

classes htmldoclet doctranslets/html/res dtd/ent html/res rng:
	mkdir -p classes
	test -d htmldoclet || mkdir htmldoclet
	test -d doctranslets/html/res || mkdir -p doctranslets/html/res
	test -d dtd/ent || mkdir -p dtd/ent
	test -d html/res || mkdir -p html/res
	test -d rng || mkdir rng

## We don't use $(GCJFLAGS) in this rule, because it might contain '-O',
## and that doesn't work that great when generating bytecode.
##
## FIXME change this to be user-configurable, so '-g' can be disabled.

$(com_sun_javadoc_jar_CLASSES) $(com_sun_tools_doclets_Taglet_jar_CLASSES) $(gnu_classpath_tools_gjdoc_jar_CLASSES): $(lib_gnu_classpath_tools_gjdoc_la_GENSOURCES) 

$(com_sun_javadoc_jar_CLASSES) $(com_sun_tools_doclets_Taglet_jar_CLASSES) $(gnu_classpath_tools_gjdoc_jar_CLASSES): classes/%.class: $(srcdir)/src/%.java
	$(JAVAC) $(USE_JAVAC_FLAGS) -d classes $<

$(gnu_classpath_tools_gjdoc_jar_GENCLASSES): classes/%.class: %.java
	test -d classes/gnu/classpath/tools/gjdoc/expr || mkdir -p classes/gnu/classpath/tools/gjdoc/expr
	$(JAVAC) $(USE_JAVAC_FLAGS) -d classes $<

clean-local:
	for res in $(gnu_classpath_tools_gjdoc_jar_CSS) $(gnu_classpath_tools_gjdoc_jar_DTDS) \
	$(gnu_classpath_tools_gjdoc_jar_ENTS) $(gnu_classpath_tools_gjdoc_jar_MODS) \
	$(gnu_classpath_tools_gjdoc_jar_PROPERTIES) $(gnu_classpath_tools_gjdoc_jar_RNGS) \
	$(gnu_classpath_tools_gjdoc_jar_TXTS) $(gnu_classpath_tools_gjdoc_jar_XHTML) \
	$(gnu_classpath_tools_gjdoc_jar_XSLS) ; \
	do rm -f $$res; done
	rm -rf htmldoclet doctranslets classes rng dtd
	rm -f antlr.so java.lang-classes-1.{2,3,4,5}.d
	rm -f version.d

dist-hook:
	test -d $(distdir)/src/ || mkdir $(distdir)/src
	-cp -R $(srcdir)/src/resources $(distdir)/src
	-find $(distdir)/src/resources -name CVS -exec rm -rf {} \;

install-data-hook:
if !ENABLE_NATIVE
	$(INSTALL) --mode 755 gjdoc.sh $(DESTDIR)$(bindir)/gjdoc
endif

uninstall-hook:
if !ENABLE_NATIVE
	rm -f $(bindir)/gjdoc
endif

antlr.so: $(ANTLR_JAR)
	$(GCJ) -shared $(AM_GCJFLAGS) $(GCJFLAGS) -c -o $@ $<
