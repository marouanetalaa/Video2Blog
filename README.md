# Video2Blog

This API is designed to generate a blog from a conference video. The process involves two main steps:

1. **Audio Transcription**: The audio from the video is extracted and transcribed using an enhanced version of Whisper (faster-whisper). The output is a series of speech chunks with their timestamps (start and end) and the accuracy of transcription for each chunk.

2. **Visual Processing**: The visual part of the video is processed to extract the slides used during the conference, along with their respective timestamps.

## Features

- **Slide Extraction**: The API detects slide transitions in the video by splitting it into frames using OpenCV. It then calculates the mean squared error between consecutive frames and extracts the peaks in the histogram using a threshold (determined by the Otsu method or an asymmetric Gaussian distribution).

- **Context Chunking**: The extracted slides and their timestamps are used to split the transcription into chunks of the same context. This is important because language models have a fixed token limit.

- **Slide Content Extraction**: The content of the slides is also extracted and added to the prompts sent to the language model to improve the blog output.

- **Language Model Integration**: Each context chunk, along with the corresponding slide content, is processed by a language model to generate a formatted HTML section.

- **Blog Assembly**: The HTML sections are combined to create the final blog.

## Installation

1. Clone the repository:

```bash
git clone https://github.com/your-repo/blog-generation-api.git
