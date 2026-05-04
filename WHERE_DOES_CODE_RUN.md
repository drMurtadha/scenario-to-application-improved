# 🏗️ WHERE DOES THE MOCK DATA CODE RUN?
## Architecture Guide: Google Sheets vs. Backend vs. Frontend

---

## ❌ NOT in Google Sheets

**Google Sheets limitations:**
- ❌ Can't run JavaScript code directly
- ❌ Can only use Google Sheets formulas (=SUM, =IF, etc.)
- ❌ No file system or data generation capabilities
- ❌ Can't update in real-time every 30 seconds

**Google Sheets is the DATA STORAGE LAYER, not where code runs.**

---

## ✅ WHERE THE CODE ACTUALLY RUNS

The `mockBusData.js` code runs in ONE of THREE places:

### Option 1: **BACKEND** (Node.js Server) - RECOMMENDED

```
┌─────────────────────────────────────────────────────────────┐
│                     YOUR APP ARCHITECTURE                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  FRONTEND (Browser)        BACKEND (Node.js)               │
│  ┌─────────────────────┐  ┌─────────────────────────────┐ │
│  │                     │  │ mockBusData.js RUNS HERE ✓  │ │
│  │ React Component     │  │ ┌──────────────────────────┐│ │
│  │ - Shows buses       │  │ │class MockBusDataService  ││ │
│  │ - Updates every 30s │←─┤ │{                         ││ │
│  │                     │  │ │  initializeRoutes()      ││ │
│  │ Calls API:          │  │ │  initializeBuses()       ││ │
│  │ GET /api/buses      │  │ │  getBusStatus()          ││ │
│  │                     │  │ │  updateBusPositions()    ││ │
│  └─────────────────────┘  │ │}                         ││ │
│           ↓               │ │                          ││ │
│  Browser displays bus     │ │ Timer: every 30 seconds  ││ │
│  data from API response   │ │ updateBusPositions()     ││ │
│                           │ └──────────────────────────┘│ │
│                           │                             │ │
│                           │ Express Server              │ │
│                           │ GET /api/buses/:routeId    │ │
│                           │ → returns current state    │ │
│                           └─────────────────────────────┘ │
│                                      ↕                     │
│                           (Optional) Google Sheets        │
│                           (only if you want persistence)  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**How it works:**

1. **Backend server runs mockBusData.js**
   - Data lives in server memory
   - Updates every 30 seconds
   - No database needed for mock data

2. **Frontend calls the API**
   ```javascript
   // In React component
   fetch('/api/buses/ROUTE-1')
     .then(res => res.json())
     .then(buses => setBuses(buses))  // Show on screen
   ```

3. **User sees real-time updates**
   - Browser refreshes display every 30 seconds
   - Feels like real-time bus tracking

**Pros:**
- ✅ Most realistic
- ✅ Scalable to multiple users
- ✅ Professional architecture
- ✅ Can connect to real API later (no code change)

**Cons:**
- ⚠️ Requires backend knowledge (Node.js/Express)
- ⚠️ Need to deploy server somewhere
- ⚠️ More setup time (~5 hours)

**File structure:**
```
project/
├── backend/
│   ├── mockBusData.js        ← CODE RUNS HERE
│   ├── server.js             ← Express app
│   └── package.json
├── frontend/
│   ├── BusTracker.jsx        ← React component
│   └── ...
└── database/
    └── buses.json            ← Optional persistent storage
```

---

### Option 2: **FRONTEND** (Browser with JavaScript) - SIMPLEST

```
┌──────────────────────────────────────┐
│       YOUR APP (All in Browser)      │
├──────────────────────────────────────┤
│                                      │
│  mockBusData.js RUNS HERE ✓         │
│  ┌──────────────────────────────────┤
│  │ const dataService =              │
│  │   new MockBusDataService()       │
│  │                                  │
│  │ setInterval(() => {              │
│  │   dataService.updateBusPositions()
│  │   setBuses(...)  // Update UI    │
│  │ }, 30000)                        │
│  └──────────────────────────────────┤
│                                      │
│  React Component renders buses       │
│  Data stored in memory (resets      │
│  when page refreshes)               │
│                                      │
└──────────────────────────────────────┘
```

**How it works:**

1. **All code runs in browser**
   - No server needed
   - mockBusData.js included in React app
   - Data updates every 30 seconds

2. **Code example:**

```javascript
// BusTracker.jsx (React component)
import MockBusDataService from './mockBusData';

export default function BusTracker() {
  const [buses, setBuses] = useState([]);
  const dataService = new MockBusDataService();
  
  useEffect(() => {
    // Update every 30 seconds
    const interval = setInterval(() => {
      dataService.updateBusPositions();
      setBuses(dataService.getBusesOnRoute('ROUTE-1'));
    }, 30000);
    
    return () => clearInterval(interval);
  }, []);
  
  return (
    <div>
      {buses.map(bus => (
        <div key={bus.busId}>
          {bus.currentStop} → {bus.nextStop}
          ETA: {bus.estimatedNextArrival}
        </div>
      ))}
    </div>
  );
}
```

**Pros:**
- ✅ Simplest to build (no backend)
- ✅ Fastest to prototype (2-3 hours)
- ✅ No server deployment needed
- ✅ Works completely offline

**Cons:**
- ❌ Data resets when page refreshes
- ❌ Only works for single user
- ❌ Can't scale
- ❌ Not realistic for production

**File structure:**
```
project/
├── src/
│   ├── mockBusData.js        ← CODE RUNS HERE (in browser)
│   ├── BusTracker.jsx
│   ├── App.jsx
│   └── ...
└── package.json
```

---

### Option 3: **GOOGLE SHEETS** (Partial) - HYBRID APPROACH

```
┌────────────────────────────────────────────────────────────┐
│         HYBRID: Frontend + Google Sheets                   │
├────────────────────────────────────────────────────────────┤
│                                                            │
│  FRONTEND (React)                                          │
│  mockBusData.js runs in browser ✓                         │
│  Updates every 30 seconds                                 │
│          ↓                                                 │
│  Google Sheets API                                         │
│  Reads/writes to Google Sheet                            │
│          ↓                                                 │
│  GOOGLE SHEETS (Data Storage)                             │
│  Buses | Routes | Stops tables                            │
│  (Data persists between sessions)                         │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

**How it works:**

1. **mockBusData.js runs in browser** (like Option 2)
2. **But instead of losing data on refresh**, it writes to Google Sheets
3. **When page reloads**, it reads latest data from Google Sheets

**Code example:**

```javascript
import { GoogleSpreadsheet } from 'google-spreadsheet';

class MockBusDataService {
  constructor(spreadsheetId, apiKey) {
    this.doc = new GoogleSpreadsheet(spreadsheetId);
    this.apiKey = apiKey;
  }
  
  async initializeBuses() {
    // Read from Google Sheets
    const busesSheet = await this.doc.sheetsByTitle['BUSES'];
    this.buses = await busesSheet.getRows();
  }
  
  async updateBusPositions() {
    // Update bus data
    this.buses.forEach(bus => {
      bus.currentStop = this.calculateNextStop(bus);
      bus.save(); // Write back to Google Sheets
    });
  }
}

// In React:
useEffect(() => {
  const dataService = new MockBusDataService(
    'YOUR_SPREADSHEET_ID',
    'YOUR_API_KEY'
  );
  
  const interval = setInterval(() => {
    dataService.updateBusPositions();
    setBuses(dataService.buses);
  }, 30000);
  
  return () => clearInterval(interval);
}, []);
```

**Pros:**
- ✅ No backend server needed
- ✅ Data persists (not lost on refresh)
- ✅ Simple Google Sheets interface for demo
- ✅ Can view data in spreadsheet

**Cons:**
- ⚠️ Google Sheets API has rate limits (slower)
- ⚠️ Requires API credentials setup
- ⚠️ Not ideal for real-time performance
- ⚠️ Overkill for prototype

---

## 📊 COMPARISON TABLE

| Feature | Option 1: Backend | Option 2: Frontend | Option 3: Hybrid |
|---------|-------------------|-------------------|------------------|
| **Code runs where?** | Node.js server | Browser | Browser |
| **Data storage** | Server memory | Browser memory | Google Sheets |
| **Persistent data** | ✅ Yes | ❌ No | ✅ Yes |
| **Real-time updates** | ✅ Yes (30sec) | ✅ Yes (30sec) | ✅ Yes (30sec) |
| **Multiple users** | ✅ Yes | ❌ No (1 user) | ⚠️ Limited |
| **Setup complexity** | ⚠️ Medium | ✅ Easy | ⚠️ Medium |
| **Development time** | 5 hours | 2-3 hours | 3-4 hours |
| **Performance** | ✅ Fast | ✅ Fast | ⚠️ Slower (API) |
| **Production ready** | ✅ Yes | ❌ No | ⚠️ Partial |
| **Cost** | Free (AWS/Heroku) | Free | Free (Google has limits) |

---

## 🎯 WHICH OPTION SHOULD YOU CHOOSE?

### For Learning & Portfolio:
**Recommendation: Option 1 (Backend with Node.js)**

Why:
- ✅ Most realistic/professional
- ✅ Shows you understand architecture
- ✅ Impresses instructors and employers
- ✅ Path to real production code
- ✅ Scalable

### For Quick Demo:
**Recommendation: Option 2 (Frontend only)**

Why:
- ✅ Fastest to build (2-3 hours)
- ✅ No backend knowledge needed
- ✅ Works immediately
- ⚠️ But data resets on page refresh

### For Teaching/Classroom:
**Recommendation: Option 2 (Frontend) → Option 1 (Backend)**

Why:
- Start with frontend for quick demo
- Then upgrade to backend for full implementation

---

## 🚀 STEP-BY-STEP: BUILD OPTION 1 (RECOMMENDED)

### Step 1: Create Backend Project

```bash
mkdir bus-tracker-backend
cd bus-tracker-backend
npm init -y
npm install express cors
```

### Step 2: Create mockBusData.js

**File: `mockBusData.js`**

```javascript
class MockBusDataService {
  constructor() {
    this.routes = this.initializeRoutes();
    this.buses = this.initializeBuses();
  }
  
  initializeRoutes() {
    return [
      {
        id: "ROUTE-1",
        name: "Dorm → Central Campus",
        stops: [
          {id: "STOP-1", name: "Kolej Tun Razak", lat: 1.556, lng: 103.738},
          {id: "STOP-2", name: "Kolej Chancellor", lat: 1.553, lng: 103.735},
          {id: "STOP-3", name: "Engineering", lat: 1.550, lng: 103.740},
          {id: "STOP-4", name: "Central Hub", lat: 1.548, lng: 103.742},
          {id: "STOP-5", name: "Library", lat: 1.545, lng: 103.745},
        ]
      }
    ];
  }
  
  initializeBuses() {
    const buses = [];
    this.routes.forEach(route => {
      for (let i = 0; i < 5; i++) {
        buses.push({
          id: `BUS-${route.id}-${i}`,
          routeId: route.id,
          currentStopIndex: Math.floor(Math.random() * route.stops.length),
          delay: this.generateRealisticDelay(),
          occupancy: Math.floor(Math.random() * 60),
          capacity: 60
        });
      }
    });
    return buses;
  }
  
  generateRealisticDelay() {
    const random = Math.random();
    if (random < 0.70) return 0;
    if (random < 0.90) return Math.random() * 5;
    return Math.random() * 15;
  }
  
  getBusStatus(busId) {
    const bus = this.buses.find(b => b.id === busId);
    const route = this.routes.find(r => r.id === bus.routeId);
    const currentStop = route.stops[bus.currentStopIndex];
    const nextStop = route.stops[bus.currentStopIndex + 1];
    
    return {
      busId: bus.id,
      routeName: route.name,
      currentLocation: {lat: currentStop.lat, lng: currentStop.lng},
      currentStop: currentStop.name,
      nextStop: nextStop ? nextStop.name : "End",
      occupancy: `${bus.occupancy}/${bus.capacity}`,
      delay: bus.delay,
      status: bus.delay > 10 ? "Delayed" : "On Time"
    };
  }
  
  getBusesOnRoute(routeId) {
    return this.buses
      .filter(b => b.routeId === routeId)
      .map(b => this.getBusStatus(b.id));
  }
  
  updateBusPositions() {
    this.buses.forEach(bus => {
      const route = this.routes.find(r => r.id === bus.routeId);
      if (Math.random() < 0.3) {
        bus.currentStopIndex = (bus.currentStopIndex + 1) % route.stops.length;
        if (Math.random() < 0.1) {
          bus.delay = this.generateRealisticDelay();
        }
        bus.occupancy = Math.max(0, Math.min(60,
          bus.occupancy + Math.floor((Math.random() - 0.5) * 10)
        ));
      }
    });
  }
}

export default MockBusDataService;
```

### Step 3: Create Express Server

**File: `server.js`**

```javascript
import express from 'express';
import cors from 'cors';
import MockBusDataService from './mockBusData.js';

const app = express();
app.use(cors());

const dataService = new MockBusDataService();

// Update buses every 30 seconds
setInterval(() => {
  dataService.updateBusPositions();
}, 30000);

// API endpoint
app.get('/api/buses/:routeId', (req, res) => {
  const buses = dataService.getBusesOnRoute(req.params.routeId);
  res.json(buses);
});

app.listen(3000, () => {
  console.log('Bus Tracker API running on port 3000');
});
```

### Step 4: Run the Server

```bash
node server.js
```

Output:
```
Bus Tracker API running on port 3000
```

### Step 5: Test the API

Open browser and go to:
```
http://localhost:3000/api/buses/ROUTE-1
```

Response (JSON):
```json
[
  {
    "busId": "BUS-ROUTE-1-0",
    "routeName": "Dorm → Central Campus",
    "currentLocation": {"lat": 1.548, "lng": 103.742},
    "currentStop": "Central Hub",
    "nextStop": "Library",
    "occupancy": "42/60",
    "delay": 0,
    "status": "On Time"
  },
  ...
]
```

### Step 6: Connect Frontend React App

**File: `BusTracker.jsx`**

```javascript
import React, { useState, useEffect } from 'react';

export default function BusTracker() {
  const [buses, setBuses] = useState([]);
  
  useEffect(() => {
    // Fetch buses every 30 seconds
    const fetchBuses = async () => {
      const res = await fetch('http://localhost:3000/api/buses/ROUTE-1');
      const data = await res.json();
      setBuses(data);
    };
    
    fetchBuses();
    const interval = setInterval(fetchBuses, 30000);
    return () => clearInterval(interval);
  }, []);
  
  return (
    <div className="bus-tracker">
      <h1>🚌 Real-Time Bus Tracker</h1>
      {buses.map(bus => (
        <div key={bus.busId} className="bus-card">
          <h3>{bus.busId}</h3>
          <p>📍 {bus.currentStop}</p>
          <p>🎯 {bus.nextStop}</p>
          <p>👥 {bus.occupancy}</p>
          <p>⏱️ Delay: {bus.delay.toFixed(0)} min</p>
          <p>{bus.status}</p>
        </div>
      ))}
    </div>
  );
}
```

---

## 📍 SUMMARY: WHERE DOES THE CODE RUN?

| Component | Where It Runs | Technology |
|-----------|---------------|-----------|
| `mockBusData.js` | **Backend Server** (Node.js) | JavaScript/Node.js ✅ |
| `server.js` (Express) | **Backend Server** | JavaScript/Node.js ✅ |
| `BusTracker.jsx` | **Browser** (Frontend) | React/JavaScript ✅ |
| Google Sheets | **Cloud Storage** (Optional) | Google API ⚠️ |
| Database | **NOT NEEDED for mock** | - |

**Google Sheets does NOT run the code - it's just data storage (optional).**

---

## ✅ FINAL ANSWER TO YOUR QUESTION

**Q: Should the code run in Google Sheets?**

**A: No, never.**

- mockBusData.js runs on a **Node.js backend server**
- Google Sheets only stores **data** (optional)
- Frontend (React) **calls the API** to get data
- Browser displays the data to users

**This is the correct architecture.** 🏗️

