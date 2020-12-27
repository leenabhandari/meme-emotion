# Emotion From Tweet

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
