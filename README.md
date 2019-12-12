
<!-- README.md is generated from README.Rmd. Please edit that file -->
plantR
======

Management of Plant Occurrence Records.

Description
-----------

The package plantR provides tools for retrieving, processing, cleaning and validating occurrence records of plant species from biological collections.

Installation
------------

You can install the released version of plantR from [CRAN](https://CRAN.R-project.org) with:

``` r
install.packages("plantR")
library(plantR)
```

Details
-------

Managing the information linked to species records from herbarium collections is an important but often difficult task. The notation often differ between collections and even within collections because collection authors often provide information in different formats. In addition, it is often difficult to validate the geographical locality and taxonomy of individual records, especially when working with thousands of records. Thus, having tools to perform the (fast) processing and validation of herbarium records can be quite handy for collection curators, taxonomists, ecologists and conservationists.

The package plantR was developed to deal with data from herbarium collections, providing tools to perform:

-   the download of herbarium data for a list of species names or collections codes;
-   the batch processing of typical herbarium fields (e.g. collector name);
-   thw geographical and taxonomic validation of herbarium records.

Currently, the download of records is available for speciesLink (website) and GBIF (website), but the user can also provide its own dataset as an input. Field editing covers most of the typical variation in the notation of author and determiner names, trying to provide standardized ouputs in the TDWG format. Currently, geographical validation can be performed at county-level for Latin American countries and at country level for the rest of the world. We provide a gazetteer to retrieve and check geographical coordinates, which is currenlty biased towards Latin American countries, particularly for Brazil. Taxonomical validation is performed based on a compilation of plant taxonomist names from all over the world.

Basic assumptions of the data validation
----------------------------------------

In case of invalid or missing coordinates, we assume that the country, state, county (and locality) given in the specimen label are correct (i.e. locality prevails over coordinates), and so the working coordinates are taken from a gazetteer instead.

We ignore records with coordinates given only at county level, assuming that our gazetteer is a more complete and/or safe source of county coordinates (this may not be the case for sites outside Latin America). It is also important to note that if the occurrence information on the localities are indeed mistaken (eg. wrong/missing county name), than the locality won\`t be found in the gazetteer and thus, even if the original coordinates are good, they may be replaced by other coordinates taken from the gazetteer.

During taxonomic validation, we did not attempt to set priorities for different specialists within a given family. That is, all the specimens determined by the specialist within his/her family family of expertise were taken as being validated. Although we recognize that there are specialists from one or few genera within a family, the current validation process is only carried at family level.

In the case of conflicting determination among specialists for duplicates across different collections, we simply assume the most recent determination as being the most up-to-date one. Note that if the year of determination is missing from one or more duplicate labels, the corresponding determinations are not taken into account while trying to assign the most up-to-date determination for a group of duplicates.

Authors
-------

References
----------

See Also
--------

Funding
-------

The development of this package was possible under ...

Acknowledgements
----------------

The construction of the some functions and dictionaries provided by ...