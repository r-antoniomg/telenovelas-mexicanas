# Telenovelas mexicanas \[Sample project\]  
**NOTE**: For sample projects in this GitHub account, the objective is not to have a fully-formed research question, valid sample, and methodology. The main objective is to showcase my learning about different tools used for digital scholarship.  

This project was intended to explore tools for obtaining data and doing network analysis.
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
## Network analysis: image examples
Image 01. Visual representation of relationships between telenovelas and their cast members :
![Telenovelas mexicanas: network analysis detail](https://user-images.githubusercontent.com/102780927/161389993-27da594f-9257-45f8-9c48-55a49ff512f9.png)

Image 02. Relationship visual focus on title :
![Telenovelas mexicanas: network analysis by title](https://user-images.githubusercontent.com/102780927/161389994-a86f10f6-fc13-44d6-aa84-daa920ebf30d.png)

Image 03. Relationship visual focus on cast member :
![Telenovelas mexicanas: network analysis by cast member](https://user-images.githubusercontent.com/102780927/161389995-eed10e5f-6645-491a-8cc8-e96d6f118a65.png)
