# 🎬 Web Accessibility: Audio & Video Content

## 🎯 Key Elements for Accessible Multimedia

### 1. Captions & Subtitles
* **Captions:** Text version of spoken words *plus* important non-verbal sounds (music, laughter), synchronized with the video. Essential for deaf or hard-of-hearing users.
* **Subtitles:** Text translations of spoken dialogue for users who don't understand the language. Also useful for people watching in noisy or quiet environments.

#### Implementation via HTML `<track>` Element
```html
<video controls src="video.mp4">
  <track
    src="captions.vtt"
    kind="captions"
    srclang="en"
    label="English"
  />
</video>

<audio controls src="audio.mp3">
  <track
    src="captions.vtt"
    kind="captions"
    srclang="en"
    label="English"
  />
</audio>