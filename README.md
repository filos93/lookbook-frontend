<p>
  <img src="./src/assets/logo.png" alt="LookBook Logo" width="180">
</p>

# LookBook Frontend (Swap Studio)

React + Vite single-page client application for **LookBook (Swap Studio)**, a peer-to-peer clothing exchange and administrative inventory management platform.

Built with React 18, Vite, and Tailwind CSS, it provides:

- Real-time catalog search
- Interactive 2-user / 2-item swap building
- Multi-criteria order filtering
- Client-side validation
- Automatic state synchronization with the backend API

> **Backend Repository:** Looking for the Node.js, Express 5 & MySQL REST API? Check out [lookbook-api](https://github.com/filos93/lookbook-api).

---

## 🚀 Tech Stack

- **Framework & Build Tool:** React 18, Vite (`@vitejs/plugin-react`)
- **Styling & UI:** Tailwind CSS, Dark Mode UI, PostCSS, Autoprefixer
- **API Integration:** Unified Fetch API client (`src/api/client.js`) with Vite development proxy (`/api → http://localhost:3000`)
- **Testing & Quality:** Vitest, React Testing Library (`@testing-library/react`, `@testing-library/user-event`, `@testing-library/jest-dom`), and `jsdom`

---

## 🛠️ Project Structure

```text
lookbook-frontend/
├── public/
├── src/
│   ├── __tests__/
│   │   └── App.test.jsx
│   ├── api/
│   │   └── client.js
│   ├── assets/
│   │   └── logo.png
│   ├── components/
│   │   ├── AddProductModal.jsx
│   │   ├── AddUserModal.jsx
│   │   ├── DeleteProductModal.jsx
│   │   ├── DeleteSwapModal.jsx
│   │   ├── DeleteUserModal.jsx
│   │   ├── EditProductModal.jsx
│   │   ├── EditSwapModal.jsx
│   │   ├── EditUserModal.jsx
│   │   ├── NavBar.jsx
│   │   ├── ProductCard.jsx
│   │   ├── StatsOverview.jsx
│   │   ├── SwapCard.jsx
│   │   ├── SwapFilters.jsx
│   │   ├── SwapRecord.jsx
│   │   └── UserCard.jsx
│   ├── hooks/
│   │   └── useAppData.js
│   ├── App.jsx
│   ├── index.css
│   ├── main.jsx
│   └── setupTests.js
├── .env.example
├── .gitignore
├── index.html
├── package.json
├── postcss.config.js
├── README.md
├── tailwind.config.js
└── vite.config.js
```

---

## 🏁 Quick Start

### 1. Requirements

- Node.js (v18+ recommended)
- A running instance of **lookbook-api** (default: `http://localhost:3000`)

### 2. Environment Configuration

Copy `.env.example` to `.env` if you need to override the default API endpoint:

```bash
cp .env.example .env
```

```env
# Leave as /api during local development to use the Vite proxy
VITE_API_BASE_URL=/api

# Example production endpoint:
# VITE_API_BASE_URL=https://your-lookbook-api.onrender.com/api
```

### 3. Installation & Development Server

```bash
# Clone the repository
git clone https://github.com/filos93/lookbook-frontend.git
cd lookbook-frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

The application will be available at:

```text
http://localhost:5173
```

All `/api/*` requests are automatically proxied to:

```text
http://localhost:3000
```

---

## 🧭 Views & Backend Integration

### 🖥️ Dashboard Views

| View / Module | Description |
|--------------|-------------|
| Stats Overview | Displays live totals for garments, active swaps, registered users, and gross exchanged value (€) |
| Explore Catalog | Responsive garment grid with multi-photo previews, live search, swap pre-selection, and inventory CRUD |
| Swap Builder | Interactive 2-step selector enforcing distinct owners and item availability |
| Active Swaps | Chronological swap ledger with date-range and garment filtering, inline editing, and rollback deletion |
| Users Directory | Community member directory with registration, profile editing, and cascading deletion warnings |

### 🔌 API Client Mapping (`src/api/client.js`)

| Helper Function | Backend Endpoint | Purpose |
|----------------|------------------|---------|
| `fetchUsers`, `createUser`, `updateUser`, `deleteUser` | `/api/users` | Manage community members |
| `fetchProducts`, `createProduct`, `updateProduct`, `deleteProduct` | `/api/products` | Manage inventory listings |
| `fetchSwaps`, `createSwap`, `updateSwap`, `deleteSwap` | `/api/swaps` | Manage swap transactions |

---

## 🧪 Testing & Production Build

Integration tests run with Vitest and React Testing Library against mocked API boundaries to verify:

- UI rendering
- Modal workflows
- Swapped-item lockouts
- Client-side validation
- Backend concurrency error handling

```bash
# Run tests once
npm test

# Watch mode
npm run test:watch

# Production build
npm run build

# Preview production build
npm run preview

# Dependency audit
npm audit
```

---

## ✅ Core Features

- **Unified API Client & Dev Proxy**  
  Centralized fetch wrapper with standardized error handling and seamless Vite proxy integration.

- **Read-Only Status Enforcement**  
  Locks edits, deletions, and duplicate selections on already-swapped garments.

- **Conflict-Aware Swap Builder**  
  Prevents same-owner exchanges and invalid selections before API submission.

- **Live Multi-Field Filtering**  
  Instant search across garments, prices, and owner metadata.

- **Centralized State Synchronization**  
  `useAppData` refreshes products, swaps, and KPIs after every mutation.

- **Client-Side Validation**  
  Email, name, pricing, and image URL validation across all forms.

- **Automated Integration Testing**  
  Test suite covering rendering, user workflows, disabled states, and race-condition handling.

## 📄 License

This project is released under the MIT License.
