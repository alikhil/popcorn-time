# 🍿 Popcorn Timer

A smart web application that listens to your microwave popcorn pops and suggests the optimal time to turn it off, maximizing popped corn while preventing burning.

## Features

- 🎤 **Real-time Audio Detection**: Uses your device's microphone to detect popcorn pops
- 📊 **Visual Feedback**: Live audio visualization and pop indicators
- ⏱️ **Smart Timing**: Intelligent algorithm suggests when to stop based on pop frequency
- 📱 **Mobile-Friendly**: Works on modern Android and iOS browsers
- 🔒 **Privacy-First**: All processing happens locally in your browser
- 🚫 **No Dependencies**: Pure JavaScript, no external libraries or server required

## How It Works

The app uses the Web Audio API to analyze audio from your microphone in real-time:

1. **Audio Capture**: Captures audio through your device's microphone
2. **Pop Detection**: Analyzes audio amplitude to detect characteristic popcorn "pop" sounds
3. **Pattern Analysis**: Tracks the frequency and timing of pops
4. **Smart Suggestions**: Recommends stopping when:
   - Pops slow to 2-3 seconds apart (optimal)
   - No pops detected for 4+ seconds (burning warning)

## Usage

1. Open `index.html` in a modern web browser
2. Place your device near the microwave
3. Click "Start Listening" and allow microphone access
4. Start your popcorn in the microwave
5. Watch the real-time pop detection
6. Follow the app's recommendation to stop at the optimal time

## Browser Compatibility

The app uses standard Web APIs supported by modern browsers:

- ✅ **Chrome/Edge**: 74+ (Android & Desktop)
- ✅ **Safari**: 11+ (iOS & macOS)
- ✅ **Firefox**: 63+ (Android & Desktop)
- ✅ **Samsung Internet**: 11+

### Required Browser Features

- Web Audio API (MediaStream, AudioContext, AnalyserNode)
- Canvas API for visualization
- ES6+ JavaScript support

## Technical Details

### Algorithm

The pop detection algorithm uses:
- **RMS (Root Mean Square)** calculation for audio amplitude
- **Threshold detection** (configurable threshold of 150)
- **Cooldown period** (200ms) to prevent double-counting
- **Rate analysis** over 10-second windows

### Recommendations Logic

- **Active Popping** (>2 pops/sec): Keep waiting
- **Slowing Down** (0.5-2 pops/sec): Get ready
- **Optimal Time** (>2.5s since last pop): Stop now
- **Danger Zone** (>4s since last pop): Stop immediately!

### Privacy & Security

- No data is sent to any server
- All audio processing happens locally
- Microphone access only while actively listening
- No storage of audio data

## Development

The application is a single HTML file with embedded CSS and JavaScript:

- **No build process required**
- **No dependencies to install**
- **Works offline** after initial load
- **No server needed**

Simply open `index.html` in a browser or serve it with any static file server.

## Tips for Best Results

1. **Positioning**: Place your phone/device 1-2 feet from the microwave
2. **Environment**: Minimize background noise for better detection
3. **Microwave**: Works best with standard household microwaves
4. **Sensitivity**: The app auto-calibrates to your environment
5. **Safety**: Always stay near the microwave when using this app

## Troubleshooting

**Microphone not working?**
- Ensure you've granted microphone permission
- Check that no other app is using the microphone
- Try refreshing the page

**Not detecting pops?**
- Move device closer to the microwave
- Reduce background noise
- Ensure microwave door is closed properly

**False detections?**
- Move device slightly further away
- Minimize other noise sources

## License

MIT License - Feel free to use and modify as needed.

## Contributing

This is a simple single-file application. Contributions welcome for:
- Algorithm improvements
- UI/UX enhancements
- Browser compatibility fixes
- Better pop detection logic