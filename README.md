# Identifying-balls-and-colors-in-quadrants

### Video Processing and Ball Detection

This Python script is designed to process a video file, detect quadrants within frames, and automatically identify and log changes related to colored balls placed or removed from these quadrants. Here’s a breakdown of its functionality:

#### Libraries Used:
- **OpenCV (`cv2`)**: Used for reading video frames, image processing (color conversions, contour detection), and drawing contours.
- **NumPy (`np`)**: Essential for numerical operations, array manipulations, and handling color ranges.
- **Time**: Used for timestamp generation for logging.
- **CSV**: Utilized for logging output to a structured CSV file.

#### Functionality:
1. **Color Identification**: 
   - Defines HSV color ranges for specific ball colors (e.g., green, orange, yellow).
   - Uses these ranges to create masks for detecting colored balls in the video frames.

2. **Frame Processing**:
   - Converts each frame from BGR to HSV color space for better color segmentation.
   - Applies predefined masks to isolate specific colors (e.g., red) using `cv2.inRange`.
   - Finds contours in these masked areas to detect quadrilateral shapes, potentially representing areas where balls are placed.

3. **Quadrant Detection and Monitoring**:
   - Divides detected quadrilateral regions (where balls might be placed) into four quadrants.
   - Monitors changes in each quadrant by comparing the number of non-zero pixels (indicating ball presence) between consecutive frames.
   - Determines if a ball has been placed or removed based on predefined thresholds (`500` non-zero pixel difference).

4. **Logging**:
   - Logs each detected event (ball placed or removed) along with the quadrant number, detected ball color, action (placed or removed), and timestamp.
   - Accumulates these logs in a list during video processing.

5. **CSV Output**:
   - After video processing is complete, writes the accumulated log entries to a CSV file (`output_log.csv`).
   - The CSV file includes columns for quadrant number, ball color, action (placed or removed), and timestamp, making it easy to analyze and visualize the data.

6. **User Interface**:
   - Displays the processed frames in a window (`Processed Frame`) in real-time.
   - Pressing 'q' quits the video processing loop and closes the display window.

#### Usage:
- Replace `'input_video.mp4'` with the path to your input video file.
- Define `output_csv` to specify the path where the log will be saved as a CSV file.
- Run the script to process the video and generate the CSV log.

#### Dependencies:
- Ensure you have Python installed with necessary libraries (`cv2`, `numpy`, `time`, `csv`).
- Recommended to use in environments supporting graphical displays (like local machines or cloud-based services with GUI support).

