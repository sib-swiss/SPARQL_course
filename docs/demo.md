# GraphDB demo

## Learning outcomes

**After this demo, you will be able to:**

- Navigate through GraphDB and use its basic features

## Material

The exercises below are based on [this tutorial](https://docs.stardog.com/getting-started-series/getting-started-4) and [data](https://github.com/stardog-union/stardog-tutorials/tree/master/music) from [Stardog](https://docs.stardog.com/) (another semantic graph database).

Let's look at a small example of the music database:

```ttl title="beatles_notsimplified.ttl"
PREFIX : <http://contextualise.dev/ontology/>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

:The_Beatles      rdf:type  :Band .
:The_Beatles      :name     "The Beatles" .
:The_Beatles      :member   :John_Lennon .
:The_Beatles      :member   :Paul_McCartney .
:The_Beatles      :member   :Ringo_Starr .
:The_Beatles      :member   :George_Harrison .
:John_Lennon      rdf:type  :SoloArtist .
:Paul_McCartney   rdf:type  :SoloArtist .
:Ringo_Starr      rdf:type  :SoloArtist .
:George_Harrison  rdf:type  :SoloArtist .
:Please_Please_Me rdf:type  :Album .
:Please_Please_Me :name     "Please Please Me" .
:Please_Please_Me :date     "1963-03-22"^^xsd:date .
:Please_Please_Me :artist   :The_Beatles .
:Please_Please_Me :track    :Love_Me_Do .
:Love_Me_Do       rdf:type  :Song .
:Love_Me_Do       :name     "Love Me Do" .
:Love_Me_Do       :length   125 .
:Love_Me_Do       :writer   :John_Lennon .
:Love_Me_Do       :writer   :Paul_McCartney .
```

Let's look at its structure when connecting the entities:

<figure>
  <img src="../../assets/images/rdf-beatles.png" width="700"/>
</figure>

Now let's use a bigger music database that uses the same structure (it's from DBpedia):

Download the ttl file [`music.ttl`](Music/music.ttl)

It is already loaded on the ReconXKG server (https://reconx.vital-it.ch), but you can also install it on your local instance if you wish.

Now let's browse through it on this website!
