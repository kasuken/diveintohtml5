# Quick Reference Guide 🦄✨

A quick lookup for all the magical features covered in this course!

## 📑 Table of Contents

- [Feature Detection](#feature-detection)
- [Canvas & Graphics](#canvas--graphics)
- [Media](#media)
- [Location](#location)
- [Storage](#storage)
- [Offline & PWA](#offline--pwa)
- [Forms](#forms)
- [Background Processing](#background-processing)
- [Real-Time Communication](#real-time-communication)
- [User Interface](#user-interface)
- [HTTP Requests](#http-requests)

---

## Feature Detection

### Check if Feature Exists
```javascript
// Modern approach - no libraries needed!
if ('geolocation' in navigator) { /* supported */ }
if ('serviceWorker' in navigator) { /* supported */ }
if ('Notification' in window) { /* supported */ }

// Canvas
const canvas = document.createElement('canvas');
if (canvas.getContext && canvas.getContext('2d')) { /* supported */ }

// Check permissions
const permission = await navigator.permissions.query({ name: 'geolocation' });
console.log(permission.state); // 'granted', 'denied', 'prompt'
```

**📖 Learn more:** [detect.html](detect.html)

---

## Canvas & Graphics

### 2D Canvas
```javascript
const canvas = document.getElementById('myCanvas');
const ctx = canvas.getContext('2d');

// Set canvas size (not CSS!)
canvas.width = 800;
canvas.height = 600;

// Draw rectangle
ctx.fillStyle = '#9b59b6';
ctx.fillRect(10, 10, 100, 50);

// Draw circle
ctx.beginPath();
ctx.arc(100, 100, 50, 0, Math.PI * 2);
ctx.fill();

// Animation
function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  // Draw things
  requestAnimationFrame(animate);
}
animate();
```

### WebGL & 3D
```javascript
// Using Three.js
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, width/height, 0.1, 1000);
const renderer = new THREE.WebGLRenderer();

const geometry = new THREE.BoxGeometry(1, 1, 1);
const material = new THREE.MeshBasicMaterial({ color: 0x9b59b6 });
const cube = new THREE.Mesh(geometry, material);
scene.add(cube);

function animate() {
  requestAnimationFrame(animate);
  cube.rotation.x += 0.01;
  renderer.render(scene, camera);
}
```

**📖 Learn more:** [canvas.html](canvas.html) • [webgl.html](webgl.html)

---

## Media

### Video
```javascript
const video = document.querySelector('video');

// Play (returns Promise!)
await video.play();

// Events
video.addEventListener('play', () => console.log('Playing'));
video.addEventListener('ended', () => console.log('Ended'));

// Properties
video.currentTime = 30; // Jump to 30 seconds
video.volume = 0.5;     // 50% volume
```

### Audio
```javascript
const audio = new Audio('song.mp3');
await audio.play();
```

**📖 Learn more:** [video.html](video.html)

---

## Location

### Geolocation
```javascript
// Get current position
const position = await new Promise((resolve, reject) => {
  navigator.geolocation.getCurrentPosition(resolve, reject);
});

const { latitude, longitude, accuracy } = position.coords;

// Watch position
const watchId = navigator.geolocation.watchPosition(
  (pos) => console.log(pos.coords),
  (err) => console.error(err),
  { enableHighAccuracy: false } // Save battery!
);

// Stop watching
navigator.geolocation.clearWatch(watchId);
```

**📖 Learn more:** [geolocation.html](geolocation.html)

---

## Storage

### localStorage
```javascript
// Save
localStorage.setItem('key', 'value');
localStorage.setItem('user', JSON.stringify({ name: 'Sparkles' }));

// Get
const value = localStorage.getItem('key');
const user = JSON.parse(localStorage.getItem('user'));

// Remove
localStorage.removeItem('key');
localStorage.clear(); // Remove all

// Check existence
if (localStorage.getItem('key')) { /* exists */ }
```

### IndexedDB (use library!)
```javascript
// Using idb-keyval
import { get, set, del } from 'idb-keyval';

await set('unicorn', { name: 'Sparkles', power: 9000 });
const unicorn = await get('unicorn');
await del('unicorn');
```

**📖 Learn more:** [storage.html](storage.html)

---

## Offline & PWA

### Service Worker
```javascript
// Register
if ('serviceWorker' in navigator) {
  const registration = await navigator.serviceWorker.register('/sw.js');
}

// In sw.js
const CACHE = 'v1';

self.addEventListener('install', (e) => {
  e.waitUntil(
    caches.open(CACHE).then(cache => cache.addAll(['/']))
  );
});

self.addEventListener('fetch', (e) => {
  e.respondWith(
    caches.match(e.request).then(r => r || fetch(e.request))
  );
});
```

### Manifest
```json
{
  "name": "My App",
  "short_name": "App",
  "start_url": "/",
  "display": "standalone",
  "background_color": "#fff",
  "theme_color": "#9b59b6",
  "icons": [
    { "src": "/icon-192.png", "sizes": "192x192", "type": "image/png" }
  ]
}
```

**📖 Learn more:** [offline.html](offline.html)

---

## Forms

### Modern Input Types
```html
<input type="email" required>
<input type="url">
<input type="tel">
<input type="number" min="1" max="100">
<input type="range" min="0" max="9000">
<input type="date">
<input type="color">
<input type="file" accept="image/*" multiple>
```

### Validation
```javascript
const form = document.querySelector('form');

// Check validity
if (form.checkValidity()) {
  // Valid!
}

// Show validation UI
form.reportValidity();

// Custom validation
input.setCustomValidity('Custom error message');
```

**📖 Learn more:** [forms.html](forms.html)

---

## Background Processing

### Web Workers
```javascript
// Create worker
const worker = new Worker('worker.js');

// Send message
worker.postMessage({ task: 'process', data: [1,2,3] });

// Receive message
worker.onmessage = (e) => {
  console.log('Result:', e.data);
};

// Terminate
worker.terminate();

// In worker.js
self.onmessage = (e) => {
  const result = e.data.data.map(x => x * 2);
  self.postMessage(result);
};
```

**📖 Learn more:** [webworkers.html](webworkers.html)

---

## Real-Time Communication

### WebSockets
```javascript
const socket = new WebSocket('wss://example.com/chat');

socket.onopen = () => {
  console.log('Connected!');
  socket.send(JSON.stringify({ type: 'join', name: 'Sparkles' }));
};

socket.onmessage = (event) => {
  const data = JSON.parse(event.data);
  console.log('Message:', data);
};

socket.onerror = (error) => console.error(error);
socket.onclose = () => console.log('Disconnected');
```

**📖 Learn more:** [websockets.html](websockets.html)

---

## User Interface

### Drag & Drop
```javascript
// Make draggable
element.draggable = true;

element.ondragstart = (e) => {
  e.dataTransfer.setData('text/plain', element.id);
};

// Drop zone
dropZone.ondragover = (e) => e.preventDefault();

dropZone.ondrop = (e) => {
  e.preventDefault();
  const id = e.dataTransfer.getData('text/plain');
  const element = document.getElementById(id);
  dropZone.appendChild(element);
};
```

### Notifications
```javascript
// Request permission
const permission = await Notification.requestPermission();

// Show notification
if (permission === 'granted') {
  new Notification('Hello!', {
    body: 'This is a notification',
    icon: '/icon.png'
  });
}

// Service Worker notification (persistent)
const registration = await navigator.serviceWorker.ready;
await registration.showNotification('Title', {
  body: 'Message',
  actions: [
    { action: 'open', title: 'Open' },
    { action: 'close', title: 'Close' }
  ]
});
```

**📖 Learn more:** [dragdrop.html](dragdrop.html) • [notifications.html](notifications.html)

---

## HTTP Requests

### Fetch API
```javascript
// GET request
const response = await fetch('/api/data');
const data = await response.json();

// POST request
const response = await fetch('/api/data', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({ name: 'Sparkles' })
});

// With error handling
try {
  const response = await fetch('/api/data');
  if (!response.ok) throw new Error(`HTTP ${response.status}`);
  const data = await response.json();
} catch (error) {
  console.error('Fetch failed:', error);
}

// Abort request
const controller = new AbortController();
setTimeout(() => controller.abort(), 5000);

const response = await fetch('/api/data', {
  signal: controller.signal
});
```

**📖 Learn more:** [fetch.html](fetch.html)

---

## Common Patterns

### Async/Await
```javascript
// Modern async pattern
async function loadData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    throw error;
  }
}

// Multiple parallel requests
const [users, posts, comments] = await Promise.all([
  fetch('/api/users').then(r => r.json()),
  fetch('/api/posts').then(r => r.json()),
  fetch('/api/comments').then(r => r.json())
]);
```

### Error Handling
```javascript
// Always use try-catch
try {
  localStorage.setItem('key', 'value');
} catch (e) {
  console.error('Storage blocked:', e);
}

// Check before using
if ('geolocation' in navigator) {
  // Use geolocation
} else {
  // Provide fallback
}
```

### Feature Detection
```javascript
// Progressive enhancement
if ('serviceWorker' in navigator) {
  // Register service worker
} else {
  // App still works, just without offline
}
```

---

## 🎯 Best Practices

### General
1. ✅ Always check feature support
2. ✅ Use modern async/await syntax
3. ✅ Handle errors gracefully
4. ✅ Provide fallbacks
5. ✅ Test on real devices
6. ✅ Consider mobile users
7. ✅ Respect user privacy
8. ✅ Use HTTPS in production

### Performance
1. ✅ Use requestAnimationFrame for animations
2. ✅ Debounce/throttle expensive operations
3. ✅ Use Web Workers for heavy computations
4. ✅ Optimize images and assets
5. ✅ Lazy load when possible
6. ✅ Cache API responses

### Security
1. ✅ Never trust user input
2. ✅ Validate on server too
3. ✅ Use HTTPS
4. ✅ Don't store sensitive data in localStorage
5. ✅ Use Content Security Policy
6. ✅ Sanitize user-generated content

---

## 📚 Resources

- [MDN Web Docs](https://developer.mozilla.org/)
- [Can I Use](https://caniuse.com/)
- [Web.dev](https://web.dev/)
- [Three.js Docs](https://threejs.org/docs/)
- [Socket.IO](https://socket.io/)

---

<div align="center">

**🦄 Happy Coding! ✨**

*This quick reference covers the essentials. Visit individual chapter pages for in-depth explanations and examples!*

</div>
