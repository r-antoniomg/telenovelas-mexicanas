# Telenovelas mexicanas  
This project was intended to explore tools for obtaining data and doing network analysis.

As with all projects in this GitHub account, the objective is not to have a fully-formed research question, valid sample, and methodology. My main objective in these projects is to learn about different tools used for digital scholarship.  
## Tools  
### SPARQL  
A SPARQL query was used against DBpedia's [SNORQL query explorer](https://dbpedia.org/snorql/) to find the titles of Mexican telenovelas and names of cast members. Unique identifiers for each entity were also obtained to facilitate the network analysis.

Query :  
```
SELECT ?titleID ?title ?nameID ?name
WHERE {
?s dbo:genre :Telenovela ;
   dbo:country :Mexico ;
   dbo:wikiPageID ?titleID ;
   rdfs:label ?title .
?s dbo:starring ?cast .
?cast dbo:wikiPageID ?nameID ;
      rdfs:label ?name .
FILTER ( langMatches(lang(?title),"es" ))
FILTER ( langMatches(lang(?name),"es" ))
}
```
### Gephi
I used [Gephi](https://gephi.org/), along with a [tutorial by Martin Grandjean](http://www.martingrandjean.ch/gephi-introduction/) to do some basic network analysis.
## Data
Titles of Mexican telenovelas and cast members obtained from DBpedia.  
### Files  
- 2022-04-02-telenovelas.csv : 'Raw' data obtained from SPARQL query in DBpedia
- 2022-04-02-telenovelas-nodes.csv : Cleaned-up data identifying unique values for titles of telenovelas and names of cast members
- 2022-04-02-telenovelas-edges.csv : Cleaned-up data identifying the relationship between telenovelas and cast members
- 2022-04-02-telenovelas.gephi : Gephi file with loaded data  
## Image samples
