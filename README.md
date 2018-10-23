# 2nd Annual Singapore Collegiate Math Modelling Challenge

![comp](https://raw.githubusercontent.com/tonghuikang/sutd_modelling_comp_2018/d8933fd01de2b2e2793577103d3d613ce594bbed/comp.png "Competition information")

This competition was done with Foo Lin Geng. https://github.com/lingengfoo

# About the competition
This competition is conceived by Sergey Khursarvhev from Singapore University Technology and Design and MAJ Jessica M. Libertini from Virginia Military Institute. This serves to expose undergraduates to mathematical modelling and hopefully recuit and prepare local participants for COMAP Mathematical Contest in Modelling (MCM/ICM). This competition is modelled after modelling competitions such as those from COMAP. 

Foo Lin Geng and I participated in 2018 COMAP MCM/ICM and achieved a Honorable Mention.

# Question Statement

> ## A Song of Fire and Glaciers
> Glacier National Park is a popular tourist destination for hikers and campers in the summer.  Many of the campsites in the park are accessible only on foot, and most require a substantial amount of hiking and/or climbing to reach.  While this can be idyllic for outdoor enthusiasts, it can also be hazardous during drought summers.  On August 10, 2017, a forest fire was spotted burning near Lake McDonald in the southwestern portion of the park.  On August 12, 2017, another fire started near Logging Lake in the northwest part of the park.  To date these fires have burned more than 20,000 acres, causing the evacuation and closure of at least 8 back-country campgrounds and numerous trails.
>
> This poses an interesting challenge for park officials.  During late August, all back-country campgrounds are filled to near capacity.  Since there is little cell coverage in the park, there is virtually no way to contact campground occupants apart from visiting them in person.  Federal law (and local trail conditions) prohibits the use of wheeled or motorized vehicles in the back-country.  In the event of a fire, all back-country campers need to be evacuated from the park, presumably by hiking to a location where they can be transported by bus to safety.  What is the best way to facilitate the evacuation of campgrounds that are only accessible by foot?  How long should an evacuation be expected to take?  From which of the ranger stations should evacuation teams be dispatched in order to vacate each campground? 
>
> Your task in this problem is to propose an evacuation plan for each of the park regions in the event of a fire.  Assume that rescue teams can be dispatched from each of the five backcountry permit offices (Apgar, Two Medicine, Many Glacier, St. Mary, and Polebridge).  You should specify which ranger station(s) should dispatch which team(s) and provide estimates on how many evacuation crews should be dispatched and how long evacuation will take.  
Remember:
>	- the National Park Service does not have unlimited resources.
>	- in rough terrain, there are limits as to how far hikers can be expected to travel in a single day.
>
> The following links may help you get started: <BR>
> https://www.nps.gov/glac/planyourvisit/upload/Backcountry-Map-Web.pdf <BR>
> https://www.nps.gov/glac/planyourvisit/backcountry.htm
>
> In the Analysis and Model Assessment make sure to address the following question: how much would you need to tweak your model to address the same issue for another country (e.g., what’s the evacuation plan from a national park in Indonesia in the event of a volcano eruption).
> Describe qualitatively what’s good from your model and can be transferred to the new situation
and which parts of your model need to be tweaked/modified.

# Executive Summary

## Introduction and Objectives
Our team aims to maximise the amount of evacuation time for the most vulnerable campers, to minimise potential casualties in the event of a wildfire at Glacier National Park. We shall find the most optimal way to dispatch the rangers to inform the campers whose campgrounds are at imminent risk of wildfire.

## Assumptions
We assume that all hikers can be found on the tracks, and that all hikers have a similar hiking speed that can be approximated by the Naismith’s rule to be around 3 mph. Hikers also do not need a ranger to escort them back to safety, and only need a notification. We also assume that the fire is detected in its early stages.

## Our Model
Our model consists of two parts, the simulation of the spread of wildfire, as well as the evaluation of the rangers’ path. The speed of spread of wildfire is modelled by three parameters – a base rate, wind speed and the angle of the slope, in an equation with constants tuned to match the Rothermal model in the R library. The propagation of wildfire was modelled as a conical shape, in the direction of wind travel.

As for the rangers, we decided to dispatch one team of rangers from each permit office. We start with few preset routes available for the rangers to choose from, and they can run the ranking algorithm that tells them which route to choose. The ranking algorithm ranks the routes according to an “urgency score”, which tells them which route is most urgently in need of evacuation. Should a location be already burning, or should there be insufficient time for the rangers to reach the target location safely, those locations/evacuation routes would be taken out of consideration for land rangers. Evacuation can take from 20-30 hrs.

## Areas of Improvement
We think that impassable terrain for fires, such as lakes and glaciers, should have been considered as factors in our wildfire model. We also did not consider scenarios when another forest fire suddenly appearing after all the rangers have already been deployed. While we could weigh between two set of paths, we have not developed an algorithm that guarantees the most optimal path configuration.

## Conclusion
Our model was tested to be robust during our simulations, and it could deal with cases where multiple fires are detected at once. It is also not more difficult to adapt our model for use in other forests, by introducing another map and changing hyperparameters like wind speed, the angle of slope, etc.

![screenshot](https://raw.githubusercontent.com/tonghuikang/sutd_modelling_comp_2018/master/screenshot.png "screenshot")

# Reflections

We managed to create something of minimum value - an algorithm that evaluates which of the two evacuation path chosen is better. With better coding skills and time this can be generalised to generate the safest path by interating through the various combinations. In this aspect, and together with later experiences at coding competition, anyone claiming to code algorithms should be able to work with graphs and implement Dijkstra's algorithm is the various contexts.
