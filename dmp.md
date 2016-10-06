---
layout: default
---

### Data management plan for the PROIEL Treebank

This document describes the procedures for data management for the [PROIEL Treebank](http://proiel.github.io). The procedures are based on the Digital Curation Centre's [Checklist for a Data Management Plan v4.0](http://www.dcc.ac.uk/resources/data-management-plans/checklist).

#### Data Collection

The treebank is constructed using the [PROIEL Annotator](https://github.com/mlj/proiel-webapp/), which uses a database for storage. This database is intended only for use during annotation and is not suitable for long-term storage of the data.

At regular intervals the data must be exported from the database using the PROIEL Annotator's [built-in export functionality](https://github.com/mlj/proiel-webapp/wiki/Importing-and-exporting-texts). This produces multiple XML files using the [PROIEL XML schema](http://proiel.github.io/handbook/developer/proielxml.html). These XML files are the authoritative, long-term representation of the treebank.

The XML files are added to [a git repository](https://github.com/proiel/proiel-treebank/) for versioning. Before committing new versions to the git repository, the diff must be inspected manually to reduce the chance of systematic errors or faulty exports entering the repository.

When linguistically relevant milestones are reached, e.g. on completion of a particular text, the head of the master branch should be tagged with a version number. The version number is the date of the release on the format YYYYMMDD.

For each tagged version, [a release](https://github.com/proiel/proiel-treebank/releases) should be prepared. The release should be prepared as a zip-file and a gzipped tarball.

The release should have a flat file layout (no directories) with one file per linguistically relevant unit in the treebank (such as one file per text). The release should include a copy of the XML schema and [an up-to-date README file](https://raw.githubusercontent.com/proiel/proiel-treebank/master/README.md) that lists the contents of the release, includes a copy of the license, links to online documentation, the original source and a source for updates, and provides instructions on how to reference the treebank in publications.

Additional files with derived data may be included in a release if there is demand for it. It must be made explcitly clear in the README file that these files are derived files, and their method of derivation must be stated and replicable.

#### Documentation and Metadata

The PROIEL XML schema includes several optional metadata elements. These elements must be updated for each release. At a minimum the elements that identify the original text's author (if known) and title, the electronic text's provenance and license, and the annotator's identities must be included.

The PROIEL annotation guidelines and PROIEL XML documentation are living documents that are expected to evolve over time. Previous versions must therefore remain available for cross-referencing.

#### Ethics and Legal Compliance

As part of the onboarding process, all contributors to the treebank must explicitly accept that their contributions will be distributed as part of the treebank under a [CC BY-NC-SA 4.0 license](https://creativecommons.org/licenses/by-nc-sa/4.0/) and that that their individual contributions may be identified in released XML files and in any online application that provides access to the data set (e.g. the PROIEL Reader).

Contributors' personal information, apart from their name and treebank-internal unique identifier, must not be disclosed without explicit consent.

#### Storage and Backup

The live database for ongoing annotation is hosted by [Tekstlaboratoriet at the University of Oslo](http://www.tekstlab.uio.no/) using the University's managed storage and backup infrastructure.

Released versions of the treebank are deposited on a CLARINO node. Two redundant copies are kept: one is kept by the release manager in an off-site location and one copy is stored by the git repository provider.

The current git repository provider is GitHub, which is based in the United States. As the git repository and releases do not contain sensitive data and are covered by a permissive open-source license, there are no known obstacles to using a provider in this jurisdiction.

#### Selection and Preservation

The final product is the treebank with all layers of annotation. The development history of the treebank up to the point of review is not part of the final product and can be discarded when the treebank is released. In contrast, the development history of the treebank after its initial release should be preserved and made available alongside the treebank data itself.

Experimentation with different types of annotation inevitably results in data that cannot be represented in released XML files as these XML files need to be made available on a stable, well-understood format. Once experimental annotation matures necessary extensions to the XML format should be considered. If this is not possible, separate data dumps should be preserved, e.g. CSV files or JSON files.

#### Data Sharing

Access to the raw data is obtained by downloading a release of the treebank from CLARIN or the treebank website. Access to derived data is also possible through [Universal Dependencies](http://universaldependencies.org/).

Access to indexed data can be obtained through the [PROIEL Reader](http://proiel.johndal.com) or [INESS](http://clarino.uib.no/iness/treebanks). INESS is intended for sophisticated users who need to run complex queries while PROIEL Reader caters to users who primarily browse the treebank and run simple queries.

There should be no barriers to access (e.g. user registration or manual approval) beyond acceptance of the relevant Creative Commons license.

Persistent identifiers for each release are provided by CLARIN.

#### Responsibilities and Resources

DH is responsible for the overall quality of the linguistic data. HE is responsible for maintaining metadata. MJ is responsible for release production and control.

Storage and backup is delegated to the administrator's of the University's infrastructure, to the involved CLARINO nodes and to GitHub.
