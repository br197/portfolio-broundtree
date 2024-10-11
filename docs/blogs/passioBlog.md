---
title: "Passio Go UI Commentary"
layout: doc
---

# Passio Go UI Commentary

After attending this week’s UI design lecture, I was inspired to think about the technologies that I use on a daily basis and how their UI designs help (or disrupt) my user experience using them. One of the technologies that came to mind is Passio Go, the transit tracking app used by university students to track campus shuttles and where they are on their routes. 

Below I will analyze the app against some of the heuristic evaluation points presented in class. However, before I do so, I think it is important to remember the purpose of the app: to provide users with relevant transit tracking information, when analyzing the UI of an app.

## Ease of Use (Learnability):

Passio Go’s interface for its baseline functionality is pretty intuitive and with repeated use, users should be able to discover most of its other functionality. The main functionality of the app is for transit tracking. The interface to track transit on the app is very clearly visible (it's the first thing users see). This interface displays where the user is (see blue dot), where the transit vehicles are (see moving colored dots), and which stops these transit vehicles go to (see static pie chart dots). Once the user makes the connection of what these icons mean, the user can take advantage of the app and its main functionality. 

However, for the app’s other functionality, it can take a little bit of time to figure out. Most of the app’s other functionality are hidden in collapsed sidebars or menus. Users will need to click on these menu icons and explore the menu contents in order to discover the other features of the app that they can use.

I think the most hidden feature (and sometimes confusing) is how to get the arrival times of the vehicle. There are two methods to do this. The first method requires the user to discover that clicking onto one of the stops (colored pie chart dots) will give them a report the ETA of each shuttle that runs through the stop, bus number, and stop information. The second method requires the user to hold down on the map until a gray target and then drag the target over the stop that they would like to see the information for.

These hidden features, especially in getting the arrival times, create higher recall burden on the user as they are hidden and sometimes require multiple trials and errors to rediscover the feature.

<img src="/assets/images/passioHomeTarget.jpeg" width=300px height= 300px>

## Mapping:

I think Passio Go does a good job of laying out its interface to match its function. Upon entering the app, the user is presented with a map of their surrounding area filled with color coded routes and icons that represent transit vehicles rather than presenting something like a list of transit vehicles and their stops (ie [the MBTA bus site](https://www.mbta.com/schedules/bus)). This UI fits the apps purpose of displaying transit information because it does just that, it shows where the vehicles are and what routes they take.

<table>
<tr>
<td>
<img src="/assets/images/mbta.png" width=400px height= 400px>
<p>Boston MBTA bus routes</p>
</td>
<td>
<img src="/assets/images/passioHomeBare.jpeg" width=300px height= 300px>
<p>MIT shuttle routes</p>
</td>
</tr>
</table>


## Typography:

I really like the app’s use of color to differentiate the transit routes and how it associates information for each route with its color. The coloring creates consistency in the app (you see a color and know anything in that color belongs to route X) and creates color associations (mapping color to route/its information), making it more efficient for the user to identify routes and locate transit vehicles (and their stops). Users can just look for the color of their desired route on the home screen rather than having to click a stop to check if the transit vehicle goes to that stop or perform other additional actions to seek out the information they need.

With the color aspect of the app, it is important to keep in mind accessibility to ensure the color choices in the app and colored information is easily readable for those who are colorblind or see color in different ways.

<img src="/assets/images/passioHome.jpeg" width=300px height= 300px>
