---
layout: post
title:  Looker - Handling multiple data sources
---

This blog is written in continuation to an [earlier blog on looker](https://pyari-k.github.io/Looker-As-A-Visualisation-Tool/). While we got introduced to the basic features of looker on the first blog, here we will be dealing with multiple data sources. We will see how we can join two tables and use that data for visualisation.


### Understanding the sample data sources
We have two data sources here. One is a student database. Linked [here](https://docs.google.com/spreadsheets/d/14am_Z1QvdhoPXWXaBixO22zLxCNGmEzy7cqTnBkGTFw/edit?usp=sharing). 
It is in the format as below. 


```
| id      | firstname | lastname | email                     |
| --------|-----------|----------|---------------------------|
| 1       | Dolli     | Eldrid   | Dolli.Eldrid@xymails.com  |
| 2       | Roberta   | Neils    | Roberta.Neils@xymails.com |
```



The second [student database](https://docs.google.com/spreadsheets/d/1gCuyqZv5Q2EXaxhPxMwGHYFe140MsP_awvx4k47fBx0/edit?usp=sharinghttps://docs.google.com/spreadsheets/d/1gCuyqZv5Q2EXaxhPxMwGHYFe140MsP_awvx4k47fBx0/edit?usp=sharing)) is the marks in science and maths for the students. The format is like below:


```
| id      | Maths | Biology |                      
| --------|-------|---------|
| 1       | 84    | 53      | 
| 2       | 68    | 98      | 
```

### Clubbing both the data sources
We will try to blend this data and make some visuals. 
To do this, we have to first import both the data sets. After that, We can use the blend option to join the data sources. In this case, when we configure the joins, we can use the `id` field to join the data sources because that is the column which is the common field which binds the data sources. 

A short descriptive video on the usage of blending data from multiple data sources is also linked [here](https://www.youtube.com/watch?v=oru7tWFdJqk). 

Images showing how this can be achieved is also placed below. 

Blending data
 ![_config.yml]({{ site.baseurl }}/images/looker_blend.png)


Configuring the joins
 ![_config.yml]({{ site.baseurl }}/images/looker_join.png)


### Why club data sources?
CLubbing data sources help us answer questions related to the entire data set. 
For eg, in the above two data sets, we have student information in one set. In the second, we have student marks. 
If we have to find the names of the top 5 students who scored the highest percentage, we can sort the clubbed data in the descending order of the percentages and we know who scored the best! 

![_config.yml]({{ site.baseurl }}/images/blended_data_answers.png)
