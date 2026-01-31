# Block Diagram Auction System

An IPL-style auction game for the Crayfish Axon EPSP/IPSP studio session.

## What's Included

1. **student_bidding.html** — The student interface where teams place bids
2. **instructor_dashboard.html** — Your control panel to see all bids, run the timer, and view results
3. **google_apps_script.js** — Backend code that stores bids in Google Sheets

## How It Works

1. Teams join with a team name
2. They see all 16 sets of model components
3. Each team has 100 points to allocate across items
4. They can see other teams' bids updating live
5. When time runs out (or you freeze), highest bid wins each item
6. Teams must then negotiate/trade to get missing pieces they need

---

## Setup Instructions

### Step 1: Set Up Google Sheets Backend

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Name it "Block Diagram Auction"
3. Go to **Extensions > Apps Script**
4. Delete any code there
5. Copy the entire contents of `google_apps_script.js` and paste it
6. Save (Ctrl+S or Cmd+S)
7. In the Apps Script editor, run the function `initialSetup` once:
   - Click the dropdown next to "Debug" and select `initialSetup`
   - Click "Run"
   - Authorize when prompted
8. Deploy as web app:
   - Click **Deploy > New deployment**
   - Click the gear icon and select **Web app**
   - Set "Execute as": **Me**
   - Set "Who has access": **Anyone**
   - Click **Deploy**
9. **Copy the Web App URL** — you'll need this!

### Step 2: Update the HTML Files

1. Open `student_bidding.html` in a text editor
2. Find this line (around line 320):
   ```javascript
   const API_URL = 'YOUR_GOOGLE_APPS_SCRIPT_URL';
   ```
3. Replace `YOUR_GOOGLE_APPS_SCRIPT_URL` with your actual Web App URL from Step 1
4. Save the file
5. Do the same for `instructor_dashboard.html` (around line 230)

### Step 3: Host on GitHub Pages

1. Go to github.com
2. Create a new repository called `block-auction` (make it Public)
3. Upload both HTML files (student_bidding.html and instructor_dashboard.html)
4. Go to Settings > Pages
5. Under "Source", select **main** branch
6. Save and wait 1-2 minutes

Your URLs will be:
```
https://YOUR_USERNAME.github.io/block-auction/student_bidding.html
https://YOUR_USERNAME.github.io/block-auction/instructor_dashboard.html
```

---

## Running the Auction

### Before Class
1. Open the instructor dashboard
2. Make sure the Google Sheet is empty (or click Reset)
3. Share the student URL with teams

### During Class
1. Give teams 2-3 minutes to look at the items
2. Click **Start** on your dashboard
3. Watch the live bids come in
4. Call out interesting trends: "Everyone wants Set 3!" or "Nobody's bidding on Geometry!"
5. At the end, click **Freeze** (or let timer run out)
6. Review results in the **Winners** tab

### After Auction
1. Show which items each team won
2. Identify what's missing from each team's model
3. Teams must negotiate to get missing pieces (this is the learning!)

---

## The Penalty System

When teams need items they didn't win, options:

1. **Trade** — Give up something they won
2. **Answer a challenge question** — You ask, they explain why they need it
3. **Justify to class** — They must explain publicly why this item is essential
4. **Lose points** — If you have a scoring system

---

## Customization

### Change the Timer
In both HTML files, find:
```javascript
const AUCTION_DURATION = 15 * 60; // 15 minutes in seconds
```
Change `15` to whatever you want.

### Change the Budget
Find:
```javascript
const TOTAL_BUDGET = 100;
```

---

## Troubleshooting

**Bids not showing up?**
- Check that the API_URL is correct in both HTML files
- Make sure the Apps Script is deployed with "Anyone can access"
- Check browser console for errors (F12 > Console)

**"Authorization required" error?**
- Go back to Apps Script
- Run `initialSetup` again and authorize

**Students can't access the page?**
- Make sure your GitHub repo is Public
- Make sure GitHub Pages is enabled
- Wait a few minutes after enabling

---

## Demo Mode

If the Google Sheets backend isn't connected, both pages will still work — they'll just show demo data. Good for testing the interface before class.
