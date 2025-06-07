# STF AI(爱) Exercise Counter

> 🚀 **AI-Powered Fitness Companion with Real-Time Pose Detection, Voice Commands & Competitive Leaderboards**

[![Demo](https://img.shields.io/badge/Demo-Live-green.svg)](https://your-github-pages-url.github.io)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Firebase](https://img.shields.io/badge/Database-Firebase-orange.svg)](https://firebase.google.com/)
[![TensorFlow.js](https://img.shields.io/badge/AI-TensorFlow.js-yellow.svg)](https://www.tensorflow.org/js)

## 🎯 Overview

STF AI Exercise Counter is a cutting-edge fitness application that uses computer vision and AI to automatically count and analyze your exercises in real-time. With voice command support, competitive leaderboards, and professional form analysis, it's like having a personal trainer right in your browser!

### ✨ Key Features

🎥 **Real-Time Pose Detection** - Advanced AI tracks your movements with precision  
🎤 **Voice Commands** - Complete hands-free operation  
🏆 **Global Leaderboards** - Compete with others worldwide  
📊 **Form Analysis** - Real-time feedback on exercise technique  
⏱️ **60-Second Challenges** - Timed workouts for maximum motivation  
📱 **Mobile Optimized** - Works perfectly on all devices  
🎨 **Modern UI** - Stunning glassmorphism design with animations  

## 🏋️ Supported Exercises

| Exercise | Key Points Tracked | Form Analysis |
|----------|-------------------|---------------|
| **💪 Push-ups** | Elbow angles, body alignment | Shoulder level, hip alignment, straight body |
| **🔥 Sit-ups** | Torso angle, knee position | Bent knees, hand positioning |
| **🏋️ Squats** | Knee angles, back posture | Knee alignment, back straightness, feet positioning |
| **⚡ Jumping Jacks** | Arm/leg coordination | Arm height, feet spacing |

## 🚀 Quick Start

### 1. Clone & Deploy
```bash
git clone https://github.com/yourusername/stf-ai-exercise-counter.git
cd stf-ai-exercise-counter
```

### 2. Firebase Setup (Required for High Scores)

1. **Create Firebase Project:**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Create a new project
   - Enable Firestore Database

2. **Configure Database:**
   ```javascript
   // In Firebase Console > Firestore Database
   // Create collection: "highscores"
   // Security Rules:
   rules_version = '2';
   service cloud.firestore {
     match /databases/{database}/documents {
       match /highscores/{document} {
         allow read, write: if true;
       }
     }
   }
   ```

3. **Get Configuration:**
   - Project Settings → General → Your apps → Web app
   - Copy the config object

4. **Update Code:**
   ```javascript
   // Replace in the HTML file around line 750
   const firebaseConfig = {
     apiKey: "YOUR_API_KEY",
     authDomain: "YOUR_PROJECT_ID.firebaseapp.com", 
     projectId: "YOUR_PROJECT_ID",
     storageBucket: "YOUR_PROJECT_ID.appspot.com",
     messagingSenderId: "YOUR_SENDER_ID",
     appId: "YOUR_APP_ID"
   };
   ```

### 3. Deploy to GitHub Pages

1. Push to your GitHub repository
2. Go to Settings → Pages
3. Select source branch (usually `main`)
4. Your app will be live at `https://yourusername.github.io/stf-ai-exercise-counter`

## 🎮 How to Use

### Getting Started
1. **Allow camera access** when prompted
2. **Position yourself** so your full body is visible
3. **Select an exercise** from the top-right panel
4. **Start exercising** - reps are counted automatically!

### Competition Mode
1. Click **"🚀 Start Timer"** for a 60-second challenge
2. Complete as many reps as possible
3. **Enter your name** to save your score
4. **View leaderboards** to see how you rank globally

## 🎤 Voice Commands

Say these commands out loud (after clicking **"🎤 Voice Control"**):

| Command | Action |
|---------|--------|
| `"start timer"` | Begin 60-second challenge |
| `"reset"` | Reset rep counter |
| `"push ups"` | Switch to push-ups |
| `"sit ups"` | Switch to sit-ups |
| `"squats"` | Switch to squats |
| `"jumping jacks"` | Switch to jumping jacks |
| `"high scores"` | Open leaderboards |
| `"sound on/off"` | Toggle audio feedback |
| `"help"` | List all available commands |

## ⌨️ Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Space` | Start timer |
| `R` | Reset counter |
| `V` | Toggle voice commands |
| `H` | Show high scores |
| `S` | Toggle sound |
| `C` | Switch camera |
| `1-4` | Select exercise (1=Push-ups, 2=Sit-ups, 3=Squats, 4=Jumping Jacks) |
| `Enter` | Submit score (in modal) |
| `Escape` | Close modals |

## 🏆 Leaderboard System

- **Global Rankings** - Separate leaderboards for each exercise
- **Real-time Updates** - See new scores instantly
- **Achievement Celebrations** - Special effects for top 3 positions
- **Personal Highlighting** - Your scores are highlighted and celebrated
- **Ranking Notifications** - Audio feedback based on your position

## 📱 Browser Compatibility

| Feature | Chrome | Firefox | Safari | Edge |
|---------|--------|---------|--------|------|
| **Pose Detection** | ✅ | ✅ | ✅ | ✅ |
| **Voice Commands** | ✅ | ✅ | ⚠️ Limited | ✅ |
| **Camera Access** | ✅ | ✅ | ✅ | ✅ |
| **Audio Feedback** | ✅ | ✅ | ✅ | ✅ |
| **Firebase Storage** | ✅ | ✅ | ✅ | ✅ |

### Requirements
- **Camera access** (webcam required)
- **Modern browser** (ES6+ support)
- **Internet connection** (for AI model & Firebase)
- **Microphone access** (optional, for voice commands)

## 🛠️ Technical Architecture

### Core Technologies
- **TensorFlow.js** - AI pose detection using MoveNet Lightning
- **Firebase Firestore** - Real-time database for leaderboards
- **Web Speech API** - Voice command recognition
- **Canvas API** - Real-time pose visualization
- **Web Audio API** - Audio feedback and sound effects

### Performance Optimizations
- **Frame skipping** for low-end devices
- **Optimized rendering** with Canvas 2D
- **Efficient pose tracking** with confidence thresholds
- **Smart buffering** for smooth angle calculations
- **Responsive design** for all screen sizes

### Security Features
- **Input validation** for all user data
- **XSS protection** with proper sanitization
- **Firebase security rules** for data protection
- **HTTPS enforcement** for camera access

## 🎨 Customization

### Modify Exercise Thresholds
```javascript
// In the thresholds object (around line 880)
this.thresholds = {
    pushup: {
        angleDown: 90,    // Minimum angle for "down" position
        angleUp: 160,     // Minimum angle for "up" position
        minMovement: 20   // Minimum movement to register
    }
    // ... other exercises
};
```

### Customize UI Colors
```css
/* Primary accent color */
:root {
    --accent-color: #00ff88;
    --secondary-color: #00d4ff;
    --warning-color: #ffd700;
    --error-color: #ff6b6b;
}
```

### Add New Exercises
1. Add to `thresholds` object
2. Create `analyzeForm[Exercise]()` method
3. Create `detect[Exercise]()` method
4. Add to exercise selector UI
5. Update `detectExercise()` switch statement

## 📊 Analytics & Insights

The app tracks several metrics to help users improve:

- **Rep Count** - Automatic counting with high accuracy
- **Form Quality** - Real-time score (0-100%) based on technique
- **Rep Timing** - Time per repetition for consistency tracking
- **Movement Analysis** - Range of motion and smoothness
- **Session History** - Performance tracking over time

## 🔧 Troubleshooting

### Common Issues

**Camera not working:**
- Ensure HTTPS connection (required for camera access)
- Check browser permissions
- Try different browsers
- Restart browser/clear cache

**Pose detection inaccurate:**
- Ensure good lighting
- Stand 3-6 feet from camera
- Wear contrasting colors
- Check that full body is visible

**Voice commands not responding:**
- Check microphone permissions
- Ensure quiet environment
- Speak clearly and wait for indicator
- Try refreshing the page

**Scores not saving:**
- Verify Firebase configuration
- Check internet connection
- Ensure Firestore rules allow writes
- Check browser console for errors

### Performance Issues

**Low frame rate:**
- Close other browser tabs
- Lower camera resolution
- Enable performance mode
- Use newer device/browser

## 🤝 Contributing

We welcome contributions! Here's how to get started:

1. **Fork the repository**
2. **Create a feature branch:** `git checkout -b feature/amazing-feature`
3. **Make your changes** and test thoroughly
4. **Commit with clear messages:** `git commit -m 'Add amazing feature'`
5. **Push to your branch:** `git push origin feature/amazing-feature`
6. **Open a Pull Request**

### Development Guidelines
- Follow existing code style and structure
- Test on multiple browsers and devices
- Ensure accessibility compliance
- Add comments for complex algorithms
- Update documentation for new features

### Areas for Contribution
- 🏃 **New exercises** (planks, burpees, etc.)
- 🌐 **Internationalization** (multiple languages)
- 📈 **Advanced analytics** (charts, progress tracking)
- 🎮 **Gamification** (achievements, streaks)
- 🤖 **AI improvements** (better pose detection)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **TensorFlow.js Team** - For the amazing MoveNet model
- **Firebase Team** - For the real-time database platform
- **Contributors(KK and KC)** - For making this project better
- **STF Team** - For inspiration and feedback

## 📞 Support

- **Issues:** [GitHub Issues](https://github.com/yourusername/stf-ai-exercise-counter/issues)
- **Discussions:** [GitHub Discussions](https://github.com/yourusername/stf-ai-exercise-counter/discussions)

---

<div align="center">

**Made with ❤️ for the fitness community**

[⭐ Star this project](https://github.com/yourusername/stf-ai-exercise-counter) | [🐛 Report Bug](https://github.com/yourusername/stf-ai-exercise-counter/issues) | [💡 Request Feature](https://github.com/yourusername/stf-ai-exercise-counter/issues)

</div>