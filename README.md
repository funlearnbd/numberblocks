# 🔢 FunLearnBD Number Learning Game

## 📖 Overview

A comprehensive number learning game for kids (ages 2-8) featuring **Numberblocks** - fun block characters that help children learn numbers 1-10 in three languages: English, Bangla, and Arabic.

## 🎮 Game Modes

### 1. **📚 Learn Mode**
- View each number (1-10) with its Numberblock
- Hear pronunciation in selected language
- Navigate between numbers
- Perfect for introduction to numbers

### 2. **👆 Count Mode**
- Count interactive dots
- Tap each dot to count
- Visual feedback for correct counting
- Builds number sense

### 3. **🔍 Find Number Mode**
- Given a number, find the matching Numberblock
- Multiple choice with visual blocks
- Tests number recognition

### 4. **🎯 Quiz Mode**
- See a Numberblock, identify the number
- Multiple choice answers
- Progressive difficulty

### 5. **✏️ Trace Mode**
- Practice writing numbers
- Touch/mouse drawing on canvas
- Visual guide for proper formation
- Clear and retry as needed

### 6. **🎲 Sequence Mode**
- Put numbers in correct order
- Drag to arrange (or click)
- Tests understanding of number sequence

## 🌍 Languages Supported

- **🇬🇧 English** (0-9, zero through ten)
- **🇧🇩 Bangla** (০-৯, শূন্য থেকে দশ)
- **🇸🇦 Arabic** (٠-٩, صفر إلى عشرة)

## 🖼️ How to Add Your Numberblock Images

### Current State
The game currently uses **placeholder SVG images** that display the number with a colored background. This allows the game to work immediately while you prepare your actual Numberblock images.

### Integration Steps

#### Step 1: Prepare Your Images

Create 10 images (numbers 1-10) with these specifications:

**File Format:** PNG with transparent background (recommended)
- Also supports: JPG, SVG, WebP

**Size:** 200x200px to 500x500px (recommended)
- The game auto-scales images
- Square aspect ratio works best
- Transparent backgrounds look cleaner

**Naming Convention:**
```
numberblock-1.png
numberblock-2.png
numberblock-3.png
...
numberblock-10.png
```

Or use a naming system that works for you!

#### Step 2: Place Images in Project

Create an `images` folder next to your HTML file:

```
your-project/
├── number-learning-game.html
└── images/
    ├── numberblocks/
    │   ├── 1.png
    │   ├── 2.png
    │   ├── 3.png
    │   └── ... (up to 10.png)
```

#### Step 3: Update Image Paths in Code

Open `number-learning-game.html` and find the `getNumberblockImage()` function (around line 450):

**Replace this:**
```javascript
function getNumberblockImage(num) {
    // Current placeholder code
    return `data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" width="200" height="200"><rect width="200" height="200" fill="%23${getNumberColor(num)}"/><text x="100" y="120" font-size="80" fill="white" text-anchor="middle" font-weight="bold">${num}</text></svg>`;
}
```

**With this:**
```javascript
function getNumberblockImage(num) {
    // Use your actual Numberblock images
    return `images/numberblocks/${num}.png`;
}
```

**That's it!** The game will now use your images.

### Alternative Image Locations

#### Option A: Using a CDN or Cloud Storage
```javascript
function getNumberblockImage(num) {
    return `https://your-cdn.com/numberblocks/number-${num}.png`;
}
```

#### Option B: Different naming convention
```javascript
function getNumberblockImage(num) {
    return `assets/blocks/block_${num}_color.png`;
}
```

#### Option C: Using different formats per number
```javascript
function getNumberblockImage(num) {
    const formats = {
        1: 'svg', 2: 'png', 3: 'png', 4: 'svg',
        5: 'png', 6: 'png', 7: 'svg', 8: 'png',
        9: 'png', 10: 'svg'
    };
    return `images/numberblocks/${num}.${formats[num]}`;
}
```

## 🚀 Quick Start

### Option 1: Direct Open
1. Download `number-learning-game.html`
2. Double-click to open in browser
3. Start playing immediately!

### Option 2: Local Server (Recommended)
```bash
# Navigate to project folder
cd your-project-folder

# Python 3
python -m http.server 8000

# Or Python 2
python -m SimpleHTTPServer 8000

# Open browser to: http://localhost:8000
```

### Option 3: Live Server (VS Code)
1. Install "Live Server" extension in VS Code
2. Right-click on HTML file
3. Select "Open with Live Server"

## 🎨 Customization

### Colors
Edit the CSS color scheme in the `<style>` section:

```css
/* Primary colors */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Button colors */
.btn-primary { background: #667eea; }
.btn-success { background: #4ecdc4; }
.btn-danger { background: #ff6b6b; }
```

### Sounds
The game uses the Web Audio API for sounds. To add custom sounds:

1. Replace the `playSound()` function with audio files:

```javascript
function playSound(type) {
    const audio = new Audio(`sounds/${type}.mp3`);
    audio.play();
}
```

### Difficulty Levels
Adjust the number range by modifying:

```javascript
// Change from 10 to your desired maximum
const maxNumber = 20; // Now supports 1-20

// Then update the random number generation
const target = Math.floor(Math.random() * maxNumber) + 1;
```

## 📱 Mobile Compatibility

The game is **fully mobile-responsive** and supports:

- ✅ Touch gestures for drawing (Trace mode)
- ✅ Touch-friendly buttons
- ✅ Responsive layout (works on phones and tablets)
- ✅ PWA-ready (can be installed on device)

### Make it a PWA (Progressive Web App)

Add this to your HTML `<head>`:

```html
<link rel="manifest" href="manifest.json">
```

Create a `manifest.json`:

```json
{
  "name": "FunLearnBD Number Learning",
  "short_name": "NumberGame",
  "start_url": ".",
  "display": "standalone",
  "background_color": "#667eea",
  "theme_color": "#667eea",
  "description": "Learn numbers 1-10 in multiple languages",
  "icons": [{
    "src": "icon-192.png",
    "sizes": "192x192",
    "type": "image/png"
  }]
}
```

## 🎯 Features

### ✨ Interactive Learning
- Click on Numberblocks to hear pronunciation
- Visual and audio feedback
- Gamified learning experience

### 🏆 Progress Tracking
- Score system
- Level progression
- Streak counter for motivation

### 🎨 Beautiful UI
- Gradient backgrounds
- Smooth animations
- Confetti celebrations!
- Child-friendly design

### 🔊 Audio Support
- Text-to-Speech for number pronunciation
- Supports multiple languages
- Fun sound effects

## 🔧 Technical Details

### Browser Compatibility
- Chrome/Edge (Recommended)
- Firefox
- Safari
- Opera

**Minimum Requirements:**
- JavaScript enabled
- Canvas support (for trace mode)
- Web Audio API (for sounds)

### File Size
- **HTML + CSS + JS:** ~25KB
- **With images (10 Numberblocks):** ~200-500KB total
- Loads instantly on modern connections

### No Dependencies
- Pure vanilla JavaScript
- No frameworks required
- No external libraries
- Works offline after first load

## 📋 Image Checklist

Before going live, ensure you have:

- [ ] 10 Numberblock images (1-10)
- [ ] Transparent backgrounds (PNG)
- [ ] Consistent size (200-500px)
- [ ] Good quality (not pixelated)
- [ ] Matching your color scheme
- [ ] Properly named files
- [ ] Correct file paths in code

## 🐛 Troubleshooting

### Images Not Showing?
1. Check file paths are correct
2. Verify image files are in the right folder
3. Check browser console (F12) for errors
4. Ensure correct file extensions

### Audio Not Working?
1. Click/interact with page first (browser security)
2. Check browser permissions
3. Test with different browsers
4. Volume is turned up

### Touch Drawing Not Working?
1. Ensure touch events are enabled
2. Test on actual mobile device
3. Check if canvas is properly sized

## 🎓 Educational Benefits

This game helps children:
- **Number Recognition** - Visual identification
- **Counting Skills** - One-to-one correspondence
- **Number Formation** - Writing practice
- **Sequencing** - Understanding order
- **Multilingual** - Numbers in 3 languages

## 📄 License

Free to use for educational purposes.
Part of the FunLearnBD educational project.

## 🤝 Support

For issues or questions about the FunLearnBD project, please refer to the main project documentation.

---

## 🚀 Next Steps

1. **Add your Numberblock images** (follow guide above)
2. **Test on mobile devices**
3. **Customize colors/sounds** (optional)
4. **Share with kids and get feedback!**

---

**Made with ❤️ for FunLearnBD**

Happy Learning! 🎉
