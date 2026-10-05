# ContactSphere — Modern Contact Management Application

A complete, modern, responsive Contact Management System built with a clean and maintainable full-stack architecture. Perfect for college project evaluation, portfolio demonstration, and real-world everyday use.

---

## 🌟 Key Features

### 1. 📊 Interactive Dashboard
- **Live Metric Cards**: Total Contacts, Starred Favorites, Category Groups, and Recently Added this week.
- **Category Distribution Chart**: Visual breakdown with stacked color-coded progress bars and percentage distribution.
- **Recently Added Contacts**: Quick view of latest connections with one-click direct phone calling, email dispatch, and full profile inspection.
- **Quick Actions Hub**: One-tap shortcuts for creating contacts, exporting to CSV, importing from files, and managing groups.

### 2. 📇 Comprehensive Contact Management
- **Full Contact Profiles**:
  - Full Name (required)
  - Mobile Phone Number (with format validation)
  - Email Address (with format validation)
  - Company & Organization
  - Job Title / Role
  - Category / Group (`Work`, `College`, `Friends`, `Family`, `Others` + unlimited custom groups)
  - Physical Address (with direct Google Maps integration)
  - Notes / Bio
  - Custom Avatar Palette (12 vibrant themes)
  - Starred Favorite status
- **Real-Time Live Card Preview**: As you type in the Add/Edit form, a live preview card updates in real time.
- **Form Validation & Duplicate Prevention**: Validates required inputs, phone digits, email syntax, and prevents duplicate records by alerting if an email or phone number is already registered.
- **Safe Delete Confirmation**: Modal dialog displaying contact avatar and name before irreversible deletion.

### 3. 🔍 Smart Search, Filtering & Sorting
- **Omni-Search**: Real-time debounced search matching against names, emails, phone numbers, companies, job titles, addresses, and notes.
- **Dual View Layouts**: Seamless toggle between responsive **Grid Cards** view and structured **Table View**.
- **Sorting**: Sort by Name (A-Z / Z-A), Company, Date Created, or Recently Updated in ascending/descending order.
- **Group Filtering**: Filter by category pills or the quick-access sidebar.
- **Bulk Operations**: Multi-select checkboxes with bulk delete support.
- **Pagination**: Configurable page sizes (8, 12, 24, 50 contacts per page) with page number indicators.

### 4. ⭐ Dedicated Favorites Hub
- Dedicated page for starred contacts with instant favorite toggling.
- Direct phone call (`tel:`), email compose (`mailto:`), WhatsApp chat (`wa.me`), and clipboard copying.

### 5. 🏷️ Category & Group Management
- View total members per group with avatar preview stacks.
- Add custom groups on the fly (both from the Groups view and directly inside the Contact form).
- Safe deletion of custom groups with automatic reassignment of members to `Others`.

### 6. 📁 Data Import & Export (CSV & JSON)
- **Export to CSV**: Export your contacts database to a standard CSV file compatible with Microsoft Excel and Google Sheets.
- **Import from CSV**: Upload CSV files with automatic header mapping and validation.
- **Sample CSV Template**: Built-in template download to guide users on formatting.
- **Full JSON Backup**: Download complete raw JSON data for backups.
- **Reset to Sample Data**: One-click restoration of 12 realistic contacts across diverse categories for easy presentation and demo.

### 7. 🌗 Modern UI & Dark Mode
- Built with Tailwind CSS, custom fonts (**Plus Jakarta Sans** & **Inter**), glassmorphism panels, and smooth micro-animations.
- Full **Light Mode** and **Dark Mode** support with automatic system preference detection and localStorage persistence.
- Celebratory confetti effects upon successful contact creation.
- Toast notifications with icons for all CRUD operations.

### 8. 🗄️ Robust Data Persistence & API
- **Node.js + Express RESTful API** backend.
- Persistent file database stored at `server/data/contacts.json` and `server/data/groups.json`.
- Automatic fallback to **LocalStorage** so the application continues to work seamlessly even in offline or standalone static mode.

---

## 🛠️ Technology Stack

| Layer | Technology |
|---|---|
| **Frontend Framework** | React 18 with TypeScript |
| **Styling & Design System** | Tailwind CSS + Lucide React Icons |
| **Bundler & Tooling** | Vite 6 |
| **Backend Framework** | Node.js & Express |
| **Data Storage** | Persistent JSON Database with LocalStorage Sync Fallback |
| **Celebration & Effects** | Canvas Confetti |

---

## 🚀 Getting Started

### Prerequisites
- Node.js (v18 or higher recommended)
- npm (v9 or higher)

### Installation
Dependencies are already installed. If running on a new machine:
```bash
npm install
```

### Running the Application

#### Option 1: Full-Stack Development Mode (Recommended)
Runs both the Express backend API (port 5000) and the Vite frontend (port 3000) concurrently with hot-reloading:
```bash
npm run dev
```
Open your browser at `http://localhost:3000`.

#### Option 2: Production Server
Builds the frontend and serves both the API and client application on port 5000:
```bash
npm start
```
Open your browser at `http://localhost:5000`.

---

## 📡 RESTful API Documentation

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/health` | Health check endpoint |
| `GET` | `/api/contacts` | List contacts with query params (`search`, `group`, `favorite`, `sort`, `order`, `page`, `limit`) |
| `GET` | `/api/contacts/stats` | Analytics summary (totals, favorites, recent contacts, group breakdown) |
| `GET` | `/api/contacts/:id` | Retrieve single contact by ID |
| `POST` | `/api/contacts` | Create a new contact (validates required fields and duplicates) |
| `PUT` | `/api/contacts/:id` | Update an existing contact |
| `PATCH` | `/api/contacts/:id/favorite` | Toggle favorite status |
| `DELETE` | `/api/contacts/:id` | Delete a single contact |
| `POST` | `/api/contacts/bulk-delete` | Delete multiple contacts by IDs |
| `GET` | `/api/contacts/export/csv` | Download contacts as formatted CSV file |
| `POST` | `/api/contacts/import/csv` | Import contacts from CSV payload |
| `POST` | `/api/contacts/reset-samples` | Reset database to 12 default sample contacts |
| `GET` | `/api/groups` | Retrieve all category groups |
| `POST` | `/api/groups` | Create a new custom group |
| `DELETE` | `/api/groups/:name` | Delete a custom group and reassign contacts to 'Others' |

---

## 📂 Project Structure

```
Contact_Management_Application/
├── server/
│   ├── data/
│   │   ├── contacts.json         # Persistent contacts database
│   │   └── groups.json           # Persistent category groups
│   ├── index.js                  # Express REST API & static server
│   └── sampleData.js             # 12 initial realistic contacts & seed data
├── src/
│   ├── components/
│   │   ├── common/               # Avatar, Badge, EmptyState, Pagination, Toast
│   │   ├── contacts/             # ContactCard, ContactTable, ContactList, ContactDetailModal, ContactFormModal, DeleteConfirmModal
│   │   ├── dashboard/            # DashboardView, DashboardStats, RecentContactsCard, GroupDistributionCard, QuickActionsCard
│   │   ├── favorites/            # FavoritesView
│   │   ├── groups/               # GroupsView
│   │   ├── layout/               # Navbar, Sidebar
│   │   └── settings/             # SettingsView
│   ├── context/
│   │   ├── ContactContext.tsx    # State management for CRUD, filters, search, modals
│   │   └── ThemeContext.tsx      # Light/Dark mode state & persistence
│   ├── services/
│   │   ├── api.ts                # Unified API client with automatic offline fallback
│   │   └── sampleData.ts         # Client seed data & avatar palette
│   ├── types/
│   │   └── contact.ts            # TypeScript interfaces & types
│   ├── App.tsx                   # Main layout and view routing
│   ├── index.css                 # Tailwind directives & theme styles
│   └── main.tsx                  # React DOM entry point
├── dist/                         # Production build bundle
├── index.html                    # HTML entry with Plus Jakarta Sans font
├── package.json                  # Scripts & dependencies
├── tailwind.config.js            # Tailwind theme configuration
├── tsconfig.json                 # TypeScript compiler options
└── vite.config.ts                # Vite config with API proxy
```

---

## 🎓 College Project Highlights
- **Layered Architecture**: Complete separation of Concerns between presentation components, state management (React Context), service integration, and backend API.
- **Defensive Engineering**: Dual-mode resilience (works with the Express REST API backend or smoothly switches to localStorage if offline).
- **Data Integrity**: Full server-side and client-side input validation and duplicate prevention.
- **Real-World Usability**: Click-to-call, click-to-email, WhatsApp chat link, Google Maps address lookup, clipboard copying, and CSV import/export.
