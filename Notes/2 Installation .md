# Project Setup

## Create Project Structure
```bash
mkdir client
mkdir server
```

---

## Server Setup

### Initialize Server
```bash
cd server
npm init -y
```

### Install Dependencies
```bash
npm i express socket.io cors
npm i --save-dev nodemon
```

### Configure Server Scripts

In `server/package.json`, add:
```json
"scripts": {
  "dev": "nodemon app.js"
}
```

---

## Client Setup

### Initialize Client with Vite
```bash
cd client
npm create vite@latest
```

**Choose:**
- Framework: `react`
- Variant: `js`

### Install Dependencies
```bash
npm i
npm i @mui/material
npm i socket.io-client
```

### Run Development Server
```bash
npm run dev
```

---

## Quick Reference

| Command            | Purpose                          |
| ------------------ | -------------------------------- |
| `npm run dev`      | Start server with nodemon        |
| `npm run dev`      | Start client development server  |
| `socket.io-client` | Client-side Socket.io connection |
| `@mui/material`    | Material-UI components           |