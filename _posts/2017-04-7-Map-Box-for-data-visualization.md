Mapbox logo here.

Today I started a project with my friends, [Rowland](https://github.com/row2k) and [Mike](https://github.com/mikearango).  He is what one might consider a data nerd.  We were given access to some US government data on education from IBM, as part of an event hosted by [GW Data](https://www.facebook.com/GWDataScience/).

We had a few ideas about comparing various educations statatistics for the country with income tax rates and school funding data found here: https://www.usaspending.gov/transparency/Pages/SpendingMap.aspx

After looking at more data we decided to compare Math assment success rates with graduation rates.  Do these numbers always coorelate? And can we compare this with school funding?  These were the questions we hoped to answer with the data set.  The data was very messy and we spent the majority of the time cleaning it.  We better documented what each section of the data represents and have added those comments in our repository for it.

I also spent time learning how to use [MapBox](https://www.mapbox.com/), and let say I have fallen in love.  Mapbox, if you haven't heard, is a platform for creating custom and beautiful maps.  It let's you make your own version of google maps with what ever layers, textures, animations, constraints, and styles you'd like.  It's really an incredible tool.  In just a few minutes I was able to build the following map and embed it in a webpage. 

![alt text](https://github.com/mikearango/GWData-IBM-Hackathon/blob/master/src/img/Screen%20Shot%202017-04-07%20at%2010.50.28%20PM.png)

From there we took a bunch of shape files provided to us by IBM.  Shape files hold world coordinate information that can be added over the top of maps.  These shape files had some problems, held too much meta data, and were not compatable with MapBox right away.  Mike was able to clean them up by removing a lot of unneeded fields so that we could add them to our map. When I had a series of working shape files I was able to simply create a layer in MapBox's intuitive web-based editor.  The layer takes the information from the shape files and gives us a view of the borders of every school district in America with an ID (assigned by the Department of Education) associated with each district.  This is very valuable because when we visualize data on each school we want to be able to view it by district, not county or zipcode because that's how funding is given and how our data is tracked.  This map is embedded in the index.html in our project's repo.

The repo with all our code and data has been open sourced and can be found here: https://github.com/mikearango/GWData-IBM-Hackathon.
