# Data for PPI4SD

PPI4SD uses secondary data on development indicators, extracted from various sources.

### Splitting SDG 16
It should be noted that we have split SDG 16 in order to differentiate the topics of *peace and justice* and *strong institutions*. Thus, in this project, SDG 16a contains indicators of *peace and justice*, while SDG 16b covers *strong institutions*. This differentiation is important in the Mexican context, there governance issues may represent challenges that are not necessarily directly related to *peace and justice*.

## Development-Indicator Data
National level data consist of development indicators for the entire country of Mexico, and they have been obtained from the following sources:

* [United Nations Global SDG Database](https://unstats.un.org/sdgs/indicators/database/) (UN)
* [World Bank Sustainable Development Goals Database](http://datatopics.worldbank.org/sdgs/) (WDI)
* [World Bank Poverty and Equity Indicators](http://povertydata.worldbank.org/poverty/home/) (WBP)
* [Worldwide Governance Indicators](https://datacatalog.worldbank.org/dataset/worldwide-governance-indicators) (WGI)
* [Global Competitiveness Report Indicators](https://knoema.com/atlas/sources/WEF) (GCI)
* [Observatory of Economic Complexity](https://atlas.media.mit.edu/en/) (OEC)

Most of the data comes from the United Nations Global SDG Database, which is the official source of the SDGs. However, in many cases, this source is insufficient to cover all the 17 SDGs. For this reason, we have complemented the official source with indicators from other databases and classified them into the SDGs.

### Data Structure of National Data
The national level data covers the period 2005-2017, with each year being a column in a table. We provide two versions of it: *normalized* and *raw*. In the normalized version, the indicators have been mapped into the interval [0,1], where zero and one are the lowest and highest values for that indicator, obtained from a larger sample of countries and years (see the technical report for more details). The raw version has the original values. Both datasets can be found in the CSV-formatted files: `sample_data_norm.csv` and `sample_data_raw.csv`. The following table provides an example of the structure.

| 2005 | ... | 2017 | goal | target | countryCode | seriesCode | seriesName | instrumental | reverse |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| .552 | ... | .671 | 17 | 17.2 | MEX | 17.4.1_1 | Debt service as a proportion of exports of goods and services (%) | 1 | 1 |
| .043 | ... | .236 | 5 | NA | MEX | EOSQ088 | Ease of access to loans | 1 | 1 |

Besides the columns representing the years of the observations, there are aditional attributes that we explain bellow:

* `goal`: the SDG to which the indicator belongs (1 to 18)
* `target`: the target to which the indicator belings within its SDG. Targets are only defined for data obtained from the UN and the WDI since their indicators have been classified accordingly.
* `countryCode`: the 3-digit ISO code of the relevant country.
* `seriesCode`: the code of the indicator as it appears in its original database. If there was no code assigned by the data supplier, then one was created (e.g. for most indicators in SDG 1).
* `seriesName`: the description of the indicator as provided by the original data.
* `instrumental`: a binary variable indicating whether we consider that the topic of the indicator is *instrumental*, *i.e.* that is has specific policy instruments and dedicated resources (see technical report for more details).
* `reverse`: a binary variable saying if the indicator needs to be reversed so that a higher value represents a better outcome. In the normalized data, all the indicators that required reversion have been reversed. In the raw data this is not the case.
* `seriesNameSpanish`: the description of the indicator in spanish.
* `sourceName`: the name of the organization from which the indicators were obtained.
* `sourceNameSpanish`: the name in Spanish of the organization from which the indicators were obtained.
* `sourceProduct`: the name of the statistical product from which the data was obtained.
* `sourceProductSpanish`: the name in Spanish of the statistical product from which the data was obtained.
* `sourceLink`: the URL that provides access to the statistical product from which the indicator was obtained.
* `goalOfficial`: the official SDG of the indicator. The only difference with respect to `goal` is that `goalOfficial` does not split SDG 16, so all indicators in either SDG 16a or SDG 16b in `goal` appear as SDG 16 in `goalOfficial`.
* `goalColor`: the color of the corresponding SDG in hexagesimal format. A non-official color is asigned to SDG 16b to differentiate it from SDG 16a in the plots.
* `goalColorOfficial`: the official colors of the corresponding SDG in hexagesimal format.





