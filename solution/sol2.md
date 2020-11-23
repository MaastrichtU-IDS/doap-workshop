```SPARQL
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
PREFIX bibo: <http://purl.org/ontology/bibo/>
PREFIX doap: <http://usefulinc.com/ns/doap#>
select ?status (count(?project) as ?projectCount) where { 
    ?project a doap:Project ;
             bibo:status ?status .
} GROUP BY ?status
```

