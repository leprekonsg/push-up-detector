# AI Exercise Counter - Push-ups, Sit-ups & Squats (Optimized)

A web-based application that uses your device's camera and TensorFlow.js with the MoveNet pose detection model to count push-ups, sit-ups, and squats in real-time, analyze form, and provide feedback.

## ✨ Features

*   **Real-time Exercise Counting:** Accurately counts repetitions for Push-ups, Sit-ups, and Squats.
*   **Exercise Selection:** Easily switch between Push-up, Sit-up, and Squat modes.
*   **Stage Detection:** Identifies "up" and "down" (or equivalent) phases for each exercise.
*   **Angle Visualization:** Shows a progress bar representing the relevant joint angle for the current exercise (e.g., elbow for push-ups, torso for sit-ups, knee for squats).
*   **Form Quality Analysis:** Provides feedback on:
    *   **Push-ups:** Shoulder alignment, hip alignment, body straightness.
    *   **Sit-ups:** Keeping knees bent, hand positioning (discouraging hands pulling on the neck).
    *   **Squats:** Knee alignment over feet, back straightness, feet shoulder-width apart.
*   **Rep Time Tracking:** Displays the time taken for the last completed repetition.
*   **Audio Feedback:**
    *   Plays sounds for rep completion and stage changes.
    *   Speaks the count and form feedback messages.
*   **Haptic Feedback:** Provides vibration feedback on supported mobile devices for completed reps.
*   **Camera Switching:** Allows users to switch between front and rear cameras.
*   **Sound Toggle:** Option to mute/unmute audio feedback.
*   **Performance Mode:** Displays FPS and model inference latency for advanced users.
*   **Responsive Design:** Adapts to different screen sizes, making it mobile-friendly.
*   **Optimized Performance:** Uses MoveNet Lightning and frame skipping techniques for smoother operation on various devices.

## 🛠️ Technologies Used

*   **HTML5:** For the basic structure of the web page.
*   **CSS3:** For styling and user interface design.
*   **JavaScript (ES6+):** For application logic, DOM manipulation, and interactions.
*   **TensorFlow.js (`@tensorflow/tfjs`):** Core machine learning library for running models in the browser.
*   **TensorFlow.js Pose Detection Model (`@tensorflow-models/pose-detection`):** Specifically utilizes the **MoveNet SinglePose Lightning** model for efficient and fast pose estimation.
*   **Web Speech API:** For voice feedback.
*   **Web Audio API:** For sound effects.

## 🚀 Getting Started

This application is entirely client-side, meaning it runs in your web browser.

**1. Hosting:**
    *   You can host these files (HTML, CSS, JS) on any static web hosting provider (e.g., GitHub Pages, Netlify, Vercel, Firebase Hosting).
    *   **Important:** To use the camera (`getUserMedia`), the page **must be served over HTTPS**. Most hosting providers offer this by default.
    *   For local development, you can use a simple local HTTP server that supports HTTPS, or use tools like `live-server` (often available as a VS Code extension). Simply opening the `index.html` file directly in the browser (`file:///...`) might restrict camera access due to security policies.

**2. Usage:**
    *   Open the hosted URL in a modern web browser (Chrome, Firefox, Safari, Edge recommended).
    *   Grant camera permissions when prompted.
    *   The application will load the MoveNet model.
    *   Select your desired exercise (Push-ups, Sit-ups, or Squats).
    *   Position yourself according to the camera placement guidelines below.
    *   Start exercising!

## 🤳 Camera Placement for Best Results

For the most accurate detection and form analysis:

*   **General:**
    *   Position the camera so your **entire body** (or the relevant parts for the exercise) is visible in the frame during the full range of motion.
    *   Place the phone/camera on a **stable surface** to avoid shaky video.
    *   Ensure **good lighting** so the AI can easily detect your body landmarks. Avoid strong backlighting.
    *   Maintain a reasonable **distance** so you are clearly visible but not too small in the frame.
*   **Push-ups:**
    *   A **side view** is generally best to see elbow, shoulder, and hip alignment.
*   **Sit-ups:**
    *   A **side view** is crucial to see the torso angle relative to the ground, and knee bend.
*   **Squats:**
    *   A **front or slightly angled front-side view** can be good to see knee alignment, hip movement, and feet width. A pure side view can also work for knee and hip angles.

Experiment to find the best angle for your setup and chosen exercise.

## 📊 How it Works

1.  **Camera Access:** The application requests access to your device's camera.
2.  **Exercise Selection:** The user selects Push-ups, Sit-ups, or Squats. This configures the specific detection logic, thresholds, and form analysis rules.
3.  **Pose Detection:**
    *   Video frames are continuously fed into the pre-trained **MoveNet Lightning** model via TensorFlow.js.
    *   MoveNet identifies 17 key body points (joints).
4.  **Angle Calculation & Movement Tracking:**
    *   **Push-ups:** Calculates the angle of the elbows using shoulder, elbow, and wrist keypoints. Tracks vertical shoulder movement.
    *   **Sit-ups:** Calculates the torso angle relative to the horizontal (using average shoulder and hip positions). Tracks vertical shoulder movement.
    *   **Squats:** Calculates the angle of the knees using hip, knee, and ankle keypoints. Tracks vertical hip movement.
    *   Angles are smoothed over several frames to reduce jitter.
5.  **State Machine & Counting:**
    *   The application tracks the smoothed relevant angle and movement to determine if you are in the "up" or "down" (or equivalent) stage of the exercise.
    *   Exercise-specific thresholds define these stages (e.g., elbow angle for push-ups, torso angle for sit-ups, knee angle for squats).
    *   A repetition is counted when you transition correctly between stages (e.g., from "down" to "up").
    *   Audio, visual, and haptic feedback are provided.
6.  **Form Analysis:**
    *   Based on the selected exercise, specific rules are applied to keypoint positions and relative angles to assess form.
    *   For **Push-ups:** Checks for level shoulders and hips, and a straight body line.
    *   For **Sit-ups:** Checks if knees remain bent and if hands are not pulling on the head (inferred by wrist position relative to shoulders).
    *   For **Squats:** Checks knee alignment relative to ankles (avoiding excessive forward movement), back straightness (shoulder-hip alignment), and appropriate feet width.
    *   Provides a form quality score and specific feedback messages, including voice prompts.

## 🕹️ Controls

*   **Exercise Selector (Top Right):**
    *   **Push-ups Button:** Switches to push-up tracking mode.
    *   **Sit-ups Button:** Switches to sit-up tracking mode.
    *   **Squats Button:** Switches to squat tracking mode.
*   **Main Controls (Bottom Center):**
    *   **Reset Count:** Resets the counter and current state for the selected exercise.
    *   **Switch Camera:** Toggles between the front-facing and rear-facing cameras.
    *   **Sound (ON/OFF):** Enables or disables all audio feedback (beeps and voice).
    *   **Performance:** Toggles the display of FPS and model inference latency.

## 💡 Potential Improvements / Future Ideas

*   More detailed and nuanced form feedback for all exercises.
*   Saving workout history (would require backend or local storage).
*   Customizable angle thresholds and difficulty levels.
*   Tracking additional exercises.
*   Calibration routine for users of different body types or camera angles.
*   Visual cues for target angles directly on the pose.
