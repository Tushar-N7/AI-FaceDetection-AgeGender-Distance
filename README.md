Here's a project description you can use for your GitHub repository:

---

# Real-Time Face Detection, Gender & Age Prediction, and Distance Measurement with Email Alerts

## Overview
This project uses **OpenCV** and **deep learning models** to detect faces in real-time, predict gender and age, and calculate the distance of faces from the camera. Additionally, the system sends **email alerts** if the number of detected males exceeds the number of detected females, making it suitable for surveillance or security applications.

## Features
- **Face Detection:** Uses a pre-trained deep learning model to detect faces in video frames.
- **Gender & Age Prediction:** Identifies the gender and estimates the age of each detected face.
- **Distance Calculation:**
  - **Face-to-Camera Distance:** Estimates how far a face is from the camera using known parameters.
  - **Face-to-Face Distance:** Calculates the real-world distance between two detected faces.
- **Email Notifications:** Automatically sends an alert email if more males are detected than females.
- **Real-Time Processing:** Works with both built-in and external cameras (e.g., DroidCam).

## Technologies Used
- **OpenCV** for face detection and image processing.
- **Deep Learning** models for gender and age prediction.
- **SMTP** (via Python's `smtplib`) for sending email notifications.
- **Math** library for distance calculations.

## Prerequisites
1. **Python Libraries:**
   - `opencv-python`
   - `math`
   - `smtplib`
   - `email`

   Install them using:
   ```bash
   pip install opencv-python
   ```

2. **Pre-trained Models:**
   - Download the following models and place them in the project directory:
     - `opencv_face_detector.pbtxt`
     - `opencv_face_detector_uint8.pb`
     - `age_deploy.prototxt`
     - `age_net.caffemodel`
     - `gender_deploy.prototxt`
     - `gender_net.caffemodel`

3. **Camera Setup:**
   - This script is configured for **DroidCam** as an external camera (set to `camera_index = 1`). Modify `camera_index` based on your setup.

4. **Email Configuration:**
   - The script uses Gmail's SMTP server to send alerts. Make sure to:
     - Enable **"Less Secure Apps"** in your Gmail settings or use an **App Password**.
     - Update the email credentials in the script (`sender_email`, `sender_password`, `receiver_email`).

## How It Works
1. The system captures frames from the camera.
2. Detected faces are highlighted, and their gender and age are predicted.
3. The script calculates:
   - Distance of each face from the camera.
   - Distance between two detected faces (if there are exactly two).
4. If the number of males exceeds the number of females and surpasses the previous male count, an alert email is sent.
5. Results are displayed in real-time with bounding boxes, labels, and distance measurements.

## Code Explanation

- **Face Detection (`highlightFace`):**  
  Converts the frame into a blob, processes it through a deep learning model, and returns detected face coordinates.

- **Distance Calculations:**  
  - `calculate_distance()` computes the distance from the camera using the known width of the face and focal length.
  - `calculate_distance_between_faces()` computes pixel distance between two face centers and converts it to real-world distance based on calibration.

- **Email Alert (`send_email`):**  
  Sends an email when more males are detected than females.

## Customization
- **Camera Index:**  
  Change `camera_index = 1` to `0` or another index if using a different camera.
  
- **Alert Conditions:**  
  Modify the alert logic in the loop if you want to change when emails are triggered.

- **Calibration:**  
  Adjust `KNOWN_WIDTH`, `FOCAL_LENGTH`, and `reference_pixel_distance` for more accurate distance measurements based on your camera and setup.

## Example Output
- Bounding boxes around faces with gender and age labels.
- Distance from the camera displayed below each detected face.
- Lines connecting two faces with the real-world distance shown between them.
- Console outputs for the number of detected males and females.

## Screenshots
*(Add screenshots of the face detection with age, gender, and distance displayed.)*

## Future Improvements
- Integrate **face recognition** for identifying known individuals.
- Enhance distance calibration for multi-camera setups.
- Add a database to store detected faces and event logs.
- Implement **SMS notifications** or **push notifications** for alerts.

## License
This project is open-source and available under the [MIT License](LICENSE).

---

Feel free to modify or expand on this description depending on your project goals! Let me know if you need additional sections like setup instructions, example images, or troubleshooting tips. 🚀
