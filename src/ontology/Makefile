# LOF-ODP-001: Legal Act and Legal Document: build, test, and release.
# Requires Java 11+ and make. ROBOT is downloaded on first use.
#   make test                   run all QC checks (LOF-P-011 and SPARQL checks)
#   make release VERSION=x.y.z  write the release files to the repo root

ID       := odp-001
NAME     := lof-odp-001
BASE     := https://w3id.org/lof
EDIT     := lof-odp-001-edit.owl
CATALOG  := catalog-v001.xml
LOF_DEPS := 
ROBOT_JAR := ../../bin/robot.jar
ROBOT    := java -jar $(ROBOT_JAR)
TMP      := tmp
VERSION  ?= 0.1.0

.PHONY: test reason verify report release clean
test: verify report

$(ROBOT_JAR):
	mkdir -p ../../bin && curl -sSL -o $@ https://github.com/ontodev/robot/releases/download/v1.9.7/robot.jar

$(TMP):
	mkdir -p $(TMP)

$(TMP)/merged.owl: $(EDIT) | $(ROBOT_JAR) $(TMP)
	$(ROBOT) merge --catalog $(CATALOG) --input $(EDIT) --output $@

# LOF-P-011: consistent, no unsatisfiable classes
$(TMP)/reasoned.owl: $(TMP)/merged.owl
	$(ROBOT) reason --reasoner HermiT --equivalent-classes-allowed asserted-only --input $< --output $@

reason: $(TMP)/reasoned.owl

# SPARQL checks on the reasoned ontology; any result fails the build
verify: $(TMP)/reasoned.owl
	$(ROBOT) verify --input $< --queries ../sparql/*-violation.sparql --output-dir $(TMP)

report: $(TMP)/merged.owl
	$(ROBOT) report --input $< --fail-on ERROR --output $(TMP)/report.tsv

# Base: this pattern's own axioms only. Full: merged with imports, reasoned.
release: test
	$(ROBOT) remove --input $(EDIT) --select imports --trim false \
	  annotate --ontology-iri $(BASE)/$(ID)/$(NAME)-base.owl \
	  --version-iri $(BASE)/$(ID)/releases/$(VERSION)/$(NAME)-base.owl \
	  --annotation owl:versionInfo $(VERSION) --output ../../$(NAME)-base.owl
	$(ROBOT) merge --catalog $(CATALOG) --input $(EDIT) \
	  reason --reasoner HermiT --equivalent-classes-allowed asserted-only \
	  annotate --ontology-iri $(BASE)/$(ID).owl \
	  --version-iri $(BASE)/$(ID)/releases/$(VERSION)/$(NAME).owl \
	  --annotation owl:versionInfo $(VERSION) --output ../../$(NAME).owl

clean:
	rm -rf $(TMP)
