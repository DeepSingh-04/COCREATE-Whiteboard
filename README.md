# 🧩 COCREATE Whiteboard
[![Ask DeepWiki](https://devin.ai/assets/askdeepwiki.png)](https://deepwiki.com/DeepSingh-04/COCREATE-Whiteboard)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
![React](https://img.shields.io/badge/Frontend-React.js-blue)
![Socket.io](https://img.shields.io/badge/Realtime-Socket.io-lightgrey)
![TailwindCSS](https://img.shields.io/badge/Styling-TailwindCSS-blueviolet)
![Next.js](https://img.shields.io/badge/Framework-Next.js-orange)

> A real-time collaborative digital whiteboard designed for seamless teamwork and creativity — whether you’re brainstorming ideas, planning projects, teaching remotely, or diagramming complex workflows. COCREATE Whiteboard transforms remote collaboration into an engaging, visual experience, bridging the gap between physical whiteboards and distributed teams.

---

## 🖌️ Overview
**COCREATE Whiteboard** is a powerful, web-based application that enables multiple users to collaborate on a shared digital canvas in real-time. Imagine a virtual whiteboard where every stroke of the pen, shape drawn, or note added appears instantly for all participants, fostering dynamic idea exchange without the constraints of location or physical tools.

At its core, this project leverages modern web technologies to deliver a responsive, intuitive interface that prioritizes user experience. Whether you're a design team sketching wireframes, educators illustrating concepts during online classes, or project managers mapping out timelines, COCREATE Whiteboard adapts to your needs. The application supports an infinite canvas for unrestricted creativity, integrated chat for contextual discussions, and export options to preserve your work.

Developed with a focus on scalability and performance, it handles multiple concurrent users efficiently, ensuring low-latency updates even in high-traffic sessions. This open-source tool is perfect for developers looking to extend its functionality or integrate it into larger ecosystems, such as learning management systems or agile project tools.

Key differentiators include its lightweight footprint (no heavy dependencies), cross-browser compatibility, and mobile-responsive design, making it accessible on desktops, tablets, and even smartphones for on-the-go collaboration.

---

## 🌟 Key Features
COCREATE Whiteboard packs a suite of features tailored for productive, creative collaboration. Below is a detailed breakdown:

✨ **Real-Time Collaboration:**  
Experience live synchronization where every action—drawing, erasing, or moving elements—is broadcast to all connected users instantly. Powered by WebSockets, this ensures zero perceptible lag, even with dozens of participants. Ideal for live feedback sessions or remote pair-programming.

🎨 **Intuitive Drawing Tools:**  
A comprehensive toolkit including:  
- **Freehand Pen:** Adjustable thickness (1-20px) and pressure-sensitive drawing for natural sketching.  
- **Shapes Library:** Pre-built rectangles, circles, lines, and arrows with customizable fill/stroke colors and dashed/solid line styles.  
- **Color Palette:** 20+ vibrant colors, plus a hex code picker for precise branding.  
- **Eraser Tool:** Selective or full-canvas erase modes, with adjustable brush size to refine details without starting over.  
These tools support undo/redo stacks (up to 50 actions) to encourage experimentation without fear of mistakes.

💬 **Live Chat Integration:**  
Seamlessly communicate via a persistent sidebar chat. Features include:  
- Text messaging with timestamps and user avatars.  
- Emoji reactions and @mentions for quick pings.  
- Message history that persists for the session, exportable as a log.  
This keeps discussions tied to the visual context, reducing context-switching.

📋 **Sticky Notes (Planned):**  
Upcoming feature to add draggable, resizable digital post-its. Users can color-code notes (e.g., yellow for ideas, red for blockers), group them into clusters, and even add hyperlinks or checklists. This will enable affinity diagramming and rapid ideation workshops.

🗺️ **Infinite Canvas:**  
Break free from fixed boundaries with panning (drag to move) and zooming (pinch/scrollwheel, up to 400% magnification). Grid snapping and rulers assist in aligning elements for professional diagrams. The canvas auto-saves viewport states per user.

🧑‍🤝‍🧑 **Room System:**  
Secure, ephemeral rooms with unique alphanumeric IDs (e.g., "abc123"). Options include:  
- Password protection for private sessions.  
- User limits (default: 10, configurable).  
- Session timers to auto-expire idle rooms.  
Share links via QR codes for easy mobile joining.

💾 **Save / Export Board:**  
Capture your masterpiece with:  
- PNG/SVG export at user-defined resolutions.  
- JSON serialization for reloading boards later.  
- Integration hooks for cloud storage (e.g., Google Drive via API).  
All exports include metadata like participant list and timestamps.

🧠 **Simple Interface:**  
A distraction-free UI with:  
- Dark/light mode toggle.  
- Customizable toolbars (dockable or floating).  
- Keyboard shortcuts (e.g., 'Z' for zoom, 'E' for eraser) for power users.  
Accessibility features like high-contrast mode and screen reader support ensure inclusivity.

---

## 🧠 Tech Stack
This project is built with a modern, efficient stack emphasizing performance, maintainability, and developer happiness. Here's a breakdown:

| Category       | Technology                  | Purpose                                                                 |
|----------------|-----------------------------|-------------------------------------------------------------------------|
| **Frontend**   | React.js ⚛️ + Next.js       | Component-based UI with server-side rendering for faster initial loads. |
| **Backend**    | Node.js 🌐                  | Lightweight server for handling API routes and session management.      |
| **Realtime**   | Socket.io ⚡                 | Bidirectional communication for instant updates without page refreshes. |
| **Styling**    | TailwindCSS 💅              | Utility-first CSS for rapid, responsive design without bloat.           |
| **Language**   | JavaScript (ES6+)           | Core scripting with async/await for clean, readable code.               |
| **State Mgmt** | React Context API           | Simple global state for user sessions and canvas data (Redux optional). |
| **Build Tools**| Vite/Webpack (via Next.js)  | Optimized bundling and hot module replacement for quick dev cycles.     |
| **Testing**    | Jest + React Testing Library| Unit and integration tests for core components (coverage: 80%+).        |
| **Hosting**    | Vercel / Render / Netlify   | Easy deployment with auto-scaling; CI/CD via GitHub Actions.            |

Choices like Socket.io were made for its ease of use and fallback to polling in unstable networks, while TailwindCSS accelerates prototyping without custom CSS files.

---

## 🏗️ Architecture Overview
COCREATE Whiteboard follows a client-server architecture with real-time enhancements:

1. **Client Side:** React components handle rendering the canvas (using HTML5 Canvas API for drawing). Socket.io client listens for events like 'draw' or 'chat', updating the DOM reactively.
2. **Server Side:** Node.js with Express serves the app and manages Socket.io namespaces per room. Redis (optional) for session persistence in production.
3. **Data Flow:** Drawing data is serialized as JSON paths and broadcast via sockets. Chat uses a simple in-memory store with TTL.
4. **Security:** Rooms use JWT tokens for auth; inputs sanitized to prevent XSS.

For a deeper dive, check the [architecture diagram](docs/architecture.md) (planned).

---

## 🧩 Screenshots
Visualize the experience with these key screens:

### 🏠 Home / Room Entry
A minimal and elegant entry screen where users can create or join rooms instantly. Features quick-start buttons, room history, and a demo mode.
![Login Page](./screenshots/login.png)
*Alt: Clean landing page with 'Create Room' and 'Join Room' inputs, branded header.*

### 🎨 Real-time Collaborative Canvas
A live, shared whiteboard for drawing, chatting, and brainstorming visually. Toolbar on the left, chat on the right, infinite grid background.
![Whiteboard UI](./screenshots/whiteboard.png)
*Alt: Full canvas view with sample sketches, color picker open, and zoom controls.*

### 🤝 Multi-user Collaboration
Simultaneous drawing sessions across multiple users with real-time updates. Avatars indicate active cursors; conflict resolution via last-write-wins.
![Collaboration Example](./screenshots/collaboration.png)
*Alt: Split-view showing two users drawing overlapping shapes, with synced erases.*

*(Note: Screenshots captured on Chrome v120; actual UI may vary with updates.)*

---

## ⚙️ Getting Started
Follow these steps to get a local copy up and running for development or testing. This setup assumes a Unix-like environment (adapt for Windows with Git Bash).

### 🧾 Prerequisites
Before starting, ensure you have:
- [Node.js](https://nodejs.org/) (v18 or higher recommended for optimal performance; check with `node -v`).
- [npm](https://www.npmjs.com/) (v9+; bundled with Node.js, verify with `npm -v`).
- [Git](https://git-scm.com/) for cloning (optional if downloading ZIP).
- A modern web browser (Chrome, Firefox, or Safari) for testing.
- Optional: [Yarn](https://yarnpkg.com/) as an npm alternative for faster installs.

If you're new to Node.js, consider using [nvm](https://github.com/nvm-sh/nvm) for version management.




### Installation

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/deepsingh-04/cocreate-whiteboard.git
    ```
2.  **Navigate to the project directory:**
    ```sh
    cd cocreate-whiteboard
    ```
3.  **Install dependencies:**
    ```sh
    npm install
    ```
4.  **Start the development server:**
    ```sh
    npm start
    ```

## Usage

Once the development server is running, open your web browser and navigate to `http://localhost:3000`. You can start a new board and share the link with others to begin collaborating.

## Contributing

Contributions are welcome! If you have suggestions for improvements or find any bugs, please feel free to open an issue or submit a pull request.

1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request
