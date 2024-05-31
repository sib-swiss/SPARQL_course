# GBA1 'Lysosomal acid glucosylceramidase'

## Learning outcomes

**After having completed this chapter, you will be able to:**

- Understand the structure of a simple '`biological`' database encoded in Turtle
- Write simple SELECT SPARQL queries


## Material

The exercises below follow the same structure as the [music exercises](/music/), with a focus on the GBA1 gene involved in the Gaucher disease.


## GBA1 graph exploration

Take some time to explore the GBA1 protein graph.

It has a lot of classes connecting the different knowledges curated and aggregated by the UniProt team.

[![Class hierarchy in the GBA1 graph](assets/images/GraphDB-class-hierarchy.png "Class hierarchy in the GBA1 graph")](/assets/images/GraphDB-class-hierarchy.png)

[![Class relationships in the GBA1 graph](assets/images/GraphDB-class-relationships.png "Class relationships in the GBA1 graph")](/assets/images/GraphDB-class-relationships.png)


## GBA1 graph SPARQL queries

We will do some exercises on a simplified version *GBA1-simple*.

In this version, most of the classes have been removed to keep what is centered around the reactions catalyzed by the enzyme GBA1.


### DESCRIBE a concept

As its name suggests, `DESCRIBE` provides a useful fragment of RDF, such as all the known details for each URI found.

```sparql title="Describe_up:catalyzedReaction.sparql"
# Describe the up:catalyzedReaction concept

PREFIX up: <http://purl.uniprot.org/core/>
DESCRIBE up:catalyzedReaction
```

**Exercise:**

+ Where is the `up:catalyzedReaction` concept found in the graph?
+ In which predicates is it involved?

??? done "Answer"
	```
	     subject                 predicate             object
	1    up:catalyzedReaction    rdf:type              rdf:Property
	2    up:catalyzedReaction    rdfs:subPropertyOf    up:catalyzedReaction
	3    up:catalyzedReaction    rdfs:subPropertyOf    up:catalyzedReaction
	```


### What is the GBA1 protein name?

The *predicate* qualifying the protein name is `up:fullName`.

**Exercise:** Use this predicate to find the GBA1 protein (full) name.

??? done "Answer"
	```sparql title="Protein_name.sparql"
	# Retrieve the protein name associated with the P04062 UniProt entry
	
	PREFIX up: <http://purl.uniprot.org/core/>
	SELECT ?protein_name WHERE {
		?s up:fullName ?protein_name .
	}
	```
	```
	####################################################################
	
	      protein_name
	1    "Lysosomal acid glucosylceramidase"
	```


### What does this enzyme catalyze?

**Exercise:** Using the `up:catalyzedReaction` predicate, get the reactions catalyzed by this enzyme.

??? done "Answer"
	```sparql title="This_enz_catalyses.sparql"
	# What does this enzyme catalyse?
	
	PREFIX up: <http://purl.uniprot.org/core/>
	SELECT ?reactions WHERE {
		?s up:catalyzedReaction ?reactions .
	}
    ```
    ```
	##########################################
	
	      reactions
	1     http://rdf.rhea-db.org/13269
	2     http://rdf.rhea-db.org/14297
	3     http://rdf.rhea-db.org/11956
	4     http://rdf.rhea-db.org/58264
	5     http://rdf.rhea-db.org/58324
	6     http://rdf.rhea-db.org/58316
	7     http://rdf.rhea-db.org/70303
	8     http://rdf.rhea-db.org/70307
	9     http://rdf.rhea-db.org/70311
	10    http://rdf.rhea-db.org/70315
	11    http://rdf.rhea-db.org/70235
	12    http://rdf.rhea-db.org/70255
	13    http://rdf.rhea-db.org/70239
	14    http://rdf.rhea-db.org/70251
    ```


**Exercise:** Order this list by descending Rhea ids

??? done "Answer"
	```sparql
	# What does this enzyme catalyse?
	
	PREFIX up: <http://purl.uniprot.org/core/>
	SELECT ?reactions WHERE {
		?s up:catalyzedReaction ?reactions .
	}
	ORDER BY DESC(?reactions)
    ```
    ```
	##########################################
	
	      reactions
	1     http://rdf.rhea-db.org/70315
	2     http://rdf.rhea-db.org/70311
	3     http://rdf.rhea-db.org/70307
	4     http://rdf.rhea-db.org/70303
	5     http://rdf.rhea-db.org/70255
	6     http://rdf.rhea-db.org/70251
	7     http://rdf.rhea-db.org/70239
	8     http://rdf.rhea-db.org/70235
	9     http://rdf.rhea-db.org/58324
	10    http://rdf.rhea-db.org/58316
	11    http://rdf.rhea-db.org/58264
	12    http://rdf.rhea-db.org/14297
	13    http://rdf.rhea-db.org/13269
	14    http://rdf.rhea-db.org/11956
    ```


### What are Rhea reactions associated with an EC number?

All GBA1 catalyzed reactions are reactions in [Rhea](https://www.rhea-db.org/).

The GBA1 graph contains also enzyme classes (`up:enzymeClass` predicate).

**Exercise:** Get the GBA1 Rhea reactions associated with an EC number

??? done "Answer"
    ```sparql
	# What are Rhea reactions associated with an EC number?
	
	PREFIX up: <http://purl.uniprot.org/core/>
	SELECT ?rhea ?EC WHERE {
		?CatalyticActivity  up:catalyzedReaction   ?rhea .
		?CatalyticActivity  up:enzymeClass         ?EC .
	}
	```
    ```
    ##########################################
	
	     rhea                            EC
	1    http://rdf.rhea-db.org/13269    enzyme:3.2.1.45
	2    http://rdf.rhea-db.org/14297    enzyme:3.2.1.46
	```


The two triples use the same subject: `?CatalyticActivity`.

The query can be simplified with the **;** punctuation sign.

**Exercise:** Simplify the previous query with **;**

??? done "Answer"
    ```sparql title=""
	# What are Rhea reactions associated with an EC number?
	
	PREFIX up: <http://purl.uniprot.org/core/>
	SELECT ?rhea ?EC WHERE {
		?CatalyticActivity  up:catalyzedReaction   ?rhea ;
		                    up:enzymeClass         ?EC .
	}
    ```
    ```
	##########################################
	
	     rhea                            EC
	1    http://rdf.rhea-db.org/13269    enzyme:3.2.1.45
	2    http://rdf.rhea-db.org/14297    enzyme:3.2.1.46
    ```


### What are Rhea reactions associated with an EC number, and those which are not?

We have seen previously that GBA1 catalyzes 14 reactions. All of them are linked to Rhea, but not all of them are linked to an EC number.

**Exercise:** Get the GBA1 Rhea reactions associated with an EC number, if any

??? done "Answer"
    ```sparql
	# What ...
	
	```
	```
	##########################################
	
	     rhea                            EC
	1    
	```


### TODO

