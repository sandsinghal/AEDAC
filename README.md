# AEDAC
Audio Event Detection and Classification

## Introduction
Repository for CS698X course project (Topics in Probabilistic Modeling and Inference, Winter 2021, IIT Kanpur), on Audio Event Detection and Audio event classification for 10 different audios - dog bark, children playing, AC noise, etc. 

## Tasks
  Task 1: Given an audio file corresponds to a single event, find out that event.

  Evaluation: Accuracy
  Return audio event detecte. E.g. street_music
  
  TASK 2: Given an audio file contains a sequence of events occurring one after the other, find out that sequence of events. A sequence can contain at least 1 and at most 5 events.

  Evaluation: Edit distance
  Return sequence of classes separated by hyphen "-". E.g. street_music-dog_bark-engine_idling 
  Labels would not repeat consecutively, e.g., street_music-dog_bark-dog_bark will be labeled as street_music-dog_bark

## Model

## Running the models


## References
(educational) AED talk by Justin Salamon https://www.youtube.com/watch?v=zvccOFz2KxI&ab_channel=SpeechandAudiointheNortheast%28SANE%29 
(interesting) Application of AED in Amazon Alexa: https://www.youtube.com/watch?v=-nKelNVVblM&ab_channel=Amazonre%3AMAR
