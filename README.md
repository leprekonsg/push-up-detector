# AI Push-Up Counter (Optimized)

A web-based application that uses your device's camera and TensorFlow.js with the MoveNet pose detection model to count push-ups in real-time, analyze form, and provide feedback.

## ✨ Features

*   **Real-time Push-Up Counting:** Accurately counts repetitions.
*   **Stage Detection:** Identifies "up" and "down" phases of a push-up.
*   **Elbow Angle Visualization:** Shows a progress bar representing the current elbow angle.
*   **Form Quality Analysis:** Provides feedback on:
    *   Shoulder alignment
    *   Hip alignment
    *   Body straightness
*   **Rep Time Tracking:** Displays the time taken for the last completed repetition.
*   **Audio Feedback:** Plays sounds for rep completion and stage changes.
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
   *   Position yourself according to the camera placement guidelines below.
   *   Start doing push-ups!

## 🤳 Camera Placement for Best Results

For the most accurate push-up detection and form analysis:

*   **Position the camera to your SIDE.** This allows the AI to clearly see the movement of your shoulders, elbows, hips, and knees.
*   Ensure your **entire body** is visible in the frame, from head to feet if possible, especially during the full range of motion.
*   Place the phone/camera on a **stable surface** to avoid shaky video.
*   Ensure **good lighting** so the AI can easily detect your body landmarks. Avoid strong backlighting.
*   Maintain a reasonable **distance** so you are clearly visible but not too small in the frame.

## 📊 How it Works

1.  **Camera Access:** The application requests access to your device's camera.
2.  **Pose Detection:**
    *   Video frames are continuously fed into the pre-trained **MoveNet Lightning** model via TensorFlow.js.
    *   MoveNet identifies 17 key body points (joints).
3.  **Angle Calculation:** The angle of the elbow is calculated using the coordinates of the shoulder, elbow, and wrist keypoints.
4.  **State Machine:**
    *   The application tracks the smoothed elbow angle to determine if you are in the "up" or "down" stage of a push-up.
    *   Thresholds are used to define these stages (e.g., `< 90°` for down, `> 160°` for up).
    *   Vertical shoulder movement is also considered to ensure actual push-up motion.
5.  **Counting & Feedback:** A push-up is counted when you transition from a "down" state (elbows bent significantly) to an "up" state (elbows extended). Audio and visual feedback are provided.
6.  **Form Analysis:**
    *   Checks for level shoulders and hips.
    *   Assesses if the body (shoulders to hips) remains relatively straight.
    *   Provides a form quality score and specific feedback messages.

## 🕹️ Controls

*   **Reset Count:** Resets the push-up counter and current state.
*   **Switch Camera:** Toggles between the front-facing and rear-facing cameras on your device.
*   **Sound (ON/OFF):** Enables or disables audio feedback.
*   **Performance:** Toggles the display of FPS and model latency.

## 💡 Potential Improvements / Future Ideas

*   More detailed form feedback (e.g., head position, hand placement).
*   Saving workout history (would require backend or local storage).
*   Different exercise tracking.
*   Customizable angle thresholds.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!
1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

## 📄 License

This project is licensed under the MIT License - see the `LICENSE.md` file for details (you would need to create this file if you want to specify a license, MIT is a common permissive one).

---

*This README was generated based on the provided HTML, CSS, and JavaScript code for the AI Push-Up Counter.*