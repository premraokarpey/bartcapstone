# Executive Summary
## **Original Goal** :
Analysing ridership data collected over a 36 month long period to predict seat availability on the BART using regression models.The Bay Area Rapid Transit has over 800,000 daily passengers, and is the fifth biggest public transportation system in the country. A big slice of the ridership tends to commuting residents during rush hour, when trains can contain over 5000 passengers. This causes overcrowding in cars and hence a metric to predict seat availability can help riders decide between their time of travel or convenience of a seat.
Using these metrics we can provide further insight into traffic along routes and population density. Understanding those trends are key to be able to provide advice on future expansion plans for the BART infrastructure and its subsidiaries.



## **Data** : 

The data that I have gathered are from 2 places, both from the BART public website. The first was the RTGS information that contained the several tables with all the workings of the BART infrastructure. These included start/stop times, station names, locations, fare prices etc. This data helped us to understand the underlying workings of a daily train, and stringent schedules the BART adheres by. 

The second group of datasets were ridership reports. Each report was classified on a monthly basis by weekday, saturday and sunday traffic respectively. These datasets were in a correlational format, i.e by entry and exit stations in a 47X47 format. Understanding how to work with this data was a great challenge in the project. The number of station-station pairs were 46^2 and hence the possible number of routes for a 36 month period were enourmous. I decided to narrow down on the scope of the project to focus on particular routes that had high traffic.

## **Motivation** :
My motivation behind this project was two-fold. I have commuted daily from the WARM SPRINGS BART station to the MONTOGOMERY STREET station every weekday for over 3 months. This line has some of the highest traffic in the BART for daily commuters, going from the Eastbay to Downtown San Francisco for work. The 55 minute train ride is very crowded from 7-9 AM and 4-6 PM on the reverse, which leads to many people being unable to get a seat. In addition, there are frequent delays in the system due to heavy train load and track disturbances. 

My main goal was to figure out how to predict basic ridership for a given route and then see how to establish the frequency with which one can get a seat on the train. This task was very challenging with the given dataset as I had to configure it in a way to help view the data on a route by route basis.

## **Modified Goal** : 
Predicitng ridership for a specific month given 36 months of data on every possible route in the BART infrastrucutre. This equated to 43^2 number of routes and had a sizable dataframe. 

## **Approach** :
The approach to this project was to first get a handle on all the data. As all of my data was offically published on the webiste I downloaded it and put them via read_excel into a jupyter notebook. I wanted to be able to pick out individual routes in the data for multiple years and classify them into 1 list of values. This way I could plot various routes and understand how to create a dataframe that had every possible route. Once I could create a dataframe with one station, I wanted to create a function that would iterate through all the stations and show me all the possible routes with ridership numbers for the last 36 months. 

<img src = "https://git.generalassemb.ly/premrao/bartcapstone/blob/master/datasets/bart/system-map.gif">

## **EDA** :
The EDA for this project was extensive. After loading the RTGS and Ridership reports, I had to understand the data. The RTGS information was pretty straight forward, with labelled tables that were joinable with each other. I plotted a few graphs to illustrate the data, such as stations and ticket fare. Dealing with the Ridership reports proved to be more of a challenge. In its native form, the data was quite dirty. Missaligned columns, and more importantly the correlated data, proved to be hard to alter. However I create 2 functions to process the data and deal out clean data sets. I then looked to create a value function that could give out a list of the last 36 months of ridership data between any 2 stations. This helped to give me a better understanding of the trends and pick and choose which specific routes I wanted to go after. 


## **Modelling** :
For modelling the data I needed to create the final dataframe. With the help of 2 functions, I could create a dataframe that contained every route in the system for the last 3 years and order it. I then decided to go with Linear Regression as the model of choice. I performed a train test split on the data(70-30 split) and then fit and scored it. As the data was so highly correlational, the model score a 0.99+ accuracy for predicting ridership in the month of December 2017. 

## **Roadblocks** :
As the live RTGS information was difficult to set up, it wasn't possisble for me to gather live data and try to use datetime as a feature. Another roadblock was the fact that the initial dataframe had station-station data, but it was not cumulative. This meant that if 50 people got onto the train at Fremont and exited at Montogomery, there would be no metric to know how many other people were on the train at the same time. Furthermore, as there were no external data factors such as weather, holidays or other features, it was hard to create a model with multiple features, hence relying solely on the ridership data. 

## **Results** :

I was able to predict the ridership for the month of december 2017. The accuracy of my model was above 99% and the predicted results showed every station-station result. The trend of data that we see through the project is that routes that are longer in distance have a greater number of passengers. In addition, routes into and out of downtown san francisco are the most crowded, with people opting to live outside the city and commute in for work.

## **Future Steps** :
An important future step for this project would be to calculate the probablity of people getting a seat on every route. This could be done by cumulatively adding the passengers for every route in a certain direction and then diving the number of seats by the passengers. To do this, we would need to incorporate the time of trains, and divide by the number of daily passengers accordingly. 
