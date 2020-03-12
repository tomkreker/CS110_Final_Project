# Under the Radar - Connection Flight Finder

## Motivation
Flight fare-comparison services are extremely popular web applications, particularly among students who travel every four months to a different side of the globe. These students (and many others) are often interested in finding the cheapest way to get from A to B even if it requires additional stops. However, based on my experience, many popular services like Skyscanner are not comprehensive in their coverage of alternative routes in the name of savings. To stick with that example, Skyscanner presents an “Everywhere” feature showing cheap flights options from a source airport, but they do not fully use it when suggesting paths for standard searches — many times I found cheaper fares by manually iterating through the cheap options in the “Everywhere” list and looking for flights from them to my destination. This was the motivation behind this application, titled (unoriginally, I admit) “Under the Radar”.

## Contents
The two main files of interests are:
1. The [report](https://github.com/tomkreker/CS110_Final_Project/blob/master/Final%20project/Under%20the%20Radar_%20Final%20Project.pdf) that summarized the approach, implementation, and results.
2. The [Jupyter Notebook](https://github.com/tomkreker/CS110_Final_Project/blob/master/Final%20project/Under%20the%20Radar.ipynb) with the code.

The code and analysis cover the following topics:
1. Problem description
2. The choice of Dijkstra's algorithm
3. Three adaptations to the algorithm
4. Asymptotic time complexity and memory analysis
5. Practical performance analysis

## Data

The application holds a database of ~3000 airports and ~36000 unique routes between them, each containing the cheapest available fare for the route. The airport and paths (and their accompanying visuals, featured in the cover) were retrieved from [OpenFlights](https://openflights.org/), while fare prices were generated randomly in absence of easily publicly available data, with domestic
flights having a lower range of possible prices than international. The main purpose of this project was thus the implementation of the algorithm to solve the problem, rather than actually producing results (since I did not have the capacity to scrape real fare data).

## Algorithm
I implemented an adapted version of Dijkstra’s Algorithm to find the cheapest route between two given airports up to a given number of stops. I used the heapq Python module to create a min-heap queue, in which insertions and deletions take O( log queue size) time. I used two Python dictionaries to hold the distances and paths of each node. I also made several adaptations to the standard algorithm to save unnecessary relaxations, i.e heap operations, made possible under the application’s constraints. These and further information on the implementation appear in the PDF report.

## Code Design
The code is attached as a Jupyter notebook along with the relevant CSV files containing the data. The code is divided to several sections as follows: Creating the Airport and Graph classes; Importing airport and routes data from CSV files and populate the relevant data structures; The adapted Dijkstra's Algorithm to find the cheapest route up to a given stop limit; Auxiliary functions to get user input and print output; Code for the Performance Analysis section including simulation and graphing; Main section to run the application; Testing zone with a commented simple graph and ready-made specific calls to Dijkstra.
