# AEDAC
Audio Event Detection and Classification

## Introduction
Repository for EE608V course project (Machine Learning in Signal Processing, Fall 2020, IIT Kanpur), on Audio Event Detection and Audio event classification for 10 different audios - 'air_conditioner', 'car_horn', 'children_playing', 'dog_bark', 'drilling', 'engine_idling', 'gun_shot', 'jackhammer','siren', 'street_music'

## Tasks
  #### Task 1: 
  Given an audio file corresponds to a single event, find out that event.

  Evaluation: Accuracy
  
  Return audio event detected. E.g. street_music
  
  #### TASK 2: 
  Given an audio file contains a sequence of events occurring one after the other, find out that sequence of events. A sequence can contain at least 1 and at most 5 events.

  Evaluation: Edit distance
  
  Return sequence of classes separated by hyphen "-". E.g. street_music-dog_bark-engine_idling 
  Labels would not repeat consecutively, e.g., street_music-dog_bark-dog_bark will be labeled as street_music-dog_bark

## Approach Used
 #### Task 1
The approach followed by us is as follows:
1. Firstly, we removed all repeated audio files so that the model does not overfit.
2. We saw that almost all the temporal information was contained in about 40 frames by
hearing audios of each classes.
3. So, we decided to only use 40 frames as input to the neural network.
4. We converted each audio file into spectrogram using librosa library.
5. We split the spectrogram into several files, each file containing 40 frames in time axis.
6. Trained several CNN architectures as we intuitively felt CNN can capture the information
well. We did not train the networks for too long to prevent overfitting. We stopped at the
point after which the difference in train and dev set accuracy started increasing.
7. Then , we simply applied a majority voting (among all such 40 frame outputs) for predictions
on the test set provided.

The best pair of (train accuracy, validation accuracy), we achieved over this dataset is (65,52)
We used a different validation dataset taken from internet sources. It was however not at all used in training the model.
Other approach used were to simply fed the CNN network with whole spectrogram but the validation accuracy from that approach was coming out to be only near 30%.

 #### Task 2
1. Since the audio file was directly concatenated, we thought to reuse the model trained in Task 1 as a sub routine.
2. The subroutine gives us labels for every 40 frames.
3. We then clean the output by removing noise and keeping only the predictions which repeat for sufficient(here, used 3) number of 40 frames. I.e., only those predictions are kept which are surrounded by same prediction.
4. Then, we finally remove consecutive same labels and give the final predicted sequence of audio events!

For example,
[3,3,3,2,1,3,3,3,5,5,5,5,4,5,5,5,5,7,7,7,7,7,7] is first cleaned to [3,3,5,5,5,5,7,7,7,7]
Then finally [3,3,5,5,5,5,7,7,7,7] is reduced to [3,5,7] and converted to label encoding and given as output.

## Schematic Diagram 
<img width="1005" alt="Screenshot 2021-10-07 at 3 26 28 PM" src="https://user-images.githubusercontent.com/45767605/136362625-7042270a-9220-49c2-b412-7596f0ac67ea.png">



## References
1. AED talk by Justin Salamon https://www.youtube.com/watch?v=zvccOFz2KxI&ab_channel=SpeechandAudiointheNortheast%28SANE%29 
2. Application of AED in Amazon Alexa: https://www.youtube.com/watch?v=-nKelNVVblM&ab_channel=Amazonre%3AMAR
