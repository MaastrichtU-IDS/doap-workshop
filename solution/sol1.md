```SPARQL
PREFIX doap: <http://usefulinc.com/ns/doap#>
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX bibo: <http://purl.org/ontology/bibo/>
select distinct * where { 
    ?project a doap:Project ;
        doap:name ?name ;
        doap:description ?description ;
        doap:programming-language ?programmingLanguage .
    OPTIONAL {
        ?project doap:repository [
            a doap:GitRepository ;
            doap:location ?gitUrl
          ] .
    }
    OPTIONAL {
        ?project doap:bug-database ?bugdatabase .
    }
    OPTIONAL {
        ?project doap:category ?category .
    }
    OPTIONAL {
        ?project bibo:status ?status .
    }
    OPTIONAL {
        ?project doap:created ?created .
    }
    OPTIONAL {
        ?project doap:download-page ?downloadpage .
    }
    OPTIONAL {
        ?project doap:homepage ?homepage .
    }
    OPTIONAL {
        ?project doap:license ?license .
    }
    OPTIONAL {
        ?project doap:shortdesc ?shortdesc .
    }
    FILTER (?programmingLanguage = "Python")
}
```

