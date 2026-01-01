# 🪐 Interactive Solar System Simulation

![Three.js](https://img.shields.io/badge/Three.js-Black?style=for-the-badge&logo=three.js&logoColor=white)
![WebGL](https://img.shields.io/badge/WebGL-Red?style=for-the-badge&logo=webgl&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

A real-time, interactive 3D simulation of the Solar System developed using **Three.js** and **WebGL**. This project demonstrates fundamental Computer Graphics principles such as Hierarchical Modeling (Scene Graphs), Texture Mapping, Lighting, and Raycasting interaction.

## 🚀 Live Demo
**[Click here to view the simulation live!](https://hamzayuruk.github.io/interactive-solar-system/)**

## ✨ Key Features

* **🔭 Real-Time Rendering:** Smooth 60 FPS animation loop using `requestAnimationFrame`.
* **☀️ Dynamic Lighting & Shadows:** The Sun acts as a central point light source, casting realistic shadows on planets (e.g., eclipses).
* **🌍 Hierarchical Modeling (Scene Graph):** Planets orbit the Sun, and moons orbit planets using a parent-child `Object3D` structure.
* **🖱️ Raycasting Interaction:** Click on any planet to smoothly focus the camera on it using vector interpolation.
* **🪐 Custom Geometry:** Saturn's rings are rendered using `RingGeometry` with double-sided materials and transparency.
* **🎛️ UI Controls:**
    * **Zoom Slider:** Dynamic camera distance adjustment.
    * **Speed Control:** Accelerate or decelerate the simulation time.
    * **Target Selector:** Dropdown menu to quick-travel to any celestial body.

## 🛠️ Technical Implementation

### 1. Scene Graph (Hierarchical Modeling)
Instead of calculating complex trigonometry for every object's position, the project utilizes a Scene Graph architecture.
* **Sun** (Root)
    * **OrbitGroup** (Invisible Pivot) -> Rotates around Y-axis
        * **PlanetMesh** (Child) -> Rotates around own axis
            * **MoonGroup** -> **MoonMesh**

### 2. Raycasting (Mouse Interaction)
The project converts 2D screen coordinates (mouse click) into a 3D ray in the world space to detect intersections with planets.

```javascript
// Raycasting Logic
raycaster.setFromCamera(mouse, camera);
const intersects = raycaster.intersectObjects(clickableObjects);
if (intersects.length > 0) {
    focusOnObject(intersects[0].object);
}
```
3. Textures & Materials
High-resolution equirectangular textures are mapped onto spheres using MeshStandardMaterial. This allows the planets to react physically to the light source (Sun), creating realistic day/night cycles.

💻 Installation & Usage
Clone the repository:

Bash

git clone [https://github.com/hamzayuruk/interactive-solar-system.git](https://github.com/hamzayuruk/interactive-solar-system.git)
Navigate to the project folder.

Important: Since this project uses ES Modules and texture loading, you need to run it on a local server (to avoid CORS errors).

VS Code Users: Right-click index.html and select "Open with Live Server".

Python Users: Run python -m http.server in the terminal.
