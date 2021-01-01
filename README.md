# Intelligent Meme Generator

This repository contains the source code for iHACK hackathon organized by Hackerearth and Sentient.io
## Problem


The current social media campaigns for promotion of any films include trailers, posters on social media and celebrities tweeting and posting about it. Although this works and creates an online awareness, this strategy does not make use of the full social media potential. Memes are the current generation's way of communicating and sharing information. And, they go viral pretty easily. Some media houses have tried using memes to promote their ad campaigns. But presently, all the work of taking out images and possibly best dialogs is manual.

## Solution
By leveraging sentiment.io APIs and an ML based model, we plan to build a solution which would create meme automatically and intelligently. The user only needs to submit a video clip URL and rest is taken care of. This would help in achieving the brand awareness and would eventually improve revenue.
The system uses current news clips to generate movie based memes.

## Implementation
Steps:
1. A movie trailer URL is taken as input. The video is downloaded and processed. Text is separated and timestamps are taken for the dialogs. This will generate smaller video clips for each dialog. Sentient.io API is used here.
2. A model is pretrained based on sentiment140 dataset. This calculated values for emotions – Anger, Joy, Fear and Sadness.
3. Current news is fetched based on category and country. For every dialog in the previous step, emotion is calculated. Same is done for news clippings. The best match of news and dialogs is used to generate memes.
4. Final output is a set of memes for each dialog in the movie trailer. (getMeme() function in MEME-generator notebook)


## Steps to reproduce results
**NOTE: Skip to Generate Meme step directly to get final output i.e. with pretrained model and sample video(Infinity war trailer)**

### Train model:
1. Run "Fetch Tweets" notebook. In the search Query, run for all 4 emotions namely - #anger, #joy, #fear, #sadness
2. Download sentiment140 dataset from kaggle. Run Train sentiment Analysis notebook. This produces tokenizer.pickle and gru_model.h5 files.
3. Run Validate API data to get dataset.csv
4. Run Train Emotion Recognition notebook to get model_weights.h5

### Get video: (Sentient.io APIs)
![Flowchart](https://i.ibb.co/PNCkFXq/Sentinent-Flowchart.jpg)
1. There is Video download notebook(Some APIs didnt give expected result). Run ASR with voice detection notebook.
2. Run video splitting notebook. For now, we have hardcoded the start time values, end time values and the dialogues based on the Avengers Infinity War trailer (which is the videoplayback.mp4 file).
This generates small clips of dialogs.

Update:
Added functionality to get dialogs and split video automatically for all Youtube videos with captions. (MEME Generator dashboard notebook)
Python packages - moviepy 1.0.3

### Generate meme-

1. Open MEME - generator notebook.
2. Run step 3 to fetch latest news articles. Here, you can change country(in,us,etc.) and category(antertainment,business,etc.).
3. Finally getMeme() function generates the memes. It uses the helper function generateFinalOutput() to combine prediction and video clips.

### Update - Use Meme Generator Dashboard notebook for GUI interface

Final output sample- https://drive.google.com/file/d/1ce0qI_mr57b1ycVQ0zIaKu_kIX5IoMKD/view?usp=sharing

*Note - Here are some challenges faced - Youtube downloader gave "Video not found" error. Video to Audio API, could not access file path. ASR API worked successfully but the result accuracy was not sufficient for models. Manual intervention and hardcoding was done here. The news API response required cleaning and yet the content was insufficient for accurate training. Adding text on video would go out of frame. Overally accuracy was hampered due to insufficient training.*
