In this project, a dataset of 17 audio files was created, containing music, speech, or a combination of both. A corresponding text file provides labels for each file:  
- **0** for music  
- **1** for speech  
- **2** for both  

The audio files were segmented into **5-second** samples, resulting in approximately **100 segments**.  

To extract meaningful features, **Mel-Frequency Cepstral Coefficients (MFCCs)** were computed from each segment. MFCCs represent the short-term power spectrum of a sound signal and are widely used in audio processing and speech recognition.  

The extracted features, along with their labels, were used to train a **Support Vector Machine (SVM)** classifier.  

### Model Testing:  
Two test files were created to evaluate the model:  
1. The first **10 seconds** contain only speech, followed by a mix of both speech and music.  
2. The first **5 seconds** contain only music, followed by a mix of both.  

The model predicts a label for each **5-second** segment. After prediction, a post-processing step is applied to detect transitions:  
- A **sequence of 0 followed by 2 or 1** (music → both or music → speech) defines `vocal_start_time`. The final output retains the original music until this time, after which the music volume is reduced and combined with the vocal track.  
- A **sequence of 1 followed by 2 or 0** (speech → both or speech → music) defines `music_start_time`. The original vocal is preserved until this time, after which only the music continues, ensuring no vocal trace remains.  

This method effectively separates and blends the music and speech components based on model predictions.  
