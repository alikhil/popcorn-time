# 🍿 Popcorn Timer

A smart web application that listens to your microwave popcorn pops and suggests the optimal time to turn it off, maximizing popped corn while preventing burning.

## Features

- 🎤 **Real-time Audio Detection**: Uses your device's microphone to detect popcorn pops
- 📊 **Visual Feedback**: Live audio visualization and pop indicators with frequency spectrum heat map
- ⏱️ **Smart Timing**: Intelligent algorithm suggests when to stop based on pop frequency
- 📱 **Mobile-Friendly**: Works on modern Android and iOS browsers
- 🔒 **Privacy-First**: All processing happens locally in your browser
- 🚫 **No Dependencies**: Pure JavaScript, no external libraries or server required
- 🔧 **Debug Mode**: Upload and analyze audio recordings for testing

## Quick Start

1. Open `index.html` in a modern web browser
2. Click "Start Listening" and allow microphone access
3. Place your device near the microwave
4. Start your popcorn
5. Follow the app's recommendations

## Debug Mode

Enable debug mode to test with pre-recorded audio:

1. Toggle the "Debug Mode" switch
2. Upload an audio file (MP3, WAV, OGG, M4A, WebM)
3. (Optional) Set start time in seconds
4. (Optional) Enable/disable audio playback
5. Click "Start Debug Session"
6. Check browser console (F12) for detailed logs

### Sample Audio

A sample audio file is included in `samples/score-4.5-a-bit-burned.m4a` for testing.

### Troubleshooting

Use `analyzer.html` for detailed audio analysis:
- Load sample or custom audio files
- View real-time frequency spectrum
- See detailed detection logs
- Monitor energy levels and peak frequencies

## How It Works

The app uses the Web Audio API to analyze audio from your microphone in real-time:

1. **Audio Capture**: Captures audio through your device's microphone
2. **Frequency Analysis**: Uses FFT to analyze frequency spectrum (1-8 kHz range)
3. **Pop Detection**: Detects characteristic popcorn "pop" sounds using dual threshold system
4. **Pattern Analysis**: Tracks the frequency and timing of pops
5. **Smart Suggestions**: Recommends stopping when:
   - Pops slow to 2-3 seconds apart (optimal)
   - No pops detected for 4+ seconds (burning warning)

## Algorithm Details

### Pop Detection
- **Frequency Range**: 1kHz - 8kHz (where popcorn pops occur)
- **Dual Threshold**: Average energy + peak amplitude detection
- **Adaptive Threshold**: 112 (first 3 pops) → 140 (normal)
- **Cooldown**: 150ms to prevent double-counting
- **Console Logging**: Detailed energy, frequency, and timing information

### Visualization
- Frequency spectrum heat map (last 5 seconds)
- Color-coded intensity (blue → red)
- Pop markers with 🍿 icons
- Waveform overlay

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

## Privacy & Security

- No data is sent to any server
- All audio processing happens locally
- Microphone access only while actively listening
- No storage of audio data

## Development

The application consists of:
- `index.html` - Main application (1000+ lines, pure JavaScript)
- `analyzer.html` - Troubleshooting tool for audio analysis
- `samples/` - Sample audio files for testing
- `SAMPLE_AUDIO_INSTRUCTIONS.md` - Testing guide

**No build process required** - just open in a browser!

## Tips for Best Results

1. **Positioning**: Place your phone/device 1-2 feet from the microwave
2. **Environment**: Minimize background noise for better detection
3. **Microwave**: Works best with standard household microwaves
4. **Sensitivity**: The app auto-calibrates to your environment
5. **Safety**: Always stay near the microwave when using this app

## Troubleshooting

### Pops Not Being Detected?

1. **Check Console Logs** (F12):
   - Look for "📊 Audio level" messages every second
   - Check if "Avg" and "Max" values are above 50
   - Verify peak frequencies are in 1-8kHz range

2. **Use the Analyzer Tool**:
   - Open `analyzer.html` in your browser
   - Load your audio file or the sample
   - View detailed energy levels and frequencies
   - Check if threshold needs adjustment

3. **Common Issues**:
   - **Low audio levels** (Avg < 50): Increase volume or move closer
   - **Wrong frequency**: Verify sounds are in 1-8kHz range
   - **Threshold too high**: Current threshold is 140 (adaptive 112)

### Microphone Not Working?

- Ensure you've granted microphone permission
- Check that no other app is using the microphone
- Try refreshing the page

### False Detections?

- Move device slightly further away
- Minimize other noise sources
- Background noise may trigger detection

## License

MIT License - Feel free to use and modify as needed.

## Contributing

Contributions welcome for:
- Algorithm improvements
- UI/UX enhancements
- Browser compatibility fixes
- Better pop detection logic