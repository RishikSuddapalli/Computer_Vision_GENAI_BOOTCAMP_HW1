# Video Brightness and Time Classification

## Overview
This script processes a video to calculate the brightness of each frame and classifies it into one of three categories: **Day**, **Night**, or **Sunrise/Sunset**. The average brightness value and classification are displayed on the top-left corner of the video. The output is saved as a new annotated video file.

---

## Features
- Calculates the average brightness for each frame.
- Categorizes frames into:
  - **Day**: Brightness above a threshold.
  - **Sunrise/Sunset**: Intermediate brightness levels.
  - **Night**: Low brightness.
- Adds a visible overlay on each frame with brightness and classification information.
- Saves the processed video to a specified output file.

---

## Requirements
To run this script, you need:
- Python 3.10 or later
- OpenCV library
- NumPy library

Install the required libraries using pip:
```bash
pip install opencv-python numpy
```

---

## How to Use
1. Place your input video file in a known location (e.g., `timelapse/Time_Lapse.mkv`).
2. Update the script to point to your input video file and set the desired output path.
3. Run the script using Python:
   ```bash
   python video_brightness_overlay.py
   ```

### Script Parameters
- `video_path` (str): Path to the input video file.
- `output_path` (str): Path to save the annotated output video file.

Example usage:
```python
process_video_with_brightness_and_time("timelapse/Time_Lapse.mkv", "output_video.avi")
```

---

## Code Explanation
### Key Steps:
1. **Read Video:** Opens the input video using OpenCV's `VideoCapture`.
2. **Frame Brightness Calculation:**
   - Converts each frame to grayscale.
   - Computes the average brightness using NumPy.
3. **Classification:**
   - Compares brightness values with predefined thresholds to classify as Day, Sunrise/Sunset, or Night.
4. **Overlay Text:**
   - Adds a black rectangle and overlay text showing brightness and classification.
5. **Save Output:** Writes each annotated frame to the output video file.

### Adjustable Thresholds:
- `brightness_day_threshold`: Frames with brightness above this value are classified as **Day**.
- `brightness_sunrise_sunset_threshold`: Frames with brightness between this value and `brightness_day_threshold` are classified as **Sunrise/Sunset**.

---

## Output
The output video will:
- Display brightness and classification on each frame.
- Retain the original video resolution and frame rate.

### Example Output:
For a video file `timelapse/Time_Lapse.mkv`, the processed output will be saved as `output_video.avi`. Each frame will have an overlay like:
```
Brightness: 43.301%, Sunrise/Sunset: 16.396%, Night:40.302
```

---

## Troubleshooting
1. **Error: Unable to open video file.**
   - Ensure the input video file path is correct.
   - Check if the file exists and is accessible.
2. **Missing Libraries:**
   - Install missing dependencies using `pip`.

---

## License
This script is open-source and free to use and modify. Attribution is appreciated.

