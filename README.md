Carbon footprint for meetings and courses
-----------------------------------------

Meetings, courses, workshops etc, means that participant travel,
restaurant meals and stays in hotels cause carbon emissions over and
above the carbon emissions of a participant not travelling. This carbon
footprint calculator provides a rough but consistent means of
determining carbon emmision incurred by a meeting and specifically in
this case for TESA activities. The group Technical Expertise in Stock
Assessment (TESA) organises courses and workshops each year for DFO
employees to continually build the expertise in the Department of
Fisheries and Oceans in stock assessment. It is essential that
face-to-face meetings occur for many but not all of these activities.

In an effort to quantify TESA carbon emissions, to track them by year,
activity and location, this carbon footprint calculator has been
developed. It accounts only for travel related carbon emissions
(transport, hotel, meals).

Carbon emissions (tonnes CO2) per km flying, driving, train or bus and
emissions for a night in a hotel or average meal in a restaurant are
taken from
<a href="https://calculator.carbonfootprint.com/" class="uri">https://calculator.carbonfootprint.com/</a>.

Install and load the library
----------------------------

    devtools::install_github("duplisea/TESAcarbon")
    library(TESAcarbon)

Calculate the carbon footprint for an individual traveller
----------------------------------------------------------

Five nights in a hotel, a 600 km plane trip (1200 km total return), 40
km of driving to and from airport solo and 15 meals

    C.f(hotel.nights=5,
        plane.distance=600*2,
        bustrain.distance= 0,
        car.distance=40,
        number.car.sharing=1,
        meals=15)

    ## [1] 0.530904

Carbon emissions for a series of courses or meetings held by ICES
-----------------------------------------------------------------

A mock example of a course offered by ICES is provided with the dataset
ICES. It contains only the essential columns. You can have as many
columns as you want but you need to make sure you have these ones and
they have these exact names (case sensitive)

    names(ICES)

    ##  [1] "activity.type"     "activity.name"     "origin"           
    ##  [4] "destination"       "origin.country"    "hotel.nights"     
    ##  [7] "meals"             "bustrain.distance" "car.distance"     
    ## [10] "car.sharing"       "flying"

You will likely want to create your own .csv file with the names above
and all rows filled in (1 row per participant). You would then import
this and run the carbon footprint function on it. Here is the result of
running the carbon.footprint.f function on the ICES data

    carbon.footprint.f(ICES, "ICES training carbon footprint, mock example", list.out=F)

![](README_files/figure-markdown_strict/ICES.C-1.png)

This creates a global map with all origin cities of all participants
located on the map and the host cities for the courses/meetings are
circled red. A bar graph of the carbon emissions per activity are shown
with per capita values on each bar and the title contains the total
emissions for all activities combined.

Carbon emissions for TESA 2019-20 activities
--------------------------------------------

This calculation is based on actual data though we are not sure of the
final participation of activities yet to come, these are probably close

    carbon.footprint.f(TESA19.20, "TESA carbon footprint 2019-20", list.out=F)

![](README_files/figure-markdown_strict/TESA.C-1.png)

References
----------

<a href="https://calculator.carbonfootprint.com/" class="uri">https://calculator.carbonfootprint.com/</a>
