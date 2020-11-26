# FAIR project descriptions: creating a description of a (Github) software project

<img src="assets/ids_logo.png" style="zoom:73%;" />





## Material

* [Slides](https://docs.google.com/presentation/d/17nynZvuTGUGH1-bhOFik7SgjMrv06gQExst0HpYkUOc/edit?usp=sharing) 👨‍💻[20 min]
* [IDS Dashboard motivation](https://maastrichtu-ids.github.io/best-practices/docs/create-doap) 🔎[5 min read]
* [IDS Dashboard website](https://maastrichtu-ids.github.io/projects/) 🔭
* [post-workshop feedback](https://cutrillaguerrero.typeform.com/report/GJ7o2jYd/eLuERbsrIg8b3MJX) 🍎 

## Introduction: lack of semantic interoperability 

The lack of well-defined indexing practices is a common problem in most institutional repositories. Researchers will typically assign keywords to their projects, however, these terms are not extracted from a controlled vocabulary or thesaurus. This leads to ambiguity and lack of standardization in terms which are used to describe the content of their projects. As solution to the problem, IDS has undertaken the effort to design a search engine that provides a single entry to our research projects. The result is the [IDS Dashboard](https://maastrichtu-ids.github.io/best-practices/docs/create-doap), particularly aimed at making our software findable, accessible, interoperable and reusable (FAIR), an essential component to reducing barriers for access. In addition to facilitating access to projects, IDS Dashboard reconciles and indexes projects using metadata descriptors that come directly from the Github repository using a machine-readable ontology.

This workshop introduces the ontology used to describe a project, the Description of a Project ([DOAP](https://github.com/ewilderj/doap/wiki)). Once the project descriptors are assigned to the existing projects, it is feasible to use the DOAP ontology to expand queries and to assist end-users in the selection of search terms.

You will know the answers to questions like:

- what is DOAP? 
- Why is this important? 
- How do you create a DOAP for your project? 
- How do you query project descriptors using GraphDB?

## What is DOAP (ontology)?

**[DOAP](https://github.com/ewilderj/doap/wiki)** (an acronym of **Description of a Project**) is a machine-readable ontology describing projects, in particular free and open source software projects. DOAP is a descriptive vocabulary expressed using Resource Description Framework (RDF) and the Web Ontology Language (OWL). Computers may use these DOAP profiles to find, for instance, all projects that use python as programming language, or to list all projects from a developer that you know. This is accomplished by explicitly defining the project properties.

## Why did we adopt the Description of a Project (DOAP) ontology?

Ontologies are now widely used by people - and organizations - to describe their projects using Semantic Web standards. Yet, since files are spread around the Web, there is no easy and standardized way to find a project regarding its metadata. Back to 2015, a consensus for adopting a proper [Software Ontology](http://theswo.sourceforge.net/) was taken that describes and categorizes a software project based on a list of classifiers (or descriptors) by using as much standardized language as possible. To this end, we have decided to adopt and implement project descriptors and properties from the machine-readable ontology called DOAP.

Thus, the idea of IDS Dashboard is help users to find specific projects that meet their interests and to gain a broader understanding of the wide variety of work currently underway in the IDS. This way, users just need to publish some DOAP files on their websites to benefit of this distributed architecture.

## How does a DOAP file look like?

The list of descriptors will be available through the web, and added to the project like so: 

```xml
@prefix doap: <http://usefulinc.com/ns/doap#> .
@prefix asf: <http://projects.apache.org/ns/asfext#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix bibo: <http://purl.org/ontology/bibo/> .

<https://w3id.org/umids/project/fairsharing-metrics>
  a doap:Project ;
  doap:name "Fairsharing Metrics" ;
  doap:description "A Dockerization of the Fairsharing metrics as a module for Data Quality Analysis." ;
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

>  Note: We acknowledge that the descriptors needed for the metadata are already available from public sources such [GH Archive](https://www.gharchive.org/). This primary source provides access to their data via API and will take into consideration to harvest this data via python script.

Check this [example](docs/DescriptorsDOAP.md) for understanding the descriptors [5 min].

---

##  👨‍💻 APPLY YOUR KNOWLEDGE [20 min]

Please let us know which project will you select for this activity. As previously mentioned, you can select an IDS project from the iDS-Maastricht or your personal account. The following scenarios shall clarify the next steps:

**Scenario 1: Select from your personal Github/Gitlab repository**

Add [here](https://docs.google.com/document/d/1XwIatooUNE6poEvmtq-DQNhKLmriaXvcS79GzteaGAg/edit?usp=sharing) your Github/Gitlab user and project name (e.g. `user-name/project-name`).

**Scenario 2: Select from IDS Github repository**

Find [here](https://docs.google.com/spreadsheets/d/1gmpoXs7qEMGOx6IBJifsYNqPVeLjLzwAjTNmay7ymng/edit?usp=sharing) your name and the assigned IDS project to create and upload the DOAP file.

---

### Task 1: Fill in the DOAP form [3 min]

Go to IDS Dashboard and complete the [form](https://maastrichtu-ids.github.io/projects/create-doap).

---

### Task 2: Add more DOAP project properties [5 min]

Trade with your group, and discuss extra properties or descriptors you find appropriate to improve the FAIRness of a project. 

 Add your ideas (minimum 2 per group) 💡 [here](https://docs.google.com/document/d/1D3v4r89pKnx8mIp3rvby_2VO_NooJEckIO2vI1K1dfE/edit?usp=sharing).

> 💡 e.g. [...] increase citability and reproducibility of your software project by adding PID (persistent identifier) for  the research assets. Another one is to add the ORCID of the project owner.

---

### Task 3: Git push-origin master [5 min]

Add your 📥  `doap-project.ttl` file in your project folder. If you have selected an IDS project from our repository (Scenario 2), [send us](mailito:c.utrillaguerrero@maastrichtuniversity.nl) an email with the file and we will upload the `.ttl`file.

>  ⚠️ ***Your project will automatically be added to the website tomorrow*** ⚠️

---

### Task 4: Visualise the IDS Project directory and use SPARQL query [5 min]

- **Step 1**: Go to graphdb and select [ids-projects repository](https://graphdb.dumontierlab.com/) (top right) then,
- **Step 2**: Go to SPARQL (right tab) and add the following SPARQL:

```SPARQL
# GET ALL IDS PROJECTS FROM IDS DASHBOARD
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

**Question 1** 🏆: **<u>Can you please create a SPARQL query that filters all IDS projects (ids-projects dataset) with '*Python*' as a programming language?</u>**

[Solution ✔️](solution/sol1.md)

* **Step 3**: Add another query to ids-project with the following SPARQL:

```SPARQL
# COUNT THE IDS PROJECTS PER CATEGORY
PREFIX foaf: <http://xmlns.com/foaf/0.1/>
select ?category (count(?project) as ?projectCount) where { 
    ?project a doap:Project ;
             doap:category ?category .
} GROUP BY ?category`
```

**Question 2** 🏆: **<u>Can you please create a SPARQL query that counts the project statuses in the ids-projects dataset?</u>**

[Solution ✔️](solution/sol2)

### Task 5: Give us your [feedback](https://cutrillaguerrero.typeform.com/to/GJ7o2jYd)! 🟥🟩 (30 sec)