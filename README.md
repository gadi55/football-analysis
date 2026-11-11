# Football Analysis — Cloud Demo

This fork provides a **lightweight Streamlit cloud entry point** so that users can upload short arbitrary football MP4 clips without manually supplying missing `models/best.pt`. The original full pipeline remains in `main.py` and `football_analysis/` for local/advanced use, but is **not** the pipeline executed by the hosted Streamlit UI.

## Deploy to Streamlit Community Cloud

1. Open https://share.streamlit.io/deploy?repository=gadi55%2Ffootball-analysis&branch=main&mainModule=app.py
2. If prompted, sign in with GitHub and select repository `gadi55/football-analysis`, branch `main`, file `app.py`.
3. Deploy; allow a few minutes for the first installation and automatic YOLO weight download.
4. Upload a short MP4 (ideally 10–20 seconds, maximum 60 seconds); click **Analyze possession**.

## Hosted functionality

- Automatic `yolo11n.pt` download on first inference (COCO person/sports-ball classes)
- Player bounding boxes, ball location, two approximate jersey-colour clusters
- Approximate possession and possession-change timestamps
- CSV timeline, events, annotated H.264 MP4 (ffmpeg)
- Optional custom trusted football-trained YOLO weights upload with configurable class IDs

## Accuracy and limits

**Not verified on semi-professional matches.** This is a basic proof of concept. Default COCO sports-ball detection can miss tiny footballs; team colours can confuse referees, substitutes and spectators. Nearest-player possession is a heuristic, not a reliable ground-truth turnover detector. Team A/B labels are arbitrary. No player-ID tracking, speed, distance, or advanced pitch heatmaps are promised by the hosted app; those belong to the original advanced pipeline and require additional configuration and model weights.

## Advanced original pipeline

The original `main.py` still expects `models/best.pt` and its dependencies. It is **not** configured as the default hosted entry point. This fork deliberately prioritises a first-launch cloud demo.

## Licenses

Check the upstream repository and Ultralytics model/software licensing before commercial use.
