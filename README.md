In this project a dataset of 17 audio file have been createds. Some of them containing music, some speech and some both.
there is a text file that has labels of the fies in each line. 0 for music, 1 for speech and 2 for both.

The audio files are then segmented to 5 seconds samples leading to around 100 samples at the end.

The MFCC features are extracted from the audio segments.
MFCC, or Mel Frequency Cepstral Coefficients, are a set of coefficients that represent the short-term power spectrum of a sound signal. They are widely used in audio processing and speech recognition.

The features and the labels are given to SVM or Support Vector Machine to train the model.

To test the model a test file is created cosisting of two input channel of music and vocal in a way that at the first 10 sec its only vocal then the rest is both.
Another test is the first 5 sec is only music then both.

The model predict the label for each 5 sec and after that a search is done for a sequence of 0 followed by 2 or 1 which means music then both. For making the result the original music is used until the time of vocal_start_time and then music is lowered then combined with the vocal.

For the other case we have a music_start_time which is a sequence of 1 followed by 2 or 0, the original vocal is used until the time of music_start_time and then the music until the end. So no trace of vocal at that time.
