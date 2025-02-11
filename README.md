# Parameter Usage Vocabulary Ontology
An ontology for defining parameters (observable-properties) corresponding to the [NVS Parameter Usage Vocabulary (P01)](https://vocab.nerc.ac.uk/collection/P01/current/). 

The 'semantic model' for parameters is described in the [P01 issue tracker](https://github.com/nvs-vocabs/P01/blob/master/README.md) and summarized in the following figure: 

![P01_wheel](image/P01_wheel.png)

The P01 'Semantic Model' defines the structure of a Parameter Name (seen as its `skos:prefLabel`), the RDF representation only shows generalized SKOS relationships to the component terms: 

For example, the parameter [`R0186569`](http://vocab.nerc.ac.uk/collection/P01/current/R0186569/) is currently described using the basic SKOS relations as follows:
```Turtle
<http://vocab.nerc.ac.uk/collection/P01/current/R0186569/> a skos:Concept ;
    skos:altLabel "DryWt_CAS57117-41-6_BE006569" ;
    skos:broader <http://vocab.nerc.ac.uk/collection/P02/current/BCOC/>,
        <http://vocab.nerc.ac.uk/collection/S06/current/S0600045/>,
        <http://vocab.nerc.ac.uk/collection/S25/current/BE006569/>,
        <http://vocab.nerc.ac.uk/collection/S26/current/MAT01963/>,
        <http://vocab.nerc.ac.uk/collection/S27/current/CS003687/> ;
    skos:definition "The amount (mass or number of moles) of the specified analyte per unit weight of the specified organism or part thereof after water has been removed."@en ;
    skos:prefLabel "Concentration of 1,2,3,7,8-pentachlorodibenzofuran {1,2,3,7,8-pentaCDF CAS 57117-41-6} per unit dry weight of biota {Mytilus galloprovincialis (ITIS: 79456: WoRMS 140481) [Subcomponent: flesh]}"@en ;
    skos:related <http://vocab.nerc.ac.uk/collection/P06/current/UUKG/>,
        <http://vocab.nerc.ac.uk/collection/S02/current/S041/> .
```

This [OWL implementation](rdf/puv-ont.ttl) implements explicit links to the dependency terms from the other vocabularies.  

![PUV-ont](image/puv-Parameter.png)

Using PUV-ont the relationships in the example above are explicit:

```turtle
<http://vocab.nerc.ac.uk/collection/P01/current/R0186569/> a skos:Concept , puv:Parameter ;
  skos:altLabel "DryWt_CAS57117-41-6_BE006569" ;
  skos:broader <http://vocab.nerc.ac.uk/collection/P02/current/BCOC/> ;
  skos:definition "The amount (mass or number of moles) of the specified analyte per unit weight of the specified organism or part thereof after water has been removed."@en ;
  skos:prefLabel "Concentration of 1,2,3,7,8-pentachlorodibenzofuran {1,2,3,7,8-pentaCDF CAS 57117-41-6} per unit dry weight of biota {Mytilus galloprovincialis (ITIS: 79456: WoRMS 140481) [Subcomponent: flesh]}"@en ;
  puv:biologicalObject <http://vocab.nerc.ac.uk/collection/S25/current/BE006569/> ;
  puv:chemicalObject <http://vocab.nerc.ac.uk/collection/S27/current/CS003687/> ;
  puv:matrix <http://vocab.nerc.ac.uk/collection/S26/current/MAT01963/> ;
  puv:matrixRelationship <http://vocab.nerc.ac.uk/collection/S02/current/S041/> ;
  puv:property <http://vocab.nerc.ac.uk/collection/S06/current/S0600045/> ;
  puv:uom <http://vocab.nerc.ac.uk/collection/P06/current/UUKG/> ;
.
```

The [Complex Property Model in OWL](https://github.com/adamml/opm-owl) has also addressed this issue. 
See our [comparison of PUV-ont with CPM ontology](puv-vs-cpm.md)
