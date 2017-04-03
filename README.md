# SETI Institute Hackathon and Code Challenge
#### Machine Learning 4 the Search for Extra Terrestrial Intelligence (http://www.seti.org/ml4seti)

## Introduction

This page documents the details for the SETI Institute's Hackathon (June 10-11, 2017) and code challenge (June 1 to July 31, 2017), 
as generally described on our main page, http://www.seti.org/ml4seti

## Contents

  * [Project Details](#project-details)
  * [Event Details & Registration](#event-details--registration)
      * [Hackathon Schedule](#hackathon-schedule)
  * [Awards & Prizes](#awards--prizes)
  * [Teamwork](#teamwork)
      * [Click here to up for Slack Team](https://ml4seti.mybluemix.net)
  * [Licensing](#licensing)
  * [FAQ](#frequently-asked-questions)
  * [Other Reading](#other-reading)

## Project Details

Each night, using the Allen Telescope Array (ATA) in northern California, we scan the sky at 
various radio frequencies, observing star systems with known exoplanets, searching for faint but persistent signals. 
The current signal detection system is programmed to search only for particular kinds of signals: narrow-band 
carrier waves. However, the detection system sometimes triggers on signals that are not narrow-band signals 
(with unknown efficiency) and are also not explicitly-known radio frequency interference (RFI). 
There seems to be various categories of these kinds of events that have been observed in the past. 

Our goal is to classify these accurately in 
real-time. This would allow the signal detection system to make better informed observational decisions, 
increase the efficiency of the nightly scans, and allow for explicit detection of these other signal types. 

The standard approach to SETI signal detection and classification is to transform the observed radio signals, which
are time-series data, into a 
2-dimensional representation called a spectrogram. A spectrogram is a measure of the power of the signal across 
a range of frequencies, as a function of time. From this, our software searches for narrow-band signals. 
One can also think of a spectogram as a 2D image and transform the 
problem into a visual recognition problem. This is likely to be the primary approach for most solutions, 
though other methods are certainly possible. 

For example, here is a classic narrow-band signal observered from the 
[ISEE3 explorer](https://en.wikipedia.org/wiki/International_Cometary_Explorer). These are the kinds of
signals our software is tuned to identify.


![ISEE3 Narrow Band Signal](img/isee3.png "ISEE3 Narrow Band Signal")


But things are never that pretty unless we're looking at a man-made spacecraft. Here's another example: 
a mysterious squiggle observed in 2014 (the color scale is different because the power amplitude, coming out of the
page is on a log-scale). 


![Mystery Signal](img/mystery_squiggle.png "Mystery Signal")
 

Similar to the second signal above, we often see various signal types that our software are not specifically 
designed to detect and classify. Thesea are signals that we sometimes call "squiggles", "pulsed", and 
"bright pixels".

We want to build classification models that are designed to find these "other" types of signals. 
We believe a public code challenge and hackathon around this problem would be a great way to engage the public 
and utilize the expertise from the data science community -- to increase the number of large cups in the water, 
as [may be described](https://www.ted.com/talks/jill_tarter_s_call_to_join_the_seti_search) by, our own, [Dr. Jill Tarter](http://www.seti.org/users/jill-tarter).

If you have participated in the SETI@IBMCloud project 
([blog post](https://developer.ibm.com/clouddataservices/2016/09/29/seti-data-on-ibm-cloud/), 
[github repo](https://github.com/ibm-cds-labs/seti_at_ibm)), these spectrogram should be familiar to you. 

### The Hackathon & Code Challenge
 
The code challenge will ask participants to build a classification system based on a large body of simulated 
data that we are now constructing. You will receive the raw data for tens of thousands of signals, 
like the ones you see above. 
The simulated data set will be used for the training and test data sets for 
signal detection and classification tools. Models will be judged based on their accuracy and speed 
(the detection system is done in real-time so solutions will need to classify single events relatively quickly). 
The most-accurate solution, which can classify a single event in "real-time", will be installed into our data
analysis pipeline at the Hat Creek Observatory. 

 
#### The Hackathon 

The hackathon will be a mini-version of the code challenge, with its own set of prizes; an event 
entirely within itself that you can participate in. However, it will also be a kick-off for the larger 
code challenge. 


## Event Details & Registration

We have two separate Eventbrite pages for registration. 

**Our event registration is not yet complete! Please [leave your email address here](http:www.seti.org/ml4seti) 
and we'll notify you as soon as they are ready!**

  * Hackathon: 
  * Code-Challenge: 


### Hackathon Schedule

  * Saturday, June 10, 2017
    * 8:00 - 9:00    Breakfast
    * 9:00 - 10:00   Introduction, Team forming
    * 10:00 - 12:00  Hack
    * 12:00 - 1:00   Lunch + Talk by [Dr. Jill Tarter](http://www.seti.org/users/jill-tarter) and [Dr. Gerry Harp](http://www.seti.org/seti-institute/staff/gerry-harp) of the SETI Institute
    * 1:00+          Hack
  * Sunday, June 11, 2017
    * 8:00 - 9:00    Breakfast
    * 9:00 - 12:00   Hack
    * 12:00 - 1:00   Lunck + Talk by [Dr. Danny Price](https://seti.berkeley.edu/people/Danny.html) of the [UC Berekeley SETI Research Center](https://seti.berkeley.edu/index.html)
    * 1:00 - 4:00    Hack
    * 4:00 - 5:30    Presentations + Awards
    * 5:30+          Hack until Galvanize kicks us out



## Awards & Prizes

We are excited to be able to offer some amazing and extremely unique prizes! 
You will simply not find prizes like this anywhere else.

### Code Challenge

The prize for the best classifier submitted by the end of the code-challenge will be:

  * Installation of code at ATA data acquisition pipeline.
  * Co-authorship with SETI Institute researchers on a paper to be submitted in a peer-reviewed scientific journal
  * Assistance presenting work at a SETI research conference or meetup. 

### Hackathon Awards

At the end of the hackathon, the judging panel will listen to brief presentations by participating teams
and offer awards on the

  * Most Accurate Analysis (you will present your own confusion matrix -- 
  we will not check results, so we rely on the honor system.)
    * Winner gets a tour of the ATA with SETI Institute scientists (up to 6 team members).
  * Most Interesting / Surprising Analysis

We are working on more awards and prizes for both the hackathon and code challenge.   


### Code Challenge Judging

We are planning to judge the main code challenge entries by the following metrics

  * LogLoss function based on confusion matrix results
  * Speed of single-event classification (for real-time compatibilities)

**Very Important!**  Your code entry / model must be capable of running in the SETI Institute's 
IBM Spark enviornment, which will be used for final analysis using our large simulated data set. 
We'll work with you to port your model to our system. 

Before the code challenge, we will have a better definition of how you will need to interface your code entry 
to measure it's performance.

## Teamwork!

You will mostly likely need to form a team of 4 to 6 people in order to accomplish your goals in a 
timely manner. To facilitate team-building, among other things, we have created a Slack team for 
communication. We will add Slack channels for different analysis approaches so you can easily 
communicate with the entire community.

[Sign up for the Slack team here.](https://ml4seti.mybluemix.net)


### Analysis Ideas

List of analysis ideas and concepts that may be useful:

  * "standard" machine-learning feature extraction (see [`ibmseti`](https://github.com/ibm-cds-labs/ibmseti))
  * Watson Visual Recognition
    * train Watson after using some kind of image filtering.
  * Deep Learning (DNN, CNN)
    * on fourier-space representation 
    * on raw time-series
  * [Deep Forest](https://arxiv.org/abs/1702.08835)
  * Priciple Component Analysis
  * Decision Tree
  * Support Vector Machines
  * k-Nearest Neighbors
  * Wavelet decomposition
  * De-chirping
  * KTL transform



If you wish you contribute a separate idea to this list you can

  * issue a Pull Request to this repo
  * talk to an organizer on our Slack team (`@gadamc` or `@gerryharp`)

## Licensing

In order to participate in the code challenge and hackathon, your code must be open-source and licenced under 
the Apache License 2.0. 

## Frequently Asked Questions

**Can I participate in the hackathon remotely?**

We are hoping to livestreaming the talks and to share any slides that are presented. In this way, you
can partially observe what is happening during the hackathon.
All material and information that you will need to do the work will be available online, of course. You
can participate with teams at the hackathon (and communicate wit your team via Slack). 
However, we cannot ship any prizes or give-aways to teams that are entirely
remote and we cannot support presentations of work for remote teams. 


## Other Reading

The SETI Institute has been partnering with IBM for almost two years now. We've done amazing work together and 
have written about it in various places. Please check it out!

  * [SETI@IBMCloud: SETI data, publicly available, from IBM](https://developer.ibm.com/clouddataservicesold/2016/09/29/seti-data-on-ibm-cloud/)
  * [SETI sparks Machine Learning to sift Big Data](http://blog.ibmjstart.net/2015/07/14/seti-sparks-machine-learning-to-sift-big-data/)
  * [Types of Big Data from the Allen Telescope Array](http://blog.ibmjstart.net/2015/08/06/types-of-bigdata-from-the-allen-telescope-array/)
  * [Signal Classification: Powerful Patterns from Simple Features](http://blog.ibmjstart.net/2015/11/10/signal-classification-powerful-patterns-from-simple-features/)
  * [IBM and Stanford University team up for a new perspective on SETI signal analysis](http://blog.ibmjstart.net/2016/06/29/ibm-stanford-university-team-new-perspective-seti-signal-analytics/)
  * [Status Update from the SETI Institute](https://developer.ibm.com/clouddataservicesold/2016/03/07/status-update-from-the-seti-institute/)
  * [The SETI Project Team](http://blog.ibmjstart.net/2016/10/25/draft-seti-project-team/)

