# NLPTranscriptSearch (Whisper + TF-IDF + LDA + Gradio)

This project builds a searchable dashboard for an **introductory Machine Learning video course** (40+ videos). It creates **transcripts**, **normalizes text**, extracts **key phrases**, assigns **topics**, and provides a **Gradio dashboard** where users can search by topic or key phrases to quickly find relevant videos.

## What it does

- Pulls course videos from an **Amazon S3 bucket**
- Converts `.mp4` videos to `.wav` audio (via **ffmpeg**)
- Transcribes audio to text using **OpenAI Whisper**
- Normalizes/cleans the transcripts (NLP preprocessing)
- Extracts **key phrases** using **TF-IDF**
- Extracts **topics** using **LDA (Latent Dirichlet Allocation)**
- Builds an interactive **Gradio dashboard** to search and display matching videos (with video links)

## Project workflow

1. **View & download videos** from S3 into a local `videos/` folder  
2. **Convert videos → audio** (`.mp4` → `.wav`) and store in `audios/`  
3. **Transcribe audio** using Whisper → saves `movies.csv`  
4. **Normalize text** → saves `normalized_movies.csv`  
5. **Key phrase extraction (TF-IDF)** → saves `keyphrased_tf.csv`  
6. **Topic modeling (LDA)** + assign topics → saves `video_topics.csv`  
7. **Search dashboard (Gradio)** to query by phrases/topics and show results

## Outputs (generated files)

| File | Description |
|------|-------------|
| `movies.csv` | Raw transcripts per video |
| `normalized_movies.csv` | Cleaned/normalized transcripts |
| `keyphrased_tf.csv` | Extracted TF-IDF key phrases |
| `video_topics.csv` | Topic assignment per video (topic id per transcript) |

## Tech stack

- Python
- AWS S3 (`boto3`) for storing/downloading videos
- `ffmpeg` for media conversion
- **Whisper** (`whisper`) for transcription
- NLP utilities: `nltk`, `contractions`, regex cleaning
- Topic + phrase extraction: `scikit-learn` (TF-IDF, LDA)
- Dashboard UI: **Gradio**

## Repository contents

- `Md Abrar_1273832.ipynb` — main notebook with the entire pipeline
- `Md Abrar_1273832.pdf` — exported notebook PDF
- (Optional folders created when you run)
  - `videos/` — downloaded `.mp4` files
  - `audios/` — converted `.wav` files
  - `csv/` or project root — generated `.csv` outputs

## Setup

### 1) Clone the repo
```bash
git clone <YOUR_REPO_URL>
cd <YOUR_REPO_FOLDER>
