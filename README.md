# Flexible-mitigation_of_epidemics
This repository summarizes  stores relevant data and simulates control strategies to alleviate epidemics through transportation management, introducing event-triggering mechanisms.

## Traffic Network Data
The following links contain information on German counties, raw data on German transportation, as well as transportation networks at county and state resolutions, and codes for building transportation networks.

https://drive.google.com/drive/folders/1SGO-ZuCZe27Q3X0al5quv27S7iaCpuyH?usp=sharing

This directory holds subdirectories with different data sources. Each subdirectory represents one data provider. The individual data sets are explained in detail.

### data/bkg
Provider: Bundesamt für Kartographie und Geodäsie

Data: Geographic and administrative data of Germany in different resolutions and with differing levels of detail.

### data/delfi
Provider: DELFI e.V.

Data: Public transport information for Germany.


## Data Processing for GTFS
In the GTFS format public transportation dataset, it is primarily necessary to process dataset files such as agency, calendar, calendar dates, trips, routes, stops, and stop times. To process the dataset, which is in the standard GTFS format, for calculating the transient adjacency matrix, the following steps on the respective files are required in the mentioned order:
1) For the agency dataset, reduce to agencies of interest.
2)  For the routes dataset, reduce to routes matching the filtered agency list.
3)  For the trips dataset, reduce to trips matching the \texttt{route\_id} occurrences of the filtered routes list.
4)  For the stop times dataset, reduce to stop times matching the filtered trips list.
5)  For the stops dataset, reduce to \texttt{stop\_id} values occurring in the filtered stop times list.
6)  For the calendar dataset, reduce to the \texttt{service\_id} values matching the filtered trips list.
7)  For the calendar dates dataset, reduce to the \texttt{service\_id} values matching the filtered trips list.
8)  For the stops dataset, match the latitude and longitude with the county polygon from BKG county data and augment the stops table with ARS code per stop.
9)  For the stop times dataset, augment the stop times table with ARS code per stop event using the \texttt{stop\_id}.


