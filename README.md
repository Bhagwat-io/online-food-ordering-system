# 🍽 BITES — Online Food Ordering System

A fully static, single-file online food ordering web application built with pure HTML, CSS, and vanilla JavaScript. No frameworks, no build tools, no dependencies — just open and run.

---

## 📸 Overview

BITES is a dark-themed, responsive food ordering UI that simulates a real-world food delivery experience. It includes a browsable menu, category filtering, a slide-out shopping cart, dynamic pricing, and an order confirmation flow.

---

## 🚀 Getting Started

### Prerequisites

None. This is a zero-dependency static HTML file.

### Running the App

1. Download `food-ordering.html`
2. Open it in any modern web browser:
   - Double-click the file, **or**
   - Drag it into a browser window, **or**
   - Run a local server (optional):
     ```bash
     npx serve .
     # then open http://localhost:3000/food-ordering.html
     ```

That's it. No installation, no build step, no server required.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🍽 Menu Grid | 12 food items across 7 categories |
| 🔍 Category Filter | Filter by Pizza, Burgers, Sushi, Pasta, Salads, Desserts, Drinks |
| 🛒 Cart Panel | Slide-out cart with smooth animations |
| ➕➖ Quantity Controls | Add, increase, or decrease item quantities |
| 💰 Dynamic Pricing | Auto-calculates subtotal, delivery fee, tax (8%), and total |
| 🆓 Free Delivery | Orders over $30 automatically qualify for free delivery |
| 🎉 Order Placement | Simulated order flow with randomized ETA (20–35 min) |
| 🔔 Toast Notifications | Pop-up confirmations when items are added to cart |
| 📱 Responsive Design | Mobile-friendly layout adapts to all screen sizes |
| ✨ Animations | Floating hero, card hover effects, cart slide-in, fade-up entries |

---

## 📁 Project Structure

```
food-ordering.html        ← Entire application (HTML + CSS + JS in one file)
README.md                 ← This file
```

Since this is a single-file app, everything lives in `food-ordering.html`:

```
food-ordering.html
├── <head>          Google Fonts import, CSS variables, all styles
├── <header>        Sticky nav with logo and cart button
├── Hero Section    Headline, CTA buttons, animated food emoji, stats
├── Features Strip  Delivery, freshness, payment, returns highlights
├── Menu Section    Category pills + responsive menu card grid
├── Cart Panel      Slide-out drawer with items, qty controls, totals
├── Toast System    Animated notification pop-ups
├── Order Modal     Success confirmation with delivery ETA
├── <footer>        Links and branding
└── <script>        All app logic (menu data, cart state, UI updates)
```

---

## 🗂 Menu Categories & Items

| Category | Items |
|---|---|
| 🍕 Pizza | Margherita Pizza, Spicy Pepperoni Pizza |
| 🍔 Burgers | BBQ Loaded Burger, Avocado Smash Burger |
| 🍱 Sushi | Salmon Nigiri Set, Dragon Roll |
| 🍝 Pasta | Truffle Tagliatelle, Pesto Arrabbiata Penne |
| 🥗 Salads | Caesar Royale |
| 🍰 Desserts | Lava Choco Cake |
| 🥤 Drinks | Mango Matcha Smoothie, Cold Brew Lemonade |

---

## 🧠 How It Works

### Data Layer
All menu items are stored in a `menuData` JavaScript array at the bottom of the file. Each item has:
```javascript
{ id, name, desc, price, emoji, cat, badge, badgeClass, rating, reviews }
```

### State Management
Cart state is managed with a plain JavaScript object (`cart`), keyed by item ID:
```javascript
cart = {
  1: { ...itemData, qty: 2 },
  5: { ...itemData, qty: 1 },
}
```

### Key Functions

| Function | Purpose |
|---|---|
| `renderMenu(filter)` | Renders the menu grid, optionally filtered by category |
| `addToCart(id)` | Adds an item or increments its quantity |
| `updateQty(id, delta)` | Increases or decreases quantity; removes if qty reaches 0 |
| `updateCartUI()` | Re-renders cart panel and recalculates totals |
| `toggleCart()` | Opens/closes the slide-out cart panel |
| `placeOrder()` | Clears cart, closes panel, shows success modal |
| `showToast(msg)` | Displays a temporary toast notification |

---

## 🎨 Design System

### Color Palette

| Variable | Value | Usage |
|---|---|---|
| `--bg` | `#0f0e0c` | Page background |
| `--surface` | `#1a1916` | Secondary surfaces |
| `--card` | `#221f1b` | Cards and panels |
| `--accent` | `#f5a623` | Primary accent (amber) |
| `--accent2` | `#e85d04` | Spicy/hot badges |
| `--text` | `#f0ece4` | Primary text |
| `--muted` | `#8a8070` | Secondary text |
| `--green` | `#4caf82` | Veg badges, active states |

### Typography

| Font | Usage |
|---|---|
| **Bebas Neue** | Display headings, prices, logo |
| **DM Sans** | Body text, UI elements |
| **Playfair Display** (italic) | Hero accent word |

All fonts are loaded from Google Fonts via CDN.

---

## 🛒 Cart & Pricing Logic

- **Subtotal**: Sum of `item.price × item.qty` for all cart items
- **Delivery Fee**: `$2.99` if subtotal < $30, otherwise `FREE`
- **Tax**: 8% of subtotal
- **Total**: Subtotal + Delivery + Tax

---

## 📱 Responsive Breakpoints

```css
@media (max-width: 768px) {
  /* Hero becomes single column */
  /* Hero visual (floating emoji) is hidden */
  /* Nav links are hidden (cart button remains) */
}
```

The menu grid uses CSS `auto-fill` with a minimum card width of 280px, so it naturally reflows across all screen sizes.

---

## 🔧 Customization

### Adding Menu Items
Edit the `menuData` array in the `<script>` tag:
```javascript
{ 
  id: 13,                        // unique ID
  name: "New Item",
  desc: "Item description here",
  price: 12.99,
  emoji: "🌮",
  cat: "burger",                 // must match a category key
  badge: "New",                  // "" for no badge
  badgeClass: "",                // "veg" | "spicy" | ""
  rating: 4.7,
  reviews: 45
}
```

### Adding a New Category
1. Add a pill in the categories HTML:
   ```html
   <div class="cat-pill" onclick="filterMenu('newcat', this)">🌮 New Cat</div>
   ```
2. Set `cat: "newcat"` on relevant menu items.

### Changing Colors
Update CSS variables at the top of the `<style>` block:
```css
:root {
  --accent: #your-color;
}
```

---

## 🌐 Browser Compatibility

| Browser | Support |
|---|---|
| Chrome 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Edge 90+ | ✅ Full |
| IE 11 | ❌ Not supported |

---

## 📄 License

This project is open for personal and educational use. Feel free to modify and build upon it.

---

## 🙏 Credits

- Fonts: [Google Fonts](https://fonts.google.com) — Bebas Neue, DM Sans, Playfair Display
- Icons: Unicode emoji (no external icon library required)
- Built with: Pure HTML5, CSS3, and Vanilla JavaScript
