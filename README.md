# ls563-linked-data-project
This is my LS 563 Linked Data project.
## Dataset Description
This is a dataset that was published on Kaggle.com by Michael Cai that contains data for the most popular fantasy books on Goodreads. It includes the book title, author, publication year, average rating of the book by Goodreads users, total number of ratings, number of times the book has been shelved, the series name that the book belongs to (if applicable), and what number the book is within the series. The data shows the fantasy books that were most read and highly rated by users at the time of dataset publication, which was about three years ago. The dataset was already cleaned before being published to Kaggle, so the cleaning and reconciling part of the project was very straightforward for me, and the majority of it was linking the authors to URIs through VIAF and book series' to Wikidata. 
## Ontologies and Controlled Vocabularies Used
I used BIBFRAME and Schema.org ontologies to describe the data. They contained the right kinds of vocabulary that I was looking for to describe the entities and properties within the book data. As aforementioned, I linked authors to their VIAF page during the reconciliation part of the project (using OpenRefine), and I connected Wikidata to the book series contained in the data. 
## Linking Strategy
Only the author and book series properties were linked to URIs (VIAF and Wikidata). The other properties were kept as literals since they were integer values. The book titles were also represented as literal values to include the text string the names of the books. I chose to link to VIAF because it is a large database for authors and their works. When I reconciled the book series to Wikidata, I ran into a couple of series that were not found when reconciled. However, as I searched Wikidata for those particular series--or individual books within the series--I came across alternative names for the series that I then inputted into OpenRefine and which were then able to be linked to Wikidata. 
## Sample Triples
rdf:type                     schema:Book;
        bf:agent                     viaf:95218067;
        bf:date                      "1954"^^xsd:gYear;
        bf:hasSeries                 wd:Q15228;
        bf:seriesEnumeration         "2"^^xsd:integer;
        bf:title                     "The Two Towers"@en;
        schema:aggregateRating       [ rdf:type            schema:AggregateRating;
                                       schema:ratingCount  "847263"^^xsd:integer;
                                       schema:ratingValue  "4.47"^^xsd:integer
                                     ];
        schema:interactionStatistic  "33274"^^xsd:integer .
wd:Q15228  rdf:type  schema:BookSeries .
