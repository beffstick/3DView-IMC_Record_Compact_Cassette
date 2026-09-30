# IMC RECORD Compact Cassette 3D Web Viewer & Integration Guide

This directory contains everything you need to showcase and post the interactive 3D **IMC RECORD Compact Cassette** on your website.

---

## 📁 File Structure

| File | Purpose |
| :--- | :--- |
| **`viewer_standalone.html`** | **Instant Local Testing** &bull; Fully self-contained with embedded 3D model. Simply **double-click** to open directly in Chrome/Edge without needing any local web server or CORS configuration! |
| **`index.html`** | **Web Deployment Ready** &bull; Lightweight standard web page that loads `imc_cassette.glb`. Upload this and the GLB file to any web hosting. |
| **`imc_cassette.glb`** | **3D Asset** &bull; Optimized glTF 2.0 binary asset (~1.7 MB) with physical transmission, IOR, roughness, and vector label typography. |

---

## 🚀 How to Post on Your Website

### Option 1: Standard `<model-viewer>` Component (Recommended)
1. Add Google's `<model-viewer>` script to your HTML `<head>`:
```html
<script type="module" src="https://ajax.googleapis.com/ajax/libs/model-viewer/3.5.0/model-viewer.min.js"></script>
```

2. Place the `<model-viewer>` tag anywhere in your page body:
```html
<model-viewer
  src="imc_cassette.glb"
  alt="IMC RECORD Compact Cassette"
  camera-controls
  auto-rotate
  shadow-intensity="1.2"
  style="width: 100%; height: 500px; background-color: transparent;"
  ar
  ar-modes="webxr scene-viewer quick-look">
</model-viewer>
```

---

### Option 2: Embed via `<iframe>` (WordPress, Webflow, Wix, Squarespace)
1. Upload the entire `web_viewer/` folder to your web server, AWS S3, Vercel, or Netlify.
2. In your CMS page editor, add an **Embed / HTML Block** with:
```html
<iframe 
  src="https://yourdomain.com/web_viewer/index.html" 
  width="100%" 
  height="600" 
  style="border: none; border-radius: 16px; overflow: hidden;"
  allow="camera; microphone; xr-spatial-tracking;">
</iframe>
```

---

### Option 3: React / Next.js Integration
Install the library:
```bash
npm install @google/model-viewer
```

Then create a component:
```jsx
import { useEffect } from 'react';

export default function CompactCassette3D() {
  useEffect(() => {
    import('@google/model-viewer');
  }, []);

  return (
    <div style={{ width: '100%', height: '550px' }}>
      <model-viewer
        src="/models/imc_cassette.glb"
        alt="IMC RECORD Compact Cassette"
        camera-controls
        auto-rotate
        shadow-intensity="1.2"
        style={{ width: '100%', height: '100%' }}
      />
    </div>
  );
}
```
