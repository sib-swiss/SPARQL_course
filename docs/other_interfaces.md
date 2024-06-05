# Other SPARQL interfaces

Here is a list of SPARQL endpoints - integrated in the ReconXKG RDF - that can be useful to query individually.

Note that they may rely on different RDF engines (i.e. GraphDB is not used everywhere).

The [Virtuoso](https://github.com/openlink/virtuoso-opensource/) engine is often used because it can manage larger amount of data, and is also freely available.


## UniProt

The UniProt SPARQL endpoint is available at [https://sparql.uniprot.org/](https://sparql.uniprot.org/)

[![UniProt SPARQL endpoint](assets/images/UniProt-endpoint.png "UniProt SPARQL endpoint")](https://sparql.uniprot.org/)


## Rhea

The Rhea SPARQL endpoint is available at [https://sparql.rhea-db.org/](https://sparql.rhea-db.org/)

[![Rhea SPARQL endpoint](assets/images/Rhea-endpoint.png "Rhea SPARQL endpoint")](https://sparql.rhea-db.org/)


## MetaNetX

The MetaNetX SPARQL endpoint is available at [https://rdf.metanetx.org/](https://rdf.metanetx.org/)

[![MetaNetX SPARQL endpoint](assets/images/MetaNetX-endpoint.png "MetaNetX SPARQL endpoint")](https://rdf.metanetx.org/)


## Remote queries with SERVICE

One of the strength of SPARQL queries is they can be remotely executed, opening the *federated query* way of querying.

**Exercise:** Take an example query found in Rhea or MetaNetX, and execute it from the [reconx.vital-it.ch](https://reconx.vital-it.ch) SPARQL interface.

E.g.:
```sparql
PREFIX rh: <http://rdf.rhea-db.org/>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX pubmed: <http://rdf.ncbi.nlm.nih.gov/pubmed/>
# Query 2
# Select all Rhea reactions annotated with a given Pubmed identifier (PMID = 29867142)
#
SELECT ?pubmed ?rhea ?accession ?isTransport ?equation
WHERE {
	?rhea rdfs:subClassOf rh:Reaction .
	?rhea rh:accession ?accession .
	?rhea rh:citation ?pubmed .
	VALUES (?pubmed) { (pubmed:29867142) }
	?rhea rh:isTransport ?isTransport .
	?rhea rh:equation ?equation .
} ORDER BY ?rhea
```

*NB*: The Rhea SPARQL endpoint URL is `https://sparql.rhea-db.org/`.

??? done "Answer"
    ```sparql
	PREFIX rh: <http://rdf.rhea-db.org/>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX pubmed: <http://rdf.ncbi.nlm.nih.gov/pubmed/>
	# Query 2
	# Select all Rhea reactions annotated with a given Pubmed identifier (PMID = 29867142)
	#
	SELECT ?pubmed ?rhea ?accession ?isTransport ?equation
	WHERE {
		SERVICE <https://sparql.rhea-db.org/> {                  # <--------------------
			?rhea rdfs:subClassOf rh:Reaction .
			?rhea rh:accession ?accession .
			?rhea rh:citation ?pubmed .
			VALUES (?pubmed) { (pubmed:29867142) }
			?rhea rh:isTransport ?isTransport .
			?rhea rh:equation ?equation .
		}                                                        # <--------------------
	} ORDER BY ?rhea
    ```

