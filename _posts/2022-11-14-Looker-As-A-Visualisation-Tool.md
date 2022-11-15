---
layout: post
title: Looker - A good to know tool for first time managers 
---

### Introduction 
Are you a first time manager or do you get asked a lot of questions at work?
* Where are the allocated budgets being used? 
* How much money have we burnt?
* Where are we with our targets? 
* What percentage of our company assets are with remote workers?
* What is the gender ratio in your organisation? 
* What was our revenue last week?

Questions like these can get overwhelming if you are a first time manager. We might tend to ramble while  answering questions like this. Thanks to the data visualisation tools available in the market. There are better ways to tackle questions like these. It is an old saying that is going to be of our help. 

`A picture is worth a thousand words`

 ![_config.yml]({{ site.baseurl }}/images/looker.png)

Data visualisation is a good to have skill which will help you in cases like this. 
There are many visualisation tools in the market. Some of them are:
* qlikview
* tableau
* powerbi
* Data studio (now looker)

### Why Looker?
  In this blog, we will be taking a look at data studio/looker in detail and get familiarised with it. The reasons, data studio is recommended over other tools is because of the following advantages:
* Like other products from Google, DS/Looker is cloud based. This also means that we do not have to install any software to start using this. We can type in `datastudio.google.com` or `lookerstudio.google.com` on our browser and login with our gmail. We are good to go. 
* Connecting with data which is already on google drive is easy.  
* Looker creates beautiful visualisations
* There are cool features like sliders, date pickers and score cards that makes data visualisation customisable for the end users. 
* Looker has two modes. An edit mode & a view mode. This helps the one who is creating the dashboard to get a feel of how the end user gets to see the dashboard with a toggle. 
* Access rights are easy to control. It is very much similar to how it is done in the case of google drive. So, gmail users can have a smooth induction to data studio/looker.

 We will see all these a bit more in detail in the subsequent sections of the blog. 

### Data Set Used for the demo
For this demo, we are using [a dataset of books](https://docs.google.com/spreadsheets/d/11kStaWZ24G7ahZ9rsZ7Q2EAuzHwly8UaWilvue-jKQQ/edit?usp=sharing). This data set has a collection of books and information related to that. Now, let us try asking questions like these. 

* How many books are there in the collection?
* Can we find out the names of some of the authors in the collection and the number of books under their names?
* What are the original languages these books are written in? 
* Can I randomly pick n number of books?
* What are the pricing of these books? What are their ranges and their distribution?
* When were these books procured? Given a time period, say 2022 or the last 6 months, can I find the details of the books which are procured during that period?

### Connecting to the data source 
  The first step in building the visualisation is to `connect data studio or looker to the data source`. 
In this case, the data source is a google spreadsheet. It is to be noted that, looker has connectors to various other data sources as well.
[Video demo on connecting looker to a data source](https://youtu.be/OaWl7dG35Qg).

### Score Card 
  Score card is a good & beautiful feature of data studio. This helps us to highlight any kpis or prominent numbers that we are looking for. A score card in use will look like this:
![_config.yml]({{ site.baseurl }}/images/04_ds_score_card.png)

  In the case of our books data, it can be safely assumed that the number of rows in the data set is the number of books. Hence, the label `number of books` might be more meaningful in a visual. Hence it might be appropriate to label the score card to `number of books`
[Video demonstrating the creation of score card](https://youtu.be/OLQj3RsANCQ)
[Video demonstrating the change of label of a score card](https://youtu.berla1WW-QxgI) 

### Editing the data source 
  Sometimes, we make changes to the source data. We add certain fields to the source data or we decide to remove some rows. In case we wante the data source to be edited on looker, that is also possible. 
 [Editing the data source](https://youtu.be/HK6NCmXg3JA)
 
### Charts 
  Bar Charts & Pie Charts can easily be created using looker. Below are two charts prepared using data studio. 


 ![_config.yml]({{ site.baseurl }}/images/04_ds_bar_chart.png)
 ![_config.yml]({{ site.baseurl }}/images/04_ds_pie_chart.png)

Creating a pie chart and bar chart is based on similar principles. All you have to do would be to insert a chart and select a type. Plots might be created by some default dimension which is selected by default. We might have to change the chart to reflect the dimension of our choice. 

In the case of the books data used in this demo, we can try plotting the original language in which these books are written using pie charts. The point to be noted here is that, when we choose the chart, the dimension to be choosen would be Original Language. 

Videos demonstrating the creation of bar and pie charts are linked below:
* [Video - creating a pie chart on looker](https://youtu.be/_LYQrW4J0GQ) 
* [Video - creating a bar chart on looker](https://youtu.be/EJZ_eeQwVHI)

Before moving to some of the coolest features, let us touch upon some of the obvious & trivial features of looker. 

### Access rights to the looker dashboards 
Like in the case of google drive, one can share the dashboards via email IDs. 
It is a powerful feature of Looker studio. 
[Viideo - on Access Rights](https://youtu.be/EJZ_eeQwVHI)

### Edit mode and view mode 
A dashboard has two type of users. The one who is creating the dashboard and the one who is viewing the end results. Looker hence has two modes. The one who is creating the dashboard mainly works with the edit mode. The end user gets to see the view mode. The creator of the dashboard has an option to switch between the modes so that she/he can get a feel of how the end user gets to see the final dashboard. 
[Video - Edit mode & View Mode on Looker](https://youtu.be/wR30WdA-6r8) 

So, we are moving to some of the coolest features of looker. 
Don't you think that it is good to leave the end user do some exploration on the dashboard themselves? Looker dashboards can be made dynamic with the help of controls like:
* slider
* date picker
* drop down list 

### Slider 
A slider helps you to choose the values in a selected range. With our data set, we can probably say, show me the first 100 books. Or show us the books that were purchased paying more than INR 500. This is how a slider would look like:

 ![_config.yml]({{ site.baseurl }}/images/05_ds_slider.png)

[Video - Slider in Action](https://youtu.be/-rRI_aKpOz4). 

### Date picker
Date picker is another feature which helps to build dynamic dashboards. The end user can select dates for viewing the data. When a date picker is used to chooses a start and end date, the dashboard gets redrawn with the data for the selected dates only. 
 ![_config.yml]({{ site.baseurl }}/images/05_ds_date_picker.png)
 [Video on a date picker linked here](https://youtu.be/aTmVSwqbwIQ) 

### Drop down list
Drop down list also helps build dynamic dashboard. This gives the flexibility to the end user to re-render the charts using the selected items in a drop down. For eg, if we want to give an option to the end user to choose the category of books to be defined by him/her to draw the charts, we can build a drop down list to our chart. 
 ![_config.yml]({{ site.baseurl }}/images/06_ds_drop_down_list.png)
 [Video - Drop Down List](https://youtu.be/oLMTYeCDJf0)

### There is more to Looker! 
There are many more features on looker. Quickly touching upon on few more here. But, they are not elaborated. 
* One can divide the dashboard into pages. 
* We have multiple connectors to connect to various data sources. 
* We can add filters to the data. 
* There are many more types of charts and controls. 

I will leave it to you to explore more of these features of looker. 

All the videos used for this blog has been clubbed under a [looker playlist here](https://www.youtube.com/playlist?list=PLQTizSjUx0tXV7eyjmQZOG9KlyhQORnSh). 

Happy Dashboarding. :) 

### Thank you section :)
* Thanks to WDA for the opportunity & selecting me to be a part of the current cohort. 
* Thanks to my schoolmate and friend Dhanush, for allowing me to use his collection of books and the associated data for the demo purposes in this blog. 










