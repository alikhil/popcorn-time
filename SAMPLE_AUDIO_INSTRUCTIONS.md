# Sample Audio File Instructions

## How to Add Your Sample Audio

1. Download the sample audio file from your source
2. Place it in this repository root directory
3. Name it `sample-popcorn.m4a` (or any supported format)
4. The app will work with this file in debug mode

## Testing with Sample Audio

1. Open `index.html` in your browser
2. Enable Debug Mode toggle
3. Click "Choose File" and select your sample audio
4. (Optional) Set start time if you want to skip to a specific part
5. (Optional) Toggle "Play audio during analysis" checkbox
6. Click "Start Debug Session"
7. Open browser console (F12) to see detailed detection logs

## What to Look For in Console Logs

The console will show:
- `📊 Audio level` - Real-time audio levels every second
  - **Avg**: Average energy in 1-8kHz range
  - **Max**: Peak amplitude
  - **Peak freq**: Frequency where maximum amplitude occurs
  - **Time**: Elapsed time since start

- `🍿 POP #X!` - When a pop is detected
  - **Energy**: Average energy that triggered detection
  - **Peak**: Maximum amplitude
  - **Freq**: Peak frequency of the pop
  - **Time**: When the pop occurred
  - **Threshold**: Current detection threshold

## Troubleshooting

If pops are not being detected:
1. Check console logs - look at the "Avg" and "Max" values
2. If values are consistently low (< 50), your audio might be quiet
3. Try adjusting the threshold in code (currently 140)
4. Verify sample rate matches (44100Hz or 48000Hz typical)
5. Ensure the audio file contains actual popcorn popping sounds in the frequency range 1-8kHz

## Sample Audio Requirements

- **Format**: MP3, WAV, OGG, M4A, WebM, AAC
- **Content**: Recording of actual popcorn popping
- **Quality**: Clear audio without excessive background noise
- **Duration**: Any length (app will analyze from start or specified time)
