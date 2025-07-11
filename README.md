# Warframe Market API Tools

A collection of tools for interacting with the Warframe Market API, including a Prime Set Trading Analyzer and authentication system.

---

## Features

### 🔐 Authentication System
- **Login/Logout functionality** using Warframe Market v1 API
- **JWT token management** with automatic session handling
- **Authentication status indicators** on all pages
- **Secure credential handling** with proper session management

### 📊 Prime Set Trading Analyzer
- **Prime Set Analysis:** Scans all Warframe Prime sets for the best buy/sell gaps.
- **Live Market Data:** Fetches real-time public orders from Warframe.market.
- **Smart Filtering:**
  - Only considers "ingame" (active) orders.
  - Adjustable max order age (slider, in days).
  - Minimum profit and max investment filters.
- **Realistic Trading Logic:**
  - Buy at (highest WTB + 1), sell at (lowest WTS - 1).
  - Shows only actionable, realistic opportunities.
- **Order Age Visualization:**
  - Buy price cell is color-coded by order age (green = fresh, red = stale).
  - Table shows the age (in days) of the best WTB order.
- **Top Opportunities Table:**
  - Ranks and displays the top 20 arbitrage opportunities.
  - Includes ROI, net profit, quantity, and total investment.
- **One-Click Analysis:**
  - Simple UI: set your filters, click "Analyze All Prime Sets," and see results.
- **Stop Analysis:**
  - Cancel a long scan at any time with the "Stop Analysis" button.

### 🔍 Syndicate Mod Search
- **Search syndicate mods** by syndicate name
- **Real-time pricing** from Warframe Market
- **Filter by mod type** and rank
- **Time range filtering** for order age
- **Order mode selection** (online only vs all orders)

---

## Setup Instructions

### Prerequisites
- Python 3.x
- Modern web browser

### Installation & Running
1. **Clone or download this repository.**
2. **Start the Python proxy server:**
   ```bash
   python proxy_server.py
   ```
3. **Open your browser** and go to:
   ```
   http://localhost:8000
   ```

---

## How to Use

### Authentication
1. **Navigate to the Login page** using the navigation menu
2. **Enter your Warframe Market credentials** (email and password)
3. **Check authentication status** - a green indicator shows when logged in
4. **Logout** when finished using the logout button

### Trading Calculator
1. **Set your filters:**
   - Minimum profit (platinum)
   - Maximum investment (platinum)
   - Max order age (slider)
2. **Click "Analyze All Prime Sets"**
3. **Watch the progress bar** and see the top opportunities populate the table.
4. **Review results:**
   - Buy/Sell prices, order age, ROI, net profit, and more.
5. **Stop analysis** at any time with the "Stop Analysis" button.
6. **Clear the table** with the "Clear Table" button.

### Syndicate Search
1. **Enter a syndicate name** (e.g., "Steel Meridian", "Red Veil")
2. **Adjust filters** as needed (rank, order mode, time range)
3. **View results** sorted by price and availability

---

## Authentication Details

The authentication system uses the Warframe Market v1 API:
- **JWT-based authentication** with automatic token refresh
- **Session management** with 1-hour validity
- **Secure credential handling** - credentials are not stored locally
- **CORS handling** through the proxy server

**Note:** Authentication is currently independent of the trading features. Logged-in sessions may be used for future authenticated API calls.

---

## Limitations & Known Issues

- **No Order Creation:** This tool does not create or manage orders on Warframe.market.
- **Some Orders Missing:** Some orders visible on the Warframe.market website (notably those with a special icon next to the profile picture) may not appear in this app. These orders are not present in the public API and cannot be fetched programmatically.
- **API Rate Limits:** The tool is rate-limited to avoid being blocked by Warframe.market. Large scans may take a minute or two.
- **Data Freshness:** Results are only as fresh as the public API allows. Some stale orders may appear if not yet purged from the API.
- **Authentication Scope:** Currently, authentication is separate from trading features. Future updates may integrate authenticated API calls.

---

## Project Structure

```
warframe_api/
├── index.html                 # Syndicate search page
├── trading-calculator.html    # Trading calculator UI
├── login.html                 # Authentication page
├── script.js                  # Syndicate search logic
├── trading-calculator.js      # Trading calculator logic
├── login.js                   # Authentication logic
├── style.css                  # App styling
├── proxy_server.py            # Python proxy server (CORS + API proxy)
├── auth_handler.py            # Authentication backend
├── syndicate_items.json       # Syndicate mod data
├── test_auth.py               # Authentication testing
├── README.md                  # This file
├── LICENSE                    # License info
└── .gitignore                 # Git ignore rules
```

---

## API Endpoints

### Backend Endpoints (via proxy server)
- `GET /auth/status` - Check authentication status
- `POST /auth/login` - Login with credentials
- `POST /auth/logout` - Logout and clear session

### Frontend Pages
- `/` - Syndicate search (index.html)
- `/trading-calculator.html` - Trading calculator
- `/login.html` - Authentication page

---

## Credits & Acknowledgments

- **Warframe.market** for their public API and market data.
- **Digital Extremes** for Warframe and the Warframe API.
- **You!** For using, testing, and improving this tool.

---

## License

MIT License — see LICENSE for details.

---

## Disclaimer

This tool is for educational and personal use only. Use at your own risk. The developers are not responsible for any trading losses, account issues, or market changes. Not affiliated with Digital Extremes or Warframe.market. 