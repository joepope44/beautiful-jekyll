---
layout: post
published: false
title: 'Linear Regression '
---
## Project -- Linear Regression - State Policy On Firearm Usage


![Gun Violence in America](https://cdn.zmescience.com/wp-content/uploads/2017/01/635849554906566488-1921592675_gun20violence.jpg)

For my linear regression roject at Metis I picked the topic of gun violence in America. Since the horrible incident in Parkland, I have seen numerous articles and research papers investigating the efficacy of various local, state and federal policies regarding the use and access of firearms. 

I was mainly inspired by [this Vox article](https://www.vox.com/policy-and-politics/2017/10/2/16399418/us-gun-violence-statistics-maps-charts) from earlier this year, but also Dr. Listman's work more recently found [here](https://towardsdatascience.com/predicting-gun-death-rate-from-gun-laws-d96041c14198). Listman's work uses R instead of my preferred python, and tree regression instead of traditional linear regression models, however it seemed to be an interesting line of thought to follow. 

I surveyed a number of publically available data sets to begin my research. Ultimately, I pulled data from the CDC and scraped data from a variety of government and other organizations sites to build out my features set. I used the [State Policy Index](http://www.statepolicyindex.com/data/) for most of my policy information. I am not able to vouch for the veracity of this data, but it seemed fine to use for my research project.  

Another promising data source was the [Gun Violence Archive](http://www.gunviolencearchive.org/). This site had the *perfect* data for me, as I was really interested in fatal and non-fatal firearm incidents. Many studies and stats focus on homicides or suicides or both, which is fine, but I really wanted to concentrate on all incidents, regardless if a life is lost. If there were no homicides in your neighborhood, but 20 people get shot and end up in the hospital everyday, wouldn't you want to focus on the non-fatal rate instead?  

Unfortunately, the Gun Violence Archive only had data for the past 72 hours on their site. After a little research I found that a much larger data set, encompassing several years, was on Kaggle. Buried deep in a Discussion forum on the [site](https://www.kaggle.com/jameslko/gun-violence-data/discussion), I was able to see that there were problems with the Gun Violence Archive as a source. For one, they don't want people using their data without going through them. They deliberately spike their data by inserting phony records. This creates a signature that they are then able to spot in the wild. Most noticeably, the 2017 mass shooting in Las Vegas incident is omitted, which is a huge outlier. The explanation is detailed [here](https://www.kaggle.com/jameslko/gun-violence-data/discussion/55307). 

In the end, I decided to not use the Gun Violence Archive data. The CDC data and State Policy Index provided enough information for me to dig into. I learned a lot about handling multicollinearity, regularization and feature selection, but also about one of the most troubling issues of our time. I was unaware that firearm related suicides outpace homicides 2:1, for instance. I also discovered the new and [eminent threat](https://www.wired.com/story/a-landmark-legal-shift-opens-pandoras-box-for-diy-guns/) posed by at-home 3-D printed "ghost guns". We could really figure this whole "2nd Amendment" thing out once and for all and enact true common sense firearm legislation nationwide, only to have anyone with a 3D printer to circumvent those laws and print their own gun (and ammo?). Like most public policy issues, technology is changing the debate as it's happening. 




