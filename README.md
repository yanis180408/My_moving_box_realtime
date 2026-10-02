# Welcome to My Moving Box Realtime
***

## Task
The goal of this project is to build a web application where a box moves on the screen and its position is synchronized in real time between all connected users.
When a user moves their box, every other browser connected to the page sees the movement immediately, without refreshing.
The challenge lies in handling real-time communication between the server and several clients, keeping the shared state consistent, and handling users joining and leaving at any moment.

## Description
I solved this problem by using a server that holds the shared state and broadcasts every change to the clients:
- **Real-Time Communication** : the client and the server communicate through WebSockets (Socket.IO), so updates are pushed instantly instead of being polled.
- **Server State** : the server keeps the list of connected users with the position of each box, and sends the full state to a new user when they connect.
- **Movement Handling** : the client listens to keyboard events, sends the new position to the server, and the server broadcasts it to all other clients.
- **Rendering** : the boxes are drawn in the browser with HTML and CSS, and their positions are updated every time a message is received.
- **Boundaries** : the box can't leave the visible area, so its position is clamped to the limits of the play area.
- **Connections** : when a user disconnects, the server removes their box and notifies the other clients.

## Installation
The project needs Node.js to run the server.
1. Get the project :
```bash
git clone [REPOSITORY_URL]
cd my_moving_box_realtime
```

2. Install the dependencies :
```bash
npm install
```

3. Start the server :
```bash
npm start
```

4. Open the page in your browser at `http://localhost:3000`.

## Usage
Open the page in several tabs or on several devices connected to the same server. Each user controls their own box, and every movement appears on all screens in real time.

**Controls :**
| Key | Action |
|-----|--------|
| `↑` | Move up |
| `↓` | Move down |
| `←` | Move left |
| `→` | Move right |

**Example :**
1. Open `http://localhost:3000` in two browser windows.
2. Move the box in the first window with the arrow keys.
3. Watch the box move at the same time in the second window.
4. Close one window and notice that its box disappears from the other.

### The Core Team


<span><i>Made at <a href='https://qwasar.io'>Qwasar SV -- Software Engineering School</a></i></span>
<span><img alt='Qwasar SV -- Software Engineering School's Logo' src='https://storage.googleapis.com/qwasar-public/qwasar-logo_50x50.png' width='20px' /></span>
