[README-2.md](https://github.com/user-attachments/files/25163021/README-2.md)
# 🍎 Macro Calculator

A professional, cloud-synced macro tracking web application for managing your nutrition across multiple devices.

![Version](https://img.shields.io/badge/version-4.0-blue)
![Firebase](https://img.shields.io/badge/firebase-enabled-orange)
![Mobile](https://img.shields.io/badge/mobile-optimized-green)

---

## ✨ Features

### 📊 Food Database
- **Add & manage foods** with detailed nutrition info
- **Custom serving sizes** (g, oz, lb, cup, tbsp, tsp, ml, fl oz, piece, serving)
- **Custom calories** or auto-calculated from macros
- **Searchable & sortable** alphabetical list
- **Export/Import CSV** for bulk editing
- **Compact table view** with color-coded macros

### 🍽️ Meal Builder
- **Create custom meals** from your food database
- **Real-time macro totals** as you build
- **Multiple servings** - define how many servings each meal makes
- **Per-serving calculations** automatically updated
- **Edit saved meals** anytime
- **P/Cal ratio** column to track protein density
- **Searchable dropdown** for quick food selection

### 📅 Daily Tracking
- **Add saved meals OR individual foods** to your day
- **Adjustable portions** - edit serving sizes after adding
- **Daily totals badge** at top with macro percentages
- **Clear Day** button with undo safety (10-second window)
- **Type badges** - distinguish between meals and individual foods
- **Table format** for easy scanning

### ☁️ Cloud Sync
- **4-digit PIN** authentication system
- **Auto-sync across all devices** (phone, tablet, laptop)
- **Real-time updates** when data changes on another device
- **Offline support** - changes sync when back online
- **Secure Firebase backend** - each PIN has isolated data

### 📱 Mobile Optimized
- **Responsive design** for all screen sizes
- **Touch-friendly** interfaces
- **Horizontal scrolling tables** on small screens
- **Compact layouts** that fit mobile viewports
- **No horizontal overflow** - everything stays within screen

---

## 🚀 Quick Start

### Installation

1. **Download the HTML file:**
   ```
   macro-calculator-v4.html
   ```

2. **Open in your browser:**
   - Double-click the file, OR
   - Right-click → Open with → Your browser

3. **Set your PIN:**
   - Enter any 4-digit PIN (e.g., `1234`)
   - This creates your account in the cloud
   - **Remember this PIN!** You'll need it on other devices

### First Steps

1. **Add Foods** (Food Database page)
   - Click "Add Food"
   - Enter: Name, Serving Size, Protein, Carbs, Fats
   - Optional: Fiber, Custom Calories
   - Click "Add to Database"

2. **Create Meals** (Create Meal page)
   - Enter meal name (e.g., "Breakfast Bowl")
   - Set total servings (how many the recipe makes)
   - Search and add foods
   - Adjust amounts/units for each ingredient
   - Click "Save Meal"

3. **Track Your Day** (My Day page)
   - Toggle between "Saved Meals" or "Individual Foods"
   - Search and select items
   - Set portion size
   - Click "Add to Day"
   - Watch your daily totals update!

---

## 📖 User Guide

### Food Database

#### Adding Foods
```
Example:
Name: Chicken Breast
Serving: 100g
Protein: 31g
Carbs: 0g
Fats: 3.6g
Fiber: 0g
Calories: (auto-calculated = 165)
```

#### Editing Foods
- Click **"Edit"** button on any food
- Modify values
- Click "Update Food"

#### Bulk Import/Export
1. Click **"⬇ Export"** to download CSV
2. Edit in Excel/Google Sheets
3. Click **"⬆ Import"** to upload
4. Choose **Replace** (wipe & reload) or **Merge** (update existing)

**CSV Format:**
```csv
id,name,servingAmount,servingUnit,protein,carbs,fats,fiber,calories,customCalories
123,Chicken Breast,100,g,31,0,3.6,0,165,false
```

### Meal Builder

#### Creating Meals
1. Enter meal name: `"Protein Smoothie"`
2. Set servings: `2` (makes 2 smoothies)
3. Add ingredients:
   - Whey Protein: 30g
   - Banana: 1 piece
   - Almond Milk: 200ml
4. See totals update in real-time
5. Click "Save Meal"

#### P/Cal Ratio
- Shows protein density: `(Protein × 10) / Calories`
- Higher = more protein per calorie
- Example: 30g protein, 150 calories = **2.0** P/Cal ratio

#### Editing Saved Meals
- Click **"Edit"** on any saved meal
- Meal loads into builder
- Modify ingredients or servings
- Click "Update Meal"

### Daily Tracking

#### Adding Items

**Option A: Saved Meals**
1. Click "Saved Meals" tab
2. Search for meal: `"Protein Smoothie"`
3. Set servings: `1.5` (want 1.5 smoothies)
4. Click "Add Meal to Day"

**Option B: Individual Foods**
1. Click "Individual Foods" tab
2. Search for food: `"Chicken Breast"`
3. Set amount: `150g`
4. Click "Add Food to Day"

#### Understanding the Difference
- **Meals**: Can adjust servings after adding (editable)
- **Foods**: Amount locked after adding (not editable)

#### Daily Totals
- **Protein/Carbs/Fats**: Shows grams + % of total calories
- **Calories**: Total for the day
- **Fiber**: Total grams

#### Clear Day
- Click **"Clear Day"** → Confirms → All items removed
- **"Undo Clear"** button appears for 10 seconds
- Click undo to restore everything
- After 10 seconds, undo option disappears

---

## ☁️ Cloud Sync Setup

### Initial Setup (One Time)

1. **Create Firebase Project:**
   - Go to https://console.firebase.google.com/
   - Click "Add project"
   - Name it (e.g., "macro-tracker")
   - Disable Google Analytics
   - Click "Create project"

2. **Enable Realtime Database:**
   - Click "Realtime Database" in left menu
   - Click "Create Database"
   - Choose location (United States or closest)
   - Start in **test mode**
   - Click "Enable"

3. **Set Security Rules:**
   - Go to "Rules" tab
   - Replace with:
   ```json
   {
     "rules": {
       "$pin": {
         ".read": true,
         ".write": true
       }
     }
   }
   ```
   - Click "Publish"

4. **Get Your Config:**
   - Click ⚙️ gear → Project settings
   - Scroll to "Your apps"
   - Click `</>` (web icon)
   - Register app name
   - Copy the `firebaseConfig` object

5. **Update HTML File:**
   - Open `macro-calculator-v4.html` in text editor
   - Find `const firebaseConfig = {`
   - Replace with your config
   - Save file

### Using Across Devices

**First Device (e.g., Laptop):**
1. Open app
2. Enter PIN: `1234`
3. Add foods, meals, daily tracking

**Second Device (e.g., iPhone):**
1. Open same HTML file
2. Enter **same PIN**: `1234`
3. All data appears!

**Syncing:**
- Changes on any device sync automatically
- Other devices update in real-time
- Works offline - syncs when reconnected

---

## 🔐 Security & Privacy

### PIN System
- **4-digit numeric PIN** (0000-9999)
- Each PIN gets isolated data space
- PIN `1234` cannot see PIN `5678`'s data
- Like a password - keep it private!

### Data Storage
- **Firebase Realtime Database** (Google Cloud)
- **Encrypted in transit** (HTTPS)
- **Free tier**: 1GB storage, 10GB/month bandwidth
- **Data retention**: Until you delete it

### Sharing Access
- Share your PIN = share full access to data
- Good for: Family members, couples tracking together
- **No recovery**: Lost PIN = lost access (no reset option)

### Local Backup
- Data also stored in browser `localStorage`
- Works offline using local copy
- CSV Export for manual backups

---

## 📊 Macro Calculations

### Auto-Calculated Calories
```
Calories = (Protein × 4) + (Carbs × 4) + (Fats × 9)
```

### Custom Calories
Use when:
- Alcohol content (7 cal/g)
- Sugar alcohols (2 cal/g)
- Package label doesn't match formula
- Rounding differences

### Macro Percentages
```
Protein % = (Protein grams × 4 / Total Calories) × 100
Carbs % = (Carbs grams × 4 / Total Calories) × 100
Fats % = (Fats grams × 9 / Total Calories) × 100
```

Example:
- 150g protein = 600 cal (40%)
- 150g carbs = 600 cal (40%)
- 33g fats = 300 cal (20%)
- Total = 1500 calories

### P/Cal Ratio
```
P/Cal = (Protein grams × 10) / Calories
```

Examples:
- **2.0 or higher** = Very high protein (protein powder, lean meat)
- **1.0-2.0** = High protein (chicken, fish, Greek yogurt)
- **0.5-1.0** = Moderate protein (whole eggs, nuts)
- **Below 0.5** = Low protein (fruits, grains, fats)

---

## 🔄 Unit Conversions

The app converts all units to grams (solid) or milliliters (liquid) for calculations:

### Weight (to grams)
- `1 oz = 28.35 g`
- `1 lb = 453.592 g`
- `1 piece = 1 g` (placeholder)
- `1 serving = 1 g` (defined by you)

### Volume (to ml)
- `1 cup = 240 ml`
- `1 tbsp = 15 ml`
- `1 tsp = 5 ml`
- `1 fl oz = 30 ml`

**Note:** Volume-to-weight conversions assume water density. Actual weights vary by food (e.g., 1 cup flour ≠ 1 cup water in grams).

---

## 💡 Tips & Best Practices

### Food Database
- ✅ Use **piece** for discrete items (1 apple, 1 egg, 1 protein bar)
- ✅ Use **serving** for packaged foods (1 serving = label info)
- ✅ Use **grams** for precise tracking (weigh with kitchen scale)
- ✅ Export CSV regularly as backup

### Meal Building
- ✅ Create meals for **frequently eaten combinations**
- ✅ Set servings to **batch size** (meal prep)
- ✅ Use P/Cal ratio to **optimize protein intake**
- ✅ Edit meals when recipes change

### Daily Tracking
- ✅ Add **meals** when eating prepared recipes
- ✅ Add **individual foods** when eating single items
- ✅ Adjust portions **before** adding (can't edit foods after)
- ✅ Clear day at midnight to start fresh

### Mobile Usage
- ✅ Scroll tables horizontally to see all columns
- ✅ Use search boxes to find foods quickly
- ✅ Pin to home screen for app-like experience
- ✅ Works offline - syncs when reconnected

---

## 🐛 Troubleshooting

### PIN Issues

**"I forgot my PIN"**
- No recovery option currently
- Data is locked to that PIN
- Start new PIN with fresh data

**"Data not syncing"**
- Check internet connection
- Verify same PIN on both devices
- Check browser console for errors
- Reload page to force sync

### Data Issues

**"My food disappeared"**
- Check if you're using same PIN
- Different browsers = different localStorage
- Export CSV regularly as backup

**"Import failed"**
- Check CSV format (see example above)
- Ensure headers match exactly
- Look for special characters in food names

### Mobile Issues

**"Table too wide"**
- Swipe left/right to scroll table
- Portrait mode recommended
- Zoom out if needed

**"Buttons cut off"**
- Rotate to landscape
- Scroll down to see all buttons
- Update to latest version

### Firebase Issues

**"Sync not working"**
- Check Firebase console (database created?)
- Verify security rules published
- Check browser console for errors
- Try incognito mode (cache issues)

---

## 📱 Browser Compatibility

### Fully Supported
- ✅ Chrome (Desktop & Mobile)
- ✅ Safari (Desktop & iOS)
- ✅ Firefox (Desktop & Mobile)
- ✅ Edge (Desktop & Mobile)

### Minimum Requirements
- JavaScript enabled
- LocalStorage enabled
- Internet connection (for cloud sync)

### Recommended
- **Desktop**: Chrome, Firefox, Edge
- **Mobile**: Safari (iOS), Chrome (Android)
- **Screen size**: 360px width minimum

---

## 🔄 Version History

### v4.0 (Current)
- ✅ Firebase cloud sync with PIN authentication
- ✅ Searchable dropdown selectors
- ✅ Mobile-optimized responsive design
- ✅ Import/Export CSV functionality
- ✅ P/Cal ratio column
- ✅ Macro percentage display
- ✅ Clear Day with undo
- ✅ Table-based compact layouts

### v3.0
- ✅ Individual food tracking on My Day
- ✅ Piece/item unit support
- ✅ Custom calories field
- ✅ Real-time meal totals
- ✅ Editable saved meals

### v2.0
- ✅ Meal builder functionality
- ✅ Daily tracking page
- ✅ LocalStorage persistence

### v1.0
- ✅ Food database
- ✅ Basic macro tracking

---

## 🤝 Contributing

This is a single-file HTML application. To modify:

1. Open `macro-calculator-v4.html` in text editor
2. Edit HTML/CSS/JavaScript directly
3. Save and reload in browser
4. Test thoroughly before deploying

### Key Files
- **HTML**: Lines 1-500 (structure)
- **CSS**: Lines 500-700 (styling)
- **JavaScript**: Lines 700-2000+ (functionality)

### Firebase Config
- Located at top of `<script>` section
- Replace with your own config if deploying publicly
- Never share your config publicly (API keys visible)

---

## 📄 License

This project is provided as-is for personal use.

### You CAN:
- ✅ Use for personal macro tracking
- ✅ Modify for your own needs
- ✅ Share with friends/family
- ✅ Host on your own server

### You CANNOT:
- ❌ Sell this application
- ❌ Claim as your own creation
- ❌ Remove attribution

---

## 🆘 Support

### Common Questions

**Q: Can I use this without internet?**
A: Yes, but cloud sync requires internet. Data saves locally regardless.

**Q: How much does Firebase cost?**
A: Free tier supports ~100 users. Paid plans start at $25/month.

**Q: Can I change my PIN?**
A: Yes, click "Change PIN" on login screen. Old data stays with old PIN.

**Q: Does this work on iPhone?**
A: Yes! Open in Safari. Add to home screen for app-like experience.

**Q: Where is my data stored?**
A: Both locally (browser localStorage) and cloud (Firebase).

**Q: Can I track multiple days?**
A: Currently tracks one day at a time. Export data before clearing.

### Getting Help

1. Check this README first
2. Check browser console for errors (F12)
3. Try incognito/private mode
4. Clear browser cache and reload
5. Export data before troubleshooting

---

## 🎯 Roadmap

### Potential Future Features
- Multiple day history
- Charts and trends
- Export daily logs to PDF
- Meal templates
- Barcode scanning
- Recipe scaling calculator
- Water intake tracking
- Weight tracking
- Goal setting

---

## 🙏 Credits

**Built with:**
- Vanilla JavaScript (no frameworks)
- Firebase Realtime Database
- HTML5 & CSS3
- LocalStorage API

**Inspired by:**
- MyFitnessPal
- Cronometer
- LoseIt

---

## 📞 Contact

For bugs, feature requests, or questions:
- Open an issue on GitHub (if applicable)
- Email: [your-email@example.com]
- Twitter: [@yourusername]

---

**Made with ❤️ for the fitness community**

Last updated: February 2026
Version: 4.0
