# FAIR project descriptions: creating a description of a (Github) software project

This document is an instruction to the **DOAP** at the Institute of Data Science (**IDS**). It describes what they need to do in order to help make our IDS Dashboard an attractive website.

---

### Why did we adopt the Description of a Project (DOAP) ontology?

Ontologies are now widely used by people - and organizations - to describe their projects using Semantic Web standards. Yet, since files are spread around the Web, there is no easy and standardized way to find a project regarding its metadata. Back to 2015, a consensus for adopting a proper [Software Ontology](http://theswo.sourceforge.net/) was taken that describes and categorizes a software project based on a list of classifiers (or descriptors) by using as much standardized language as possible. To this end, we have decided to adopt and implement project descriptors and properties from the machine-readable ontology called DOAP.

Thus, the idea of IDS Dashboard is help users you find specific projects that meet their interests and to gain a broader understanding of the wide variety of work currently underway in the IDS. This way, users just need to publish some DOAP files on their websites to benefit of this distributed architecture.

### General DOAP Guidelines

This section of the website contains advice and guidelines for projects when creating or maintaining their DOAP files. While much of the information contained is general to all DOAP files, some is specific to the files maintained by IDS projects.

### What is DOAP (ontology)

**[DOAP](https://github.com/ewilderj/doap/wiki)** (an acronym of **Description of a Project**) is a machine-readable ontology describing projects, in particular free and open source software projects. DOAP is a descriptive vocabulary expressed using Resource Description Framework (RDF) and the Web Ontology Language (OWL). Computers may use these DOAP profiles to find, for instance, all projects that use python as programming language, or to list all projects from a developer that you know. This is accomplished by explicitly defining the project properties.



### How does a DOAP file look like?

The list of descriptors will be available through the web, and added to the project like so: 

```xml
@prefix doap: <http://usefulinc.com/ns/doap#> .
@prefix asf: <http://projects.apache.org/ns/asfext#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix bibo: <http://purl.org/ontology/bibo/> .

<https://w3id.org/umids/project/fairsharing-metrics>
  a doap:Project ;
  doap:name "Fairsharing Metrics" ;
  doap:description '''A Dockerization of the Fairsharing metrics as a module for Data Quality Analysis.''' ;
  bibo:status "Active" ;

  doap:programming-language "Python" ;
  doap:license <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;
  doap:homepage <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;
  doap:bug-database <https://github.com/MaastrichtU-IDS/fairsharing-metrics/issues> ;
    
  doap:category "Research" ;
  doap:repository [
    a doap:GitRepository ;
    doap:location <https://github.com/MaastrichtU-IDS/fairsharing-metrics> ;
  ] ;
  doap:maintainer [
    a foaf:Person ;
    foaf:name "Vincent Emonet" ;
    foaf:mbox <mailto:vincent.emonet@maastrichtuniversity.nl>
  ] .
```

It was decided that DOAP file would be populated via website. Nonetheless, we acknowledge that the descriptors needed are already available from sources such GitHub. Some of these data sources provides access to their data via API and will take into consideration to harvest this data via python script. Click here to know more about the [descriptors](docs/Descriptors DOAP.md).


### Create a DOAP description for your project

You can easily generate the DOAP description for your project on this [website](https://maastrichtu-ids.github.io/projects/create-doap).

---

###  👨‍💻 APPLY YOUR KNOWLEDGE  - Create a DOAP for your project. 

Please let us know which project will you choose for this tasks according with the following scenarios:

#### Scenario 1: Select from your personal Github/Gitlab repository

Click on [Create an issue](https://github.com/MaastrichtU-IDS/projects/issues) and add your project link.

#### Scenario 2: Select from IDS Github repository

Find [here](https://docs.google.com/spreadsheets/d/1gmpoXs7qEMGOx6IBJifsYNqPVeLjLzwAjTNmay7ymng/edit?usp=sharing) your name and the assigned project to create and upload the DOAP file.

---

#### Task 1: Fill in the DOAP form [3 min]

Go to this website and complete the https://maastrichtu-ids.github.io/projects/create-doap.

#### Task 2: Add more DOAP project properties [5 min]

Trade with your group, and discuss extra properties or descriptors you find appropriate to improve the fairness of a project (e.g. increase citeability of your software project by adding DOI properties). Add your ideas here.

#### Task 3: Git push-origin master [5 min]

Add your `doap-project.ttl` file in your project folder. If you have selected a IDS project from our repository (Scenario 2), send us the file and we will upload the `.ttl`file.

#### Task 4: Visualise the IDS Project directory and use SPARQL query

- Go to graphdb and select [ids-projects repository](https://graphdb.dumontierlab.com/) (top right) then,
- go to SPARQL (right tab) and add the followitng SPARQL:

```SPARQL
// GET ALL IDS PROJECTS FROM IDS DASHBOARD
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
}
```

**Question 1**: Can you please do filter the dataset to all projects that use Python programming language?

Query the ids-project with the following SPARQL:

```SPARQL
// COUNT THE IDS PROJECTS PER CATEGORY
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
select ?category (count(?project) as ?projectCount) where { 
    ?project a doap:Project ;
             doap:category ?category .
} GROUP BY ?category`
```

**Question 2**: Can you please do query and count the project statuses in ids-projects dataset?



#### Task 5: Give us your feedback!