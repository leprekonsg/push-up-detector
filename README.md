# 🤖 AI Fitness Counter

An advanced, browser-based AI fitness application that uses your webcam to count push-ups, sit-ups, squats, and jumping jacks in real-time. It leverages TensorFlow.js and the MoveNet model to provide accurate repetition counting, form analysis, and real-time feedback to help you improve your workout.

## ✨ Features

-   **🤸 Multi-Exercise Tracking:** Accurately counts repetitions for four different exercises:
    -   Push-ups
    -   Sit-ups
    -   Squats
    -   **New!** Jumping Jacks
-   **📈 Real-Time Repetition Counting:** Uses a sophisticated state machine to count reps based on joint angles and body position.
-   **🧐 Advanced Form Analysis:** Provides real-time feedback on your form, identifying common mistakes.
-   **🎨 Intuitive UI:** A clean, modern interface displays your rep count, current stage, form quality, and rep time.
-   **🗣️ Voice Feedback:** Provides audio cues for rep counts and form corrections, so you don't have to look at the screen.
-   **⚡ Performance Optimized:** Implements frame skipping and other optimizations to run smoothly on a variety of devices.
-   **🌐 Cross-Platform:** Runs entirely in the browser, requiring no installation. Works on desktops, laptops, and mobile devices.

## ⚙️ How It Works

The application captures video from your webcam and feeds it into the **MoveNet.SinglePose (Lightning)** model, which is a highly optimized pose estimation model from TensorFlow.js.

1.  **Pose Estimation:** For each frame, MoveNet identifies 17 key body points (joints like shoulders, elbows, hips, knees, etc.).
2.  **Exercise-Specific Logic:** Based on the selected exercise, a dedicated function analyzes the keypoints for that specific movement.
3.  **State Machine:** A state machine tracks whether you are in the "up" or "down" phase of an exercise. A repetition is counted only when a full transition is completed.
4.  **Form Analysis:** A separate set of functions analyzes your posture against a set of rules for good form, providing corrective feedback if you deviate.
5.  **UI Rendering:** The results are displayed in a user-friendly interface, with the skeleton drawn on the canvas and key metrics updated in real-time.

###🤸‍♂️ Jumping Jack Detection Explained

The jumping jack counter is designed to be robust by tracking both arm and leg movement.

-   **Stance Quantification:** The app measures your stance by calculating the ratio of the distance between your ankles to the distance between your shoulders. This allows it to adapt to different body sizes and camera distances.
-   **What Counts as 1 Rep:** A single repetition is counted after you successfully complete the full sequence:
    1.  **Start (Down State):** Feet together and arms by your sides.
    2.  **Movement (Up State):** You jump to a state where your feet are wide apart and your arms are raised above your shoulders.
    3.  **Completion (Return to Down State):** You return to the starting position with feet together and arms down. The count is incremented upon returning to this state.

## 💻 Tech Stack

-   **TensorFlow.js:** For running the machine learning model in the browser.
-   **MoveNet (from TensorFlow Hub):** A fast and accurate pose estimation model.
-   **HTML5/CSS3/JavaScript:** For the application structure, styling, and logic.
-   **WebRTC (getUserMedia):** To access the webcam feed.
-   **Web Audio API & SpeechSynthesis API:** For sound effects and voice feedback.

## 🚀 How to Use

1.  **Open the `index.html` file** in a modern web browser (like Chrome, Firefox, or Edge).
2.  **Grant Camera Permission:** The browser will ask for permission to access your camera. Please allow it.
3.  **Select an Exercise:** Click on one of the exercise buttons at the top right.
4.  **Position Yourself:** Stand back from the camera so the model can see the relevant parts of your body for the selected exercise.
5.  **Start Working Out!** The app will begin counting your reps and providing feedback automatically.

## 🎛️ Controls

-   **Reset Count:** Resets the counter for the current exercise to zero.
-   **Switch Camera:** Toggles between the front-facing and rear-facing cameras on mobile devices.
-   **Sound ON/OFF:** Enables or disables audio feedback.
-   **Performance:** Toggles a display that shows the current Frames Per Second (FPS) and model latency.