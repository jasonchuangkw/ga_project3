
## Project 3 by Jason Chuang


## Problem Statement


Ableton Live and Fruity Loop Studio (FL Studio) are two different brands of Digital Audio Workstation (DAW). These two DAW are popular among music producers who make electronic dance music (EDM). For this reason, it is more popular among younger music producers. 

The purpose of this project is to identify differences between these two softwares based on the posts made for their respective reddit, r/ableton and r/FL_Studio so as to help young music producers

1) What are the key differences between these two softwares based on the responses from the reddit post?

2) How could one differentiate whether one post is from r/ableton or r/FL_Studio?

The findings, if possible, would help young music producers decide which software is more suitable for their needs.


## Background

It is much easier these days for aspiring musician to produce their own music from their home because of technology. If you think of Photoshop as the professional standard software for photo editing, music producers make use of a software called Digital Audio Workstation (DAW) that has all the necessary tools that can help them to complete a music production from recording, mixing and mastering, with the help of a computer. Back in the past, one could imagine that music production can only be done in a music studio that has lots of equipment. Now, even the modern music studio is also supported by computer through the DAW software.

Fast forward to our present time, there are many DAW choices in the market that it has become a very competitive market. Avid 'Pro Tools' being one of the earliest DAW is an industrial standard for Film and TV music. Steinberg Nuendo/Cubase is a popular alternative that is more popular in Europe. Ableton Live and Fruity Loop (FL) Studio are the more popular DAW for music producers specialised in Electronic Dance Music (EDM).


## Data Source

Through an API, we obtained the reddit posts for r/ableton and r/FL_Studio between 17 Nov 2020 and 17 Nov 2022. We combined the title and content of the post and dropped any of them which has less than 20 word. We also removed duplicated words. Our first cut result in about  18,562 and 13,772 for Ableton and FL Studio respectively. After doing further data cleaning, we reduced this to 14,881 and 9,305 respectively.

## File Organisation

The following is the order which the files are organised:<br>
(1) data_download_ableton - python codes that help to draw data from r/ableton<br>
(2) data_download_flstudio - python codes that help to draw data from r/ableton<br>
(3) clean_edm - python codes for cleaning and organising the data<br>
(4) model_data - python codes for modelling<br>

## Analysis

Post Observations - posts made to r/ableton and r/FL_Studio tend to revolve around:<br>
(1) Seek help or ask advice from other users pertaining to Ableton or FL Studio<br>
(2) Seek help or ask advice from other music producers on specfic topics<br>
(3) Information and updates relating to music production<br>

As expected, the top words that appeared in the posts are related to Ableton and FL Studio brand, however the occurance of is higher for Ableton (in r/ableton) than FL Studio (in r/FL_Studio).

We used a variety of models to help us to determine which words are more important than others in making distinction between the two subreddits. The Random Forest Classifier was eventually the chosen model as it gave the best result (90% accuracy for both the train and test data).

Technical Note (for those who are interested):<br>
While we have looked into other criteria to decide which model is the best, eventually acurracy was chosen as the objective of this research was to identify the words and to minimise Type I or ype II errors are less importance.

## Summary of Findings

Summary of Model Evaluation<br>
|Model|Train Cross Validation|Test Cross Validation|Accuracy|Type 1 Error|Type 2 Error|
|:---|---:|---:|---:|---:|---:|
|Random Forest Classifier|0.909|0.909|91%|5.1%|3.7%|
|K-Nearest Neighbour Classifier|0.904|0.898|91%|5.0%|4.3%|
|Support Vector Machines|0.894|0.882|90%|5.0%|5.0%|

The findings were derived based on the sorted data from df_rf.csv (output file for Random Forest Model). Here, we zoom into a few top relevant keywords (based on importance) that appeared in both r/Ableton and r/FL_Studio.  The rank is based on importance.<br>

<ins>Words More from Ableton</ins><br>

Midi (Rank: 11)<br>

MIDI is tool or language that converts music notes (e.g. A, B, C) to numbers so that it could be understood by computers.Ableton is more associated with customised programming and therefore this seems reasonable that Midi is more related from Ableton posts.<br> 

Track, Session, View and Clip (Rank: 12,18,25,36)<br>

These words are closely associated to Ableton's unique workflow known as Session View and Arrangement View. 'Clip' and 'Track' are also words associated to these views. This finding reinforces this uniqueness.<br>

Push and Push_2 (Rank 19,40)<br>

Push and Push 2 (Version 2) are the unique devices that work with Ableton software. This finding reinforces this uniqueness.<br>

Device, Audio (Rank 21, 22)<br>

This might be related to Push and Push 2.<br>

Drum (Rank 32)<br>

Ableton has a unique drum rack plugin that is quite well-known.<br>

Sample (Rank 37)<br>

Sample refers to small recording clips that can be used for music production. Ableton has several tools to help manipulate samples.<br>

<ins>Words more from FL Studio</ins><br>

Mixer (Rank: 9)<br>

FL Studio has a rather complicated mixer and some critics have suggested that this is one of their key weakness.<br>

Beat, Pattern (Rank: 10, 15)<br>

FL Studio seems to be more associated with beat and patterns, which is associated with rhythm.

Melody, Vocal and Song (Rank 27,28,30)<br>

FL Studio seems to be more associated to songwriters that touches on melody, vocal and song.

Piano (Rank 31)<br>

This might be closely associated to FL Studio's Piano Roll.

Plugin (Rank 33)<br>

Plugin refers to extra tools that can be used in production. It seems that Plugin is more associated with Fl Studio.<br>

Help (Rank 41)<br>

FL Studio tends to attract amateur music producers and they might be more likely to seek help from the subreddit.<br>


## Conclusions and Recommendations

<ins>Conclusion</ins><br>

The findings confirmed some of the key differences between Ableton and FL Studio in terms of the features and user base.<br>

The findings confirmed on some of the key features of Ableton and FL Studio. The user base is likely to be different (e.g. songwriters for FL Studio).

<ins>Recommendations</ins><br>

Potential music producers who are thinking about Ableton should be aware of its unique workflow and supportive devices that comes with the software. It seems to be more technical than FL Studio as it seem to require a greater understanding of MIDI and likely programming. There seems to be a lot more creative involved in using samples in Ableton.<br>

Anecdotally, FL Studio seems to have a younger user base as FL STudio is known to be quite heavily pirated. If this is true, then it seems logical that there would be more requests for help. This There is some comment that FL Studio is associated with beat making and the findings has confirmed on this. The association with songwriters is an interesting information. It is also interesting that 'plugin' is more associated with FL Studio.<br>