---
layout: post
title:  Looker - Handling multiple data sources
---

This blog is written in continuation to an [earlier blog on looker](https://pyari-k.github.io/Looker-As-A-Visualisation-Tool/). While we got introduced with the basic features of looker on the first blog, here we will be dealing with multiple data sources. We will see how we can join two tables and use that data for visualisation.


### Understanding the sample data sources
We have two data sources here. One is a student database. Linked [here](https://docs.google.com/spreadsheets/d/14am_Z1QvdhoPXWXaBixO22zLxCNGmEzy7cqTnBkGTFw/edit?usp=sharing). 
It is in the format as below. 



| id      | firstname | lastname | email                     |
| --------|-----------|----------|---------------------------|
| 1       | Dolli     | Eldrid   | Dolli.Eldrid@xymails.com  |
| 2       | Roberta   | Neils    | Roberta.Neils@xymails.com |


The second [student database](https://docs.google.com/spreadsheets/d/1gCuyqZv5Q2EXaxhPxMwGHYFe140MsP_awvx4k47fBx0/edit?usp=sharinghttps://docs.google.com/spreadsheets/d/1gCuyqZv5Q2EXaxhPxMwGHYFe140MsP_awvx4k47fBx0/edit?usp=sharing)) is the marks in science and maths for the students. The format is like below:


| id      | Maths | Biology |                      
| --------|-------|---------|
| 1       | 84    | 53      | 
| 2       | 68    | 98      | 


### Clubbing both the data sources
We will try to blend this data and make some visuals. 
For this, we need to import both the data sets. We can then use the blend option to join the data sources. In this case, when we configure the joins, we can use the `id` field to join the data sources because that is the column which is the common field which binds the data sources. 

Images showing how this can be achieved is placed below. 

Blending data
 ![_config.yml]({{ site.baseurl }}/images/looker_blend.png)


Configuring the joins
 ![_config.yml]({{ site.baseurl }}/images/looker_join.png)


A short descriptive video on how this can be achieved is also linked [here](https://www.youtube.com/watch?v=oru7tWFdJqk). 





