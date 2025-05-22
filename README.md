# Video Summarization Pipeline (Colab Notebook)

[![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1ksE4h0SYXFK4n0oWt7D-a2k-hFhkRFxD?usp=sharing)
![GPU](https://img.shields.io/badge/GPU-T4/L4%20Recommended-orange)

An end-to-end video summarization system that combines:
- Audio transcription (Whisper)
- Text summarization (TF-IDF)
- Visual keyframe extraction (ResNet50)
- Highlight video generation

## Notebook Instructions

### 1. Setup Requirements
- **Runtime**: Use Google Colab with:
  - **GPU**: T4 (slower) or L4 (recommended)
  - **High-RAM**: Enable to avoid crashes
- **Storage**: Minimum 20GB free space

### 2. File Changes Needed
Replace this line in the notebook:
```python
filename = "/content/drive/MyDrive/ve/sports.mp4" # Change to your video path
```

## 3. Pipeline Steps

### Audio Processing:
- Transcribe audio using Whisper  
- Segment into sentences with timestamps  
- Save transcript as `transcript.csv`  

### Text Summarization:
- Score sentences using TF-IDF  
- Select top sentences (50% of video duration)  
- Save as `top_sentences.csv`  

### Visual Analysis:
- Extract keyframes using ResNet50  
- Refine with scene change detection  
- Save keyframes as JPG + CSV  

### Video Generation:
- Create clips from selected sentences  
- Merge into final summary video  
- Output as `final_summary.mp4`  

## Runtime Notes
⚠️ **Potential Issues**:
- Crashes on long videos (>15 mins) without High-RAM  
- T4 GPU may be slow for HD videos  
- MoviePy may show warnings (can be ignored)  

## Output Files
- `corrected_transcript.csv` - Full transcript with timestamps  
- `keyframes/` - Extracted keyframe images  
- `final_summary.mp4` - Generated highlight video  

## Customization
Modify these variables as needed:
```python
model_size = "base"  # Whisper model size (tiny, base, small, medium, large)
summary_ratio = 0.5  # Target summary length (0.5 = 50%)
hist_threshold = 0.6 # Scene change sensitivity (0-1)
```
## Project Status

This is an active research/development project. All code is provided as-is without warranty.  
For usage inquiries, please open an issue.

[⭐ Star this project](https://github.com/dubeypushplata/Audio-Video-Summarizer.git) to stay updated on improvements!
---
❤️ **Enjoy this project?** Help others discover it by [giving a star](https://github.com/dubeypushplata/Audio-Video-Summarizer.git)!
