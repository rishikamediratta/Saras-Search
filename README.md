# 🔍 Saras Search – Vue.js Search Application

A minimal, responsive search application built using **Vue 3 + Vite**, implementing debounced API calls, dynamic result rendering, and clean UI interactions.

---

## 🚀 Features

* 🔎 Real-time search with **debounce**
* 🌐 Fetches results from a **REST API (Wikipedia)**
* ⚡ Efficient API handling with **race condition prevention**
* 📦 Modular architecture using reusable Vue components
* 🎯 Expandable result items (accordion behavior)
* ⏳ Loading state indicator
* ❌ Handles empty queries and no-result states gracefully
* 📱 Fully responsive (mobile-friendly UI)
* ✨ Smooth transitions and minimal animations

---

## 🧠 Tech Stack

* **Vue 3 (Composition API)**
* **Vite**
* **JavaScript (ES6+)**
* **CSS (custom styling, no framework)**

---

## 📁 Project Structure

```
src/
│
├── components/
│   ├── SearchBar.vue      # Input component
│   ├── ResultList.vue     # List wrapper
│   ├── ResultItem.vue     # Individual result
│   └── Loader.vue         # Loading spinner
│
├── App.vue                # Main logic (state, API, debounce)
├── main.js
└── style.css              # Global styles
```

---

## ⚙️ How It Works

### 1. Debounced Search

* User input is tracked using `v-model`
* A `watch` function triggers API calls with a **300ms debounce**
* Prevents excessive API requests

---

### 2. API Integration

* Uses **Wikipedia Search API**
* Fetches results dynamically based on user input
* Cleans and formats response data before rendering

---

### 3. Race Condition Handling

* Tracks the latest query
* Ignores outdated API responses to avoid UI inconsistencies

---

### 4. Component-Based Architecture

* `App.vue` → handles logic and state
* Components → handle UI rendering

---

### 5. Expandable Results

* Clicking a result expands it
* Only one result remains open at a time (accordion behavior)

---

## 🚀 Scaling & Performance Improvements

### 🔹 Scaling for Larger Applications
- Use a global state manager (Pinia) for better state handling
- Separate API logic into services for maintainability
- Introduce routing for multi-page architecture
- Component reusability across different features


### ⚡ Performance Optimizations
- Debouncing input to reduce API calls
- Lazy loading components
- Caching API responses
- Pagination or infinite scrolling for large datasets
## 📦 Installation & Setup


```bash
# Clone the repository
git clone <your-repo-link>

# Navigate into project
cd saras-search

# Install dependencies
npm install

# Run development server
npm run dev
```

---

## 🎯 Key Concepts Demonstrated

* Vue Composition API (`ref`, `watch`)
* Props & Emits (parent-child communication)
* Debouncing logic
* API integration & async handling
* Conditional rendering
* State management at component level
* Clean UI/UX design principles

---

## 📌 Future Improvements

* API request cancellation using `AbortController`
* Keyboard navigation support
* Search result highlighting (safe implementation)
* Pagination / infinite scroll

---

## 👤 Author

**Rishika Mediratta**
Aspiring Full Stack Developer 🚀

---

## ⭐ Final Thoughts

This project focuses on building a **clean, efficient, and user-friendly search experience**, emphasizing core frontend engineering concepts over unnecessary complexity.

---

