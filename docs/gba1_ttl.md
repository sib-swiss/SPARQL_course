# GBA1 'Lysosomal acid glucosylceramidase' Turtle

## Learning outcomes

**After having completed this chapter, you will be able to:**

- Get a *Turtle* file from a UniProt entry
- Import a *Turtle* file in GraphDB


## Material

The exercises below follow the same structure as the [music example](/music/), with a focus on the GBA1 gene involved in the Gaucher disease.

Let's look at the [GBA1](https://www.uniprot.org/uniprotkb/P04062) entry in [UniProt](https://www.uniprot.org/):

[![GBA1 in UniProt](assets/images/GBA1_in_UniProt.png "GBA1 in UniProt")](/assets/images/GBA1_in_UniProt.png)

Some variants of this protein caused the [Gaucher disease](https://en.wikipedia.org/wiki/Gaucher%27s_disease).

[![GBA1 Disease & Variants in UniProt](assets/images/Gaucher_disease.png "GBA1 Disease & Variants in UniProt")](/assets/images/Gaucher_disease.png)


## Export a ttl (Turtle) file from UniProt

A Turtle file can be exported directly from a UniProt entry page.

[![UniProt entry URL](assets/images/P04062_url.png "UniProt entry URL")](/assets/images/P04062_url.png)

[![Export in FASTA](assets/images/P04062.fasta.png "Export in FASTA")](/assets/images/P04062.fasta.png)

[![FASTA export](assets/images/P04062.fasta2.png "FASTA export")](/assets/images/P04062.fasta2.png)

[![Export in Turtle](assets/images/P04062.ttl.png "Export in Turtle")](/assets/images/P04062.ttl.png)


## Import a ttl file in GraphDB

### Create a new repository

Go to the GraphDB main screen

[![GraphDB main screen](assets/images/GraphDB_main-screen.png "GraphDB main screen")](assets/images/GraphDB_main-screen.png)

Create a new repository to work in

[![GraphDB repository setup](assets/images/GraphDB_repository-setup.png "GraphDB repository setup")](assets/images/GraphDB_repository-setup.png)

[![GraphDB new repository](assets/images/GraphDB_new-repository.png "GraphDB new repository")](assets/images/GraphDB_new-repository.png)

[![Choose GraphDB repository](assets/images/GraphDB_choose-GraphDB-repository.png "Choose GraphDB repository")](assets/images/GraphDB_choose-GraphDB-repository.png)

[![Choose a repository ID](assets/images/GraphDB_choose-repository-ID.png "Choose a repository ID")](assets/images/GraphDB_choose-repository-ID.png)

[![Activate the new repository](assets/images/GraphDB_activate-new-repository.png "Activate the new repository")](assets/images/GraphDB_activate-new-repository.png)

[![New repository activated](assets/images/GraphDB_new-repository-activated.png "New repository activated")](assets/images/GraphDB_new-repository-activated.png)

[![New repository running](assets/images/GraphDB_new-repository-running.png "New repository running")](assets/images/GraphDB_new-repository-running.png)


### Import a ttl file

A Turtle file can be easily imported in GraphDB

[![Want to import data](assets/images/GraphDB_want-to-import.png "Want to import data")](assets/images/GraphDB_want-to-import.png)

Select **Upload RDF files**, and upload your Turtle file(s)

[![Select RDF to import](assets/images/GraphDB_Select-RDF-to-import.png "Select RDF to import")](assets/images/GraphDB_Select-RDF-to-import.png)

[![Ready to import](assets/images/GraphDB_ready-to-import.png "Ready to import")](assets/images/GraphDB_ready-to-import.png)

[![Imported successfully](assets/images/GraphDB_imported-successfully.png "Imported successfully")](assets/images/GraphDB_imported-successfully.png)

The GraphDB main page shows statistics about the data in your repository

[![Repository statistics](assets/images/GraphDB_repository-statistics.png "Repository statistics")](assets/images/GraphDB_repository-statistics.png)


[Next](/gba1/) Queries on the GBA1 graph

