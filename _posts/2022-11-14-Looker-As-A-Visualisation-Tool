---
layout: post
title: Data Visualisation using Looker - A good to have skill for first time managers 
---
Are you a first time manager or do you get asked a lot of questions at work?
Like where is all our budget going? How much money have we burnt?
Where are we with our targets? What percentage of our company assets are with remote workers?
What is the gender ratio in your organisation? What was our revenue last week?

These questions can sometime be overwhelming if you are a first time manager. We might tend to ramble or start being long winded when we have to answer questions like this. As a manager, you might feel bad about the way you responded for questions like this. 
But, there is a way to tackle this in a much better way. Yes, it is the same old saying that is going to be of our help. 

`A picture is worth a thousand words`

Let us say, you are an admin at a school. You are asked about the gender ratio at your school during an audit. Or you are asked why the teachers and the bus drivers are not paid their salaries?
If you have all your data in one place in a form something like this, we can answer these questions easily with the help of visualisations like this.  

 ![_config.yml]({{ site.baseurl }}/images/01_ds_data_school.png)

 ![_config.yml]({{ site.baseurl }}/images/02_ds_gender_ratio.png)

  ![_config.yml]({{ site.baseurl }}/images/03_ds_fees_paid.png)


Data visualisation is a good to have skills which will help you in cases like this. 
There are many visualisation tools in the market. Some of them are:
1. qlikview
2. tableau
3. powerbi
4. Data studio (now looker)

In this blog, we will be taking a look at data studio/looker in detail and we will get familiarised with it. The reasons, data studio is recommended over other tools is because of the following advantages:
1. Like other products from Google, DS/Looker is cloud based. This also means that we do not have to install any software to start using this. We can just type datastudio.google.com or lookerstudio.google.com on our browser and login with our gmail. We are good to go. 
2. Connecting with data in sources like google drive are easy. They are all in one place. 
3. Creates beautiful visualisations
4. There are cool features like sliders, date pickers and score cards which makes data visualisation customisable for the end users. 
5. The edit mode and view mode helps one who is creating the dashboard to get a feel of how the end user gets to see the dashboard with just one toggle. 
6. Access rights are easy to control. It is very much similar to the access rights . So, gmail users can have a smooth induction to data studio/looker. 

We will see these using small demos in the subsequent session of the blog. 
For this demo, we are using this [dataset](https://docs.google.com/spreadsheets/d/11kStaWZ24G7ahZ9rsZ7Q2EAuzHwly8UaWilvue-jKQQ/edit?usp=sharing). This data set has a set of books and information related to that. 
Now, let us try asking questions like these. 

1. How many books are there in the collection?
2. Can we find out the names of some of the authors in the collection and the number of books under their names?
3. What are the original languages these books are written in? 
4. Can I randomly pick n number of books?
5. What are the pricing of these books? What are their ranges and their distribution?
6. When were these books procured? Given a time period, say 2022 or the last 6 months, can I find the details of the books which are procured during that period?

We can list more questions like this and try getting their answers from these data sets using data visualisations. We can also pass on these visuals to others as well. How do we do all these using data studio/looker? Let us see this in detail:


The first step is to `connect data studio or looker to the data source`. 
In this case, the data source is a google spreadsheet. 
To get a feel of how this can be done, a short video has been created here[https://youtu.be/OaWl7dG35Qg].
It is to be noted that, looker has connectors to various data sources. 

Score Card
A good & beautiful feature of data studio is a score card. This helps us to display any count of records that we are looking for. 
A score card in use will look like this:
 ![_config.yml]({{ site.baseurl }}/images/04_ds_score_card.png)

 In case, if we need the data source to be edited[https://youtu.be/HK6NCmXg3JA], that is also possible. There is an edit option to the data source. The data can be refreshed after reconnecting to the data source in case if it doesn't get automatically refreshed. 
 

 Herewith linked is a short video[https://youtu.be/OLQj3RsANCQ] of how a score can be used in our case to display the no: of books in the data set. In this case, we assume that the number of rows in the data set is the number of books. Hence, the label `number of books` might be more meaningful in a visual. We can hence label the record count to "no; of books". Here is a short simple video[https://youtu.berla1WW-QxgI] of how the record count can be relabelled to no: of books.  

 
Charts
Bar Charts & Pie Charts can easily be created using looker. Below are two charts prepared using data studio. 
 ![_config.yml]({{ site.baseurl }}/images/04_ds_bar_chart.png)
 ![_config.yml]({{ site.baseurl }}/images/04_ds_pie_chart.png)

Creating a pie chart and bar chart is based on similar principles. All you have to do would be to insert a chart and select a type. Plots might be created by some default dimension which is selected by default. We might have to change the chart to reflect the dimension of our choice. 
In this case, we can try plotting the original language in this books are written  using pie charts. So, when we choose the chart, the dimension to be choosen would be Original Language. 
The bar charts are plotted to see the details of the authors in the collection. In that case, when the bar chart is created, the dimesion to be chosen will be authors. 

Videos to the creation of bar and pie charts are linked below:
* [pie chart](https://youtu.be/_LYQrW4J0GQ) 
* [bar chart](https://youtu.be/EJZ_eeQwVHI)

Before moving to some of the coolest features, let us touch upon some of the obvious and trivial features of looker. 

* Access rights to the looker dashboards
Like in the case of google drive, one can share the dashboards via email IDs. 
It is a nice and trivial feature of Looker studio. You may take a look at this [video](https://youtu.be/EJZ_eeQwVHI), to see this in action. 

* Edit mode and view mode 
A dashboard has two type of users. The one who is creating the dashboard and the one who is viewing the end results. Looker hence has two modes. The one who is creating the dashboard can switch between the modes so that she/he gets a feel of how the end user gets to see the final dashboard. Yet another [video](https://youtu.be/wR30WdA-6r8) is linked here to demonstrate this feature. 

So, we are hitting some of the coolest features of looker. 
Don't you think that it is good to leave the end user do some exploration on the dashboard themselves. Looker dashboards can be made dynamic with the help of controls like:
* slider
* date picker
* drop down list 

Slider
A slider helps you to choose the values in a given range. In our case, we can probably say, show me the first 100 books. Or show us what number of books were purchased paying more than INR 500? This is how a slider would look like:
 ![_config.yml]({{ site.baseurl }}/images/05_ds_slider.png)
Let us see how a slider can show us the details of books which costs less than some selected prirce. Take a look at the slider in action [here](https://youtu.be/-rRI_aKpOz4). 

* date picker
Date picker is another feature which helps to build dynamic dashboards. The end user can select dates for viewing the data between the selected dates. [Video linked here](https://youtu.be/aTmVSwqbwIQ) The entire dashboard gets redrawn for the selected dates only. 
 ![_config.yml]({{ site.baseurl }}/images/05_ds_date_picker.png)


* drop down list
Drop down list also helps build dynamic dashboard. This gives the flexibility to the end user to re-render the charts using the selected items in a drop down. For eg, if we want to give an option to the end user to choose the category of books to be defined by him/her to redraw the charts, we can build a drop down list to our chart. [Video linked](https://youtu.be/oLMTYeCDJf0)
 ![_config.yml]({{ site.baseurl }}/images/06_ds_drop_down_list.png)



There are many more features on looker. Quickly touching upon on few more here. But, they are not elaborated. One can divide the dashboard into pages. We have multiple connectors to connect to various data sources. We can add filters to the data. There are many more types of charts and controls. 
I will leave it to you to explore more of these features of looker. 

All the videos used for this blog has been clubbed under a [looker playlist here](https://www.youtube.com/playlist?list=PLQTizSjUx0tXV7eyjmQZOG9KlyhQORnSh). 

Happy Dashboarding. :) 



Before I close, thanks to my classmate & friend Dhanush for allowing me use his data for this blog. The data used has a collection of his books. 

Thank you section :)
* Thanks to WDA for the opportunity & selecting me to be a part of the current cohort. 
* Thanks to my schoolmate and friend Dhanush, for allowing me to use his collection of books and the associated data for the demo purposes in this blog. 










