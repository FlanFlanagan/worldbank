Fire:
The fire.tif file contains the average burned area per year, where the monthly burned area is summed over each given year to obtain a yearly value, https://daac.ornl.gov/VEGETATION/guides/fire_emissions_v4_R1.html





Climate:
This contains two types of data, 'allmodels' and 'percentilesXX'.
  - 'allmodels' contains
      1) the delta T values (Celsius) or delta CDD values (count) for the 21 models [change_abs]
      2) the percentage of models who see an increase < 1C (band 1), >= 1C (band 2), >= 2C (band 3), >= 3C (band 4), not for CDD. So, in this case, the values respect: band 1 + band 2 = 100 percent, and band 4 <= band 3 <= band 2    ---> This is just in case
  - 'percentiles90' contains
      1) the delta T values (Celsius) for the 3 models --> 10th percentile, 50th percentile, 90th percentile [change_abs]
      2) the corresponding models number that were selected (band 1 = 10th percentile, band 2 = 50th percentile, band 3 = 90th percentile)
  - 'percentiles95' contains
      1) the delta T values (Celsius) for the 3 models --> 5th percentile, 50th percentile, 95th percentile [change_abs]
      2) the corresponding models number that were selected (band 1 = 5th percentile, band 2 = 50th percentile, band 3 = 95th percentile)

The models in the percentiles are selected from the coordinates: (24.3 4.0), approximate center of Africa.
The 10y period given by '2040' is 2035-2044, for reference.

The models are, by band number:
1	ACCESS1-0
2	BNU-ESM
3	CCSM4
4	CESM1-BGC
5	CNRM-CM5
6	CSIRO-Mk3-6-0
7	CanESM2
8	GFDL-CM3
9	GFDL-ESM2G
10	GFDL-ESM2M
11	IPSL-CM5A-LR
12	IPSL-CM5A-MR
13	MIROC-ESM-CHEM
14	MIROC-ESM
15	MIROC5
16	MPI-ESM-LR
17	MPI-ESM-MR
18	MRI-CGCM3
19	NorESM1-M
20	bcc-csm1-1
21	inmcm4

It also contains data on:
- Cooling Degree Days (CDD)
- Number of consecutive days below 1mm (prec_con_lt_1)
- Max 5d rain amount (prec_sum_5d)





Landslide:
The landslide.tif file contains the category of landslide susceptibility, from 1 to 5, from NASA (see reference in paper draft)





Flooding:
The flooding.tif file contains the depth in meters of flooding, from an unpublished (direct communication with Dottori) dataset closely related to https://data.jrc.ec.europa.eu/collection/id-0054





Seismic:
The pga.tif file contains the PGA value for 475 years return period (10 percent exceedance in 50 years). This is from the Global Earthquake Model (GEM), and the data represents the upper limits of the PGA. For example, a value of 0.55 means that the pixel can expect between 0.35 and 0.55g. The legend boundaries can be obtained from this map, https://maps.openquake.org/map/global-seismic-hazard-map. In a perfect world, we would get access to their more detailed data.

Note that this is 10% in 50y, or RP475y. Often, regulations use 2% in 50y, or RP2475y. There is a way to go from one to the other using the literature, if this proves necessary.





Drought:
The droughts are categorized into multiple files, with the duration/intensity/severity metrics, the 3-/6-/12-month timescale, and over three different 30 years period.
The tif files contain 4 different bands.
Band 1: Median [duration/severity/intensity] over the period of interest
Band 2: 95th percentile [duration/severity/intensity] over the period of interest
Band 3: Max [duration/severity/intensity] over the period of interest
Band 4: Count of events meeting a [duration/severity/intensity] condition over the period of interest
  For band 4:
  Duration: count the events longer than 3 months
  Intensity: count the events with a severity lower than -10
  Severity: count the events with an intensity lower than -2
The duration is defined as the number of consecutive months with a SPEI value below -1. Any event shorter than 3 months is discarded (gt3).
The severity is defined as the sum of the SPEI during the duration of the event.
The intensity is defined as the average SPEI during the drought event.

