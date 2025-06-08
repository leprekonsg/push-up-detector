# STF AI(爱) Exercise Counter

An intelligent AI-powered fitness application that counts and analyzes your exercises in real-time using computer vision and pose detection. Get instant feedback on your form, track your progress, and compete on leaderboards!

## 🌟 Features

### 🏋️ Exercise Detection
- **Push-ups**: Elbow angle tracking with form analysis
- **Sit-ups**: Torso angle monitoring and movement validation
- **Squats**: Knee angle detection with posture feedback
- **Jumping Jacks**: Full-body movement coordination tracking

### 🎯 Real-time Form Analysis
- **Visual Progress Bars**: Live angle and movement feedback
- **Form Quality Scoring**: Percentage-based form assessment (0-100%)
- **Voice Coaching**: Real-time audio feedback for form corrections
- **Movement Validation**: Ensures proper range of motion for rep counting

### ⏱️ Performance Tracking
- **60-Second Timer Challenges**: Structured workout sessions
- **Rep Counting**: Accurate exercise repetition tracking
- **Performance Metrics**: Rep time, form quality, and movement analysis
- **Progress Visualization**: Real-time visual feedback and statistics

### 🔊 Voice Controls & Audio
- **Voice Commands**: Hands-free operation with speech recognition
- **Audio Feedback**: Count announcements and form coaching
- **Sound Effects**: Audio cues for rep validation and timing
- **Voice Activation**: "Say 'start timer' to begin a workout challenge!"

### 🏆 Leaderboards & Competition
- **Firebase Integration**: Cloud-based score storage and retrieval
- **Anonymous Authentication**: Seamless user experience without signup
- **Exercise-Specific Rankings**: Separate leaderboards for each exercise type
- **Personal Achievement Tracking**: Highlight your best scores and rankings

### 📱 Mobile-Optimized Design
- **Responsive UI**: Tabbed bottom panel for organized controls
- **Touch Gestures**: Swipe to expand/minimize interface panels
- **Collapsible Stats**: Minimize stats panel to maximize camera view
- **Performance Optimization**: Adaptive frame rates and reduced particles on mobile

## 🚀 Getting Started

### Prerequisites
- Modern web browser with camera support
- Webcam or device camera
- Internet connection for Firebase features
- Microphone (optional, for voice commands)

### Installation
1. Clone the repository or download the HTML file
2. Set up Firebase (optional, for leaderboards):
   - Create a Firebase project at [console.firebase.google.com](https://console.firebase.google.com)
   - Enable Firestore Database and Authentication
   - Replace Firebase configuration placeholders in the code
3. Open the HTML file in a web browser
4. Allow camera and microphone permissions when prompted

### Firebase Setup (Optional)
```javascript
// Replace these placeholders in the code:
window.firebaseConfig = {
    apiKey: "your-api-key",
    authDomain: "your-project.firebaseapp.com",
    projectId: "your-project-id",
    storageBucket: "your-project.appspot.com",
    messagingSenderId: "123456789",
    appId: "your-app-id"
};
```

## 🎮 How to Use

### Basic Controls
1. **Select Exercise**: Choose from push-ups, sit-ups, squats, or jumping jacks
2. **Position Yourself**: Stand/position yourself in front of the camera
3. **Start Timer**: Click "🚀 Start Timer" or say "start timer" for 60-second challenge
4. **Exercise**: Perform your chosen exercise with proper form
5. **View Results**: See your count, form quality, and save your score

### Mobile Interface
- **Exercises Tab**: Select your workout type
- **Controls Tab**: Timer, reset, and leaderboard access
- **Settings Tab**: Voice controls, camera switching, sound toggle, sign out
- **Swipe Gestures**: Swipe up/down on bottom panel to expand/minimize

### Voice Commands
- "**start timer**" - Begin 60-second challenge
- "**reset**" - Reset counter and timer
- "**push ups**" - Switch to push-up mode
- "**sit ups**" - Switch to sit-up mode
- "**squats**" - Switch to squat mode
- "**jumping jacks**" - Switch to jumping jack mode
- "**high scores**" - Show leaderboards
- "**sound on/off**" - Toggle audio
- "**help**" - List available commands

### Keyboard Shortcuts
- **Spacebar**: Start timer
- **R**: Reset counter
- **V**: Toggle voice commands
- **H**: Show leaderboards
- **S**: Toggle sound
- **C**: Switch camera
- **1-4**: Quick exercise selection
- **T**: Toggle panels (mobile)
- **Escape**: Close modals

## 🏗️ Technical Architecture

### AI & Computer Vision
- **TensorFlow.js**: Machine learning framework for browser-based AI
- **MoveNet**: Google's pose detection model for real-time body tracking
- **Pose Detection**: 17-point skeletal tracking with confidence scoring
- **Angle Calculation**: Mathematical analysis of joint angles and movement

### Performance Optimizations
- **WebGL Backend**: GPU acceleration for AI model inference
- **Frame Skipping**: Adaptive frame rate based on device performance
- **Canvas Optimization**: Efficient rendering with minimal redraw operations
- **Memory Management**: Proper cleanup and resource management

### Data Storage
- **Firebase Firestore**: NoSQL cloud database for leaderboards
- **Anonymous Authentication**: User tracking without account creation
- **Real-time Sync**: Live leaderboard updates across devices
- **Data Security**: User ID-based score validation

### Browser Compatibility
- **Modern Browsers**: Chrome, Firefox, Safari, Edge (latest versions)
- **WebRTC**: Camera access and video streaming
- **Web Audio API**: Sound generation and speech synthesis
- **Speech Recognition**: Voice command processing (Webkit/Chrome)

## 📊 Exercise Analysis Details

### Push-ups
- **Primary Metric**: Elbow angle (90° down, 160° up)
- **Form Checks**: Shoulder alignment, hip alignment, body straightness
- **Movement Validation**: Shoulder vertical movement tracking
- **Quality Factors**: Range of motion, body posture, timing

### Sit-ups
- **Primary Metric**: Torso angle (30° down, 80° up)
- **Form Checks**: Knee bend, hand position, torso movement
- **Movement Validation**: Shoulder vertical displacement
- **Quality Factors**: Controlled movement, proper knee angle

### Squats
- **Primary Metric**: Knee angle (130° down, 160° up)
- **Form Checks**: Knee-foot alignment, back straightness, foot positioning
- **Movement Validation**: Hip vertical movement
- **Quality Factors**: Depth, knee tracking, posture

### Jumping Jacks
- **Primary Metrics**: Stance width, arm position
- **Form Checks**: Arm elevation, foot separation, coordination
- **Movement Validation**: Synchronized arm and leg movement
- **Quality Factors**: Full range of motion, timing, coordination

## 🎨 UI/UX Features

### Visual Design
- **Cyberpunk Aesthetic**: Dark theme with neon accents
- **Gradient Animations**: Dynamic color transitions and effects
- **Particle System**: Animated background elements
- **Glassmorphism**: Frosted glass effects with backdrop blur

### Responsive Design
- **Mobile-First**: Optimized for touch devices and small screens
- **Adaptive Layout**: Dynamic sizing based on screen dimensions
- **Touch-Friendly**: Large buttons and gesture support
- **Accessibility**: Keyboard navigation and focus management

### Real-time Feedback
- **Live Progress Bars**: Visual representation of exercise metrics
- **Color-Coded Status**: Green (good), yellow (warning), red (error)
- **Pulse Animations**: Visual emphasis on rep completion
- **Stage Indicators**: Current exercise phase display

## 🔧 Customization

### Exercise Thresholds
```javascript
this.thresholds = {
    pushup: {
        angleDown: 90,      // Minimum angle for "down" position
        angleUp: 160,       // Maximum angle for "up" position
        minMovement: 20,    // Minimum movement for validation
        angleLabel: 'Elbow Angle'
    },
    // ... other exercises
};
```

### Performance Settings
```javascript
// Adjust frame skipping for performance
this.maxFrameSkip = 2;  // Higher = lower quality, better performance

// Confidence threshold for pose detection
this.CONFIDENCE_THRESHOLD = 0.3;  // 0.0 - 1.0
```

## 🐛 Troubleshooting

### Common Issues
- **Camera not working**: Check browser permissions and ensure HTTPS
- **Low performance**: Reduce browser zoom, close other tabs, enable hardware acceleration
- **Voice commands not working**: Check microphone permissions and browser support
- **Firebase errors**: Verify configuration and internet connection

### Browser Requirements
- **Camera API**: Required for video input
- **WebGL**: Required for AI processing
- **Speech Recognition**: Optional, for voice commands
- **Local Storage**: Used for temporary data

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Make your changes
3. Test across different devices and browsers
4. Submit a pull request

### Areas for Contribution
- Additional exercise types
- Improved form analysis algorithms
- Enhanced mobile experience
- Performance optimizations
- Accessibility improvements

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- **TensorFlow.js Team**: For the amazing machine learning framework
- **Google MoveNet**: For the pose detection model
- **Firebase**: For cloud infrastructure and authentication
- **Modern Web APIs**: For camera, audio, and speech capabilities

## 📞 Support

For issues, questions, or feature requests:
- Create an issue in the GitHub repository
- Check browser console for error messages
- Ensure camera and microphone permissions are granted
- Verify internet connection for Firebase features

---

**Made with ❤️ and AI** - Empowering fitness through technology!