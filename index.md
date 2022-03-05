---
layout: default
altair-loader:
  altair-chart-1: "charts/bikecountAltair-008.json"
  altair-chart-2: "charts/bikecountAltair-062.json"
  altair-chart-3: "charts/bikecountAltair-111.json"
hv-loader:
  hv-chart-1: ["charts/passengerCount.html", "500"] # second argument is the desired height
---

# Looking at bike-bus interactions in NYC

## Introduction

What is the relation between bus arrivals and departures from a metropolitan bus stop, and the bike-share use in their vicinity? Is there a way to asses the interaction between both systems in order to provide advantages to users of both systems, like free rides for people just dropping off the bus that would similar to transit transfers? 

This project consists in a method to simultaneously retrieve real-time data from both the New York City's [MTA Bus API](https://bt.mta.info/wiki/Developers/Index) and [Citi Bike's Open Data live feed](https://ride.citibikenyc.com/system-data), wrangle it and display it in a way that shows possible interactions between both transit systems.

In order to do so, three bus stop-bike dock pairs were selected among the same MTA Bus route, the M15 Bus in its northward direction. The bus stops of these three observed locations had to comply with three conditions for the conclusions to be relevant:

* to be at least three blocks away from any Subway stations.
* to only serve the bus route selected.
* to be located sufficiently far apart and thus have different demographic or socioeconomic conditions around.
* test.


![map showing MTA transit system]({{ site.url }}{{ site.baseurl }}/assets/img/bbmm_01.png)


The locations chosen were the **1 Av./St. Mark's Pl.** stop in the more commercial Lower East Side, the **1 Av./62nd St.** stop in the affluent Lennox Hill Neighborhood and the **111st St.*** stop in the historically disadvantaged East Harlem neighborhood.


![map showing closeups of stops to be considered]({{ site.url }}{{ site.baseurl }}/assets/img/bbmm_02.png)



The observations for this sample data were obtained at 3 minute intervals over a half-hour period on a Sunday. Please note that the results retrieved in this time period might have been affected by the surge in COVID cases in the area at that moment related to the Omicron variant.


## Results

Once the data is retrieved and sorted, it is possible to produce charts comparing the arrival (or departure) of buses to an specific bus stop and the change in bike availability of its nearby Citi Bike dock, through time and by station.



<div id="altair-chart-1"></div>

In the Lower East Side's **1 Av./St. Mark's Pl.** stop the availability of bikes remained costant and high despite the two incoming bus stoping by.

<div id="altair-chart-2"></div>

In the Lennox Hill's **1 Av./62nd St.** stop there were few bikes and aa couple of them were checked out within the 3 minues after the bus arrived.

<div id="altair-chart-3"></div>

Over at East Harlem's **1 Av./111st St.** stop, bikes appear to have been checked out before and after each bus arrival.


This interactions can also be visualized with a map of moving buses and the corresponding change in bike availability at each location:


![Alt Text]({{ site.url }}{{ site.baseurl }}/assets/img/busBike.gif)



## Passenger counts

The data retrieved from the coordinated API call also includes a limited amount of bus units' passenger counts.

This can be visualized by bus unit and period of time they stopped at one of the observed locations.

<div id="hv-chart-1"></div>


The interaction of passenger counts and bike availability can also be visualized in a map across time:


![Alt Text]({{ site.url }}{{ site.baseurl }}/assets/img/busPass.gif)


## Notes

- See the [jupyter notebook](https://github.com/golete/bike-bus-project/blob/main/550-Final_Main.ipynb) that produced these plots.
