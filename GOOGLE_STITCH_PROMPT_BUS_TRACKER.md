# 3. 🎨 GOOGLE STITCH PROMPT FOR BUS TRACKING APP
## Ready to Copy-Paste

---

## 📋 COPY THIS ENTIRE PROMPT AND PASTE INTO GOOGLE STITCH

```
=== GOOGLE STITCH DESIGN BRIEF ===

PROJECT NAME: Real-Time Bus Tracker for University Campus

PROBLEM IT SOLVES:
Students struggle to know when buses arrive at campus stops. 
Current website shows outdated schedules. Students wait at bus stops 
without knowing when buses will actually arrive, causing stress and lateness to class.

TARGET USERS:
Primary: First-year university students (18-21 years old)
- Live in dorms or off-campus housing
- Commute 3-5 times per week
- Using smartphone (primary device)
- Tech-savvy but not developers

MAIN USER FUNCTIONS:
1. Select a bus route (dropdown)
2. View all buses on that route in real-time
3. See each bus's current location
4. See estimated arrival time (ETA) for next stop
5. Check bus capacity (full/not full)
6. See delay status (on-time, delayed, full)
7. Get notifications when bus arrives at their stop

TECHNICAL CONTEXT:
- Real-time bus data updates every 30 seconds
- Uses mock data (realistic bus simulation)
- Will eventually connect to real university API
- Mobile-first responsive design
- Built with React + Node.js backend

=== DESIGN REQUIREMENTS ===

VISUAL STYLE:
- Color Palette: Modern, professional, approachable
  * Primary Color: #028090 (deep teal) - for main elements and headers
  * Secondary Color: #00A896 (seafoam) - for accent boxes and highlights
  * Accent Color: #02C39A (mint) - for call-to-action buttons
  * Text Color: #2C3E50 (dark blue-gray) - for body text
  * Background: #F8F9FA (off-white) - for content areas
  * Status Colors:
    - Green (#27AE60) for "On Time" status
    - Red (#E74C3C) for "Delayed" or "Full" status
    - Orange (#F39C12) for warnings

- Typography: Clean, modern, easy to read
  * Headlines: Sans-serif, bold, 44-48pt
  * Subheadings: Sans-serif, regular, 24-28pt
  * Body Text: Sans-serif, regular, 16-18pt
  * Small Text: Sans-serif, regular, 12-14pt
  * Font: Helvetica Neue, Segoe UI, or similar (no serif fonts)

- Icon Style: Minimalist, line-drawn or emoji
  * Bus icon: 🚌
  * Location pin: 📍
  * Clock/Timer: ⏱️
  * People/Capacity: 👥
  * Checkmark/Success: ✅
  * Warning/Alert: ⚠️
  * Consistency: All icons should use same style throughout

- Overall Feel: Clean, modern, trustworthy, non-intimidating

USER EXPERIENCE PRINCIPLES:
- Minimize clicks: Main task (see bus ETA) should take ≤ 3 clicks
- Mobile-first: Design for phone first, then desktop
- Fast loading: Show buses immediately, no excessive loading
- Clear feedback: Every action has visual confirmation
- Consistent: Navigation and layout same across all screens
- Accessible: High contrast, large touch targets, keyboard navigation
- Real-time feel: Updates show immediately (within 30 seconds)

ACCESSIBILITY REQUIREMENTS:
- Text contrast: All text must have ≥ 4.5:1 contrast ratio
- Touch targets: All buttons/clickable areas ≥ 44x44 pixels
- Keyboard navigation: All features accessible without mouse
- Alt text: All icons and images have descriptions
- Color blind friendly: Don't rely on color alone for status (use text + icon)
- Simple language: Avoid jargon, use plain English
- Font size: Body text minimum 16pt, no smaller

=== REQUIRED SCREENS ===

SCREEN 1: LANDING/HOME SCREEN
Purpose: First impression, tell user what this app does, let them start

Content to show:
- App name and logo (or emoji 🚌)
- One-sentence tagline: "Real-Time Bus Tracking for UTM Campus"
- Brief benefit statement (2-3 lines):
  "Know exactly when buses arrive. Never wait wondering again."
- Large prominent button: "View Live Buses" or "Get Started"
- Small secondary buttons: "Learn More", "FAQ"
- Footer with: Version, University name, Contact info

Design notes:
- Hero image: Photo of campus bus or road with buses (if possible)
  OR use abstract design with teal + seafoam colors
- Should feel welcoming and trustworthy
- Mobile: Full-screen on phone, centered on desktop

---

SCREEN 2: AUTHENTICATION SCREENS (3 sub-screens)

2A. LOGIN SCREEN
Purpose: Let registered users sign in

Content:
- App logo/title at top
- Two input fields:
  * Email address field
  * Password field
- "Remember me" checkbox (optional)
- Large "Login" button (teal color #028090)
- "Forgot password?" link
- "Don't have account? Sign up" link at bottom

Design:
- Centered form, width ~400px max
- Input fields: 50px height, large text (16pt)
- Button: Full width of form, 50px height
- Mobile: Full-screen with padding

2B. SIGNUP/REGISTER SCREEN
Purpose: Let new users create account

Content:
- App logo/title at top
- Input fields:
  * Full name
  * Email address
  * Password
  * Confirm password
- Checkbox: "I agree to Terms of Service"
- Large "Create Account" button (teal)
- "Already have account? Login" link at bottom

Design:
- Same layout as login
- Show password strength indicator
- Mobile: Full-screen with padding

2C. PASSWORD RESET SCREEN
Purpose: Help users recover forgotten password

Content:
- "Forgot your password?" heading
- Brief instructions: "Enter your email, we'll send reset link"
- Email input field
- "Send Reset Link" button
- "Back to Login" link

Design:
- Centered form
- Mobile: Full-screen

---

SCREEN 3: MAIN DASHBOARD
Purpose: Main hub after user logs in, shows available routes

Content:
- Header:
  * Welcome message: "Welcome back, [Name]"
  * Your profile icon (small circle in top-right)
  
- Route Selection:
  * Heading: "Select a Route"
  * List of available routes as large clickable cards:
    - "Dorm → Central Campus" with bus emoji 🚌
    - "Science Park → Campus" 
    - "Night Service"
  * Each card shows: route name + number of buses running now

- Quick Info Section:
  * "All buses in operation: 15"
  * "Estimated average wait: 5 minutes"
  * "Most crowded route: Dorm → Campus"

- Bottom Navigation (for mobile):
  * Home icon (selected)
  * Tracker icon
  * Favorites icon (heart)
  * Settings icon

Design:
- Top: Centered header with welcome message
- Middle: Route cards in grid (2 columns on mobile, 3 on desktop)
- Each card: Clickable, shows route name + live bus count
- Card colors: Seafoam background, teal text
- Mobile: Full-width cards, scrollable list

---

SCREEN 4: PRIMARY FUNCTION - REAL-TIME BUS TRACKER
Purpose: MAIN SCREEN - Show all buses on selected route

Content:
- HEADER:
  * Back button (← arrow) to go back to dashboard
  * Route name: "Dorm → Central Campus" (22pt bold)
  * Last updated time: "Updated 30 seconds ago"

- ROUTE MAP/STOPS (optional):
  * If including map: Show route path with bus icons
  * If not map: Show list of stops in order
  * Current stop highlights

- BUS CARDS (Main content - This is critical):
  * Each bus shown as a card with:
    
    LAYOUT OF EACH BUS CARD:
    ┌──────────────────────────────────┐
    │ 🚌 BUS-101                       │
    │                                  │
    │ 📍 Currently at: Central Hub     │
    │ 🎯 Next stop: Library            │
    │ ⏱️  ETA: 3 minutes               │
    │ 👥 Capacity: 42/60 seats         │
    │ ✅ Status: On Time               │
    │                                  │
    │ [  Notify Me  ] [  Directions ]  │
    └──────────────────────────────────┘
    
  * Card colors by status:
    - On Time: White background, green status text
    - Delayed: White background, red "⚠️ 5 min delayed" text
    - Full: White background, red "🔴 Bus Full" text

  * Information in each card:
    - Bus ID (bold, 18pt)
    - Current location (with pin emoji 📍)
    - Next stop (with target emoji 🎯)
    - ETA in minutes (with clock emoji ⏱️) - large, prominent
    - Current capacity as "42/60" (with people emoji 👥)
    - Status badge:
      * ✅ On Time (green)
      * ⚠️ Delayed (red) with minutes
      * 🔴 Full (red)
    - Two action buttons:
      * "Notify Me" button (mint color #02C39A)
      * "Directions" button (outline style)

  * Card spacing: 10-15px between cards
  * Cards stack vertically (one per row)

- REFRESH CONTROL:
  * "Updates every 30 seconds" text at top (small, 12pt gray)
  * Manual refresh button: "🔄 Refresh Now" (top-right)

Design notes:
- Mobile: Cards full-width, stacked vertically, easily scrollable
- Desktop: Cards 2 per row (optional)
- Color coding by status: Green for good, red for problems
- Large ETA numbers (48pt minimum)
- Touch-friendly: All buttons ≥ 44x44 pixels
- No clutter: Only essential info per card

---

SCREEN 5: SECONDARY FUNCTION - FAVORITE STOPS
Purpose: Let users mark favorite stops for quick access

Content:
- Header: "My Favorite Stops"
- List of saved stops:
  * "Kolej Tun Razak" (Dorm area)
  * "Central Hub"
  * "Library"
  * Each with heart icon ❤️
  * Tap to remove from favorites
  
- Add new favorite:
  * "+ Add Stop" button

- When stop tapped:
  * Shows buses coming to that stop
  * Estimated arrival times

Design:
- List view with large touch targets
- Heart icon toggle (filled vs outline)
- Mobile: Full-width list, one item per row

---

SCREEN 6: DETAIL/VIEW SCREEN
Purpose: Detailed view of a single bus

Content when user taps on a bus card:
- Back button
- Bus ID: "BUS-101" (large)
- Route: "Dorm → Central Campus"
- Current location (with map pin)
- GPS coordinates (optional): 1.548°N, 103.742°E
- Full schedule:
  * Kolej Tun Razak → 7:00 AM
  * Kolej Chancellor → 7:05 AM (in 5 min)
  * Engineering Block → 7:10 AM
  * Central Hub (CURRENT) → 7:15 AM
  * Library → 7:20 AM
  * Main Campus Gate → 7:25 AM

- Actions:
  * [Share] button - share bus info with friend
  * [Set Reminder] button - get notified at arrival
  * [Report Issue] button - report problem (full bus, delayed, etc.)

Design:
- Scrollable detail view
- Visual progress through stops (checkmark for passed, arrow for current)
- Color-coded (green for completed, blue for current, gray for future)
- Mobile: Full-screen detail

---

SCREEN 7: SETTINGS/PREFERENCES
Purpose: Let users customize app

Content:
- Notification Settings:
  * Toggle: "Bus Arrival Alerts" (ON/OFF)
  * Toggle: "Delay Warnings" (ON/OFF)
  * Toggle: "Capacity Alerts" (ON/OFF)

- Preferences:
  * "Favorite Route" - dropdown to select default
  * "Preferred Stop" - dropdown
  * "Notification Time" - "5 min before, 2 min before, at arrival"

- Account:
  * Email: user@example.com
  * [Change Password] button
  * [Edit Profile] button

- About:
  * App Version: 1.0
  * "Privacy Policy" link
  * "Terms of Service" link
  * "Contact Support" link

- Danger Zone:
  * [Logout] button (red/orange)
  * [Delete Account] button (red)

Design:
- Simple list with toggles
- Grouping by category (Notifications, Preferences, Account, About)
- Settings icons for each section
- Mobile: Full-screen, scrollable

---

SCREEN 8: MOBILE RESPONSIVE VERSION
Purpose: Show how all above screens look on phone

Design principles:
- All content stacks vertically
- No horizontal scrolling
- Buttons are large (≥ 44x44 pixels)
- Touch-friendly spacing
- Bottom navigation bar (not top) for main sections
- Hamburger menu for secondary options

Bottom Navigation Bar (Mobile):
┌────────────────────────────────────┐
│ [🏠 Home] [🚌 Buses] [❤️ Fav] [⚙️] │
└────────────────────────────────────┘

Specific mobile changes:
- Bus cards: Full width, single column
- Route selector: Full-width buttons
- Map (if included): Thumb-friendly panning
- Typography: Slightly larger (touch-friendly)
- Spacing: More padding between elements

---

=== INTERACTION PATTERNS ===

LOADING STATE:
When app is fetching buses (top of screen):
"🔄 Loading bus data..."
Show skeleton screens of bus cards
(Gray placeholder cards with loading animation)

ERROR STATE:
If no buses available:
"No buses running on this route right now"
"Check back soon or select different route"

If API fails:
"Connection error. Please try again."
[Retry] button

EMPTY STATE:
When user first creates account (no favorites):
"No favorite stops yet"
"Tap the heart icon to save your favorite stops"
[Browse Routes] button

SUCCESS CONFIRMATION:
When user adds favorite:
Green checkmark ✅
"Added to favorites!"
(Toast notification, disappears after 2 seconds)

MODAL DIALOGS:
For confirmations:
"Are you sure you want to remove this favorite?"
[Cancel] [Confirm] buttons

For notifications:
"Bus arriving in 5 minutes"
[Got it] button

STATUS CHANGES:
When bus becomes full:
Card changes to red background
"🔴 This bus is full"
Option to check next bus

When bus is delayed:
Changes status to "⚠️ 5 min delayed"
Delay info highlights in orange/red

=== DESIGN SPECIFICATIONS ===

COMPONENT LIBRARY (Reusable Elements):

BUTTONS:
- Primary: Teal (#028090) background, white text, 50px height
- Secondary: Outline style, teal border, 50px height
- Danger: Red (#E74C3C) background, white text
- Small: 40px height (for secondary actions)
- Disabled: Gray, no hover effect

INPUT FIELDS:
- Border: Light gray (#CCCCCC), 2px
- Focus: Teal border (#028090), 2px
- Height: 50px
- Padding: 12px left/right
- Font: 16pt (no auto-zoom on iOS)

CARDS:
- Background: White (#FFFFFF)
- Border: 1px light gray (#E8E8E8)
- Border-radius: 8px
- Shadow: Subtle (0px 2px 4px rgba(0,0,0,0.1))
- Padding: 16px inside

STATUS BADGES:
- Size: 120px x 40px
- Border-radius: 20px (pill-shaped)
- Font: Bold 14pt
- Options:
  * Green (#27AE60): "✅ On Time"
  * Red (#E74C3C): "⚠️ Delayed" or "🔴 Full"
  * Gray (#95A5A6): "Not Running"

ICONS:
- Size: 20px for inline, 32px for section headers, 64px for large callouts
- Style: Consistent (all emoji or all line-drawn)
- Color: Match surrounding text color

NAVIGATION:
- Desktop top bar with logo, user profile
- Mobile bottom bar with 4 main sections
- Active state: Colored text/icon, underline
- Inactive state: Gray

SPACING:
- Page margin: 16px (mobile), 24px (desktop)
- Between cards: 12px
- Between sections: 24px
- Button padding: 12px top/bottom, 16px left/right

ANIMATIONS:
- Card tap: Slight scale effect (1.02x)
- Button hover: Darker shade of color
- Screen transitions: Slide from right (mobile), fade (desktop)
- Status changes: Smooth color transition (200ms)
- Refresh: Spinning icon during 2 seconds

TYPOGRAPHY HIERARCHY:
- Page title: 44pt bold, teal (#028090)
- Section header: 28pt bold, teal
- Card title: 18pt bold, dark gray
- Body text: 16pt regular, dark gray
- Caption: 12pt regular, medium gray
- Status: 14pt bold, color-coded (green/red)

COLOR PALETTE (FINAL):
- Primary Teal: #028090 (headers, main buttons, active states)
- Secondary Seafoam: #00A896 (accent boxes, secondary elements)
- Accent Mint: #02C39A (CTA buttons, highlights)
- Dark Text: #2C3E50 (body text, high contrast)
- Light Background: #F8F9FA (page background)
- White: #FFFFFF (cards, content areas)
- Success Green: #27AE60 (on-time status)
- Error Red: #E74C3C (delayed, full status)
- Warning Orange: #F39C12 (warnings)
- Border Gray: #CCCCCC (dividers, subtle borders)
- Disabled Gray: #95A5A6 (inactive elements)

=== DELIVERABLES EXPECTED ===

Please provide detailed designs or descriptions for:

1. WIREFRAMES
   - Sketch-style layouts for all 8 screens
   - Show positioning of elements
   - Label all major components
   - Annotate key interactions

2. VISUAL MOCKUPS
   - Full-color designs (use specified color palette)
   - Typography applied (fonts, sizes, weights)
   - Icons placed appropriately
   - Visual hierarchy clear

3. USER FLOWS
   - Show how user moves between screens
   - "Happy path": Select route → See buses → Tap bus → Get directions
   - Alternative paths: Add favorite, change settings, etc.

4. COMPONENT LIBRARY
   - Standard button styles (primary, secondary, danger)
   - Input field states (normal, focus, error, disabled)
   - Card variations (normal, delayed, full)
   - Status badges (on-time, delayed, full, not running)
   - Navigation patterns (top bar desktop, bottom bar mobile)

5. RESPONSIVE DESIGN
   - Show how screens adapt from mobile (375px) to desktop (1920px)
   - Breakpoints: 375px, 768px, 1024px, 1920px
   - Test readability at each size

6. DESIGN NOTES
   - Explain design decisions (why colors, spacing, layout)
   - Accessibility considerations
   - Performance notes (image optimization, etc.)
   - Browser/device compatibility

7. PROTOTYPE OR INTERACTIVE DEMO (if possible)
   - Show transitions between screens
   - Button interactions
   - Loading states
   - Form interactions

=== DESIGN PHILOSOPHY ===

✅ DO:
- Keep each screen focused on ONE primary task
- Use whitespace effectively to reduce clutter
- Make most important info (ETA) very prominent
- Use color to convey status (green=good, red=problem)
- Design for thumb (mobile buttons within easy reach)
- Show feedback for every user action
- Test on actual mobile devices
- Consider students in a rush (make it FAST to see ETA)

❌ DON'T:
- Overload screens with information
- Use decorative graphics that don't serve purpose
- Hide important actions in menus
- Make small text (minimum 14pt for body)
- Use color alone to convey information (add text/icon)
- Implement features "just because" (focus on core use case)
- Use hard-to-read fonts (stick to sans-serif)
- Make buttons too small (≥44x44 pixels)

=== TIMELINE EXPECTATIONS ===

Deliverable: Professional wireframes + visual mockups + user flows
Format: PDF or Figma file (shared link)
Quality: Portfolio-ready (this is for a student capstone project)
Notes: Should look professional enough to show employers

```

---

## 📋 HOW TO USE THIS PROMPT

### Step 1: Copy the Entire Prompt Above
Select all the text from:
```
=== GOOGLE STITCH DESIGN BRIEF ===
```
to the last line

### Step 2: Go to Google Stitch
Visit: https://www.google.com/design/stitch/

(Note: If Google Stitch is not available, alternatives:
- Figma (figma.com)
- Adobe XD
- Sketch)

### Step 3: Paste the Prompt
1. Create new project
2. Paste the entire prompt into the brief/description area
3. Click "Generate Design" or equivalent button

### Step 4: Review Generated Designs
Google Stitch (or similar tool) will create:
- ✅ Wireframe sketches
- ✅ Visual mockups with colors
- ✅ User flow diagrams
- ✅ Component library
- ✅ Mobile responsive versions

### Step 5: Export and Save
- Export as PDF or image files
- Save wireframes to your project folder
- Add link to your GitHub README

---

## ✅ WHAT YOU'LL GET

After sending this prompt to Google Stitch, you'll receive:

**Visual Assets:**
- 8 screen designs (landing, login, dashboard, bus tracker, favorites, detail, settings, mobile)
- Color palette applied (#028090, #00A896, #02C39A)
- Typography hierarchy shown
- Icons positioned correctly
- Component library (buttons, cards, badges, etc.)

**Documentation:**
- User flows showing screen transitions
- Design rationale explaining choices
- Responsive breakpoints (mobile, tablet, desktop)
- Accessibility notes
- Interaction patterns

**Deliverables:**
- Professional mockups (portfolio-ready)
- Wireframe sketches
- Component specifications
- Design guide

**Value for Your Project:**
- ✅ Professional UI/UX (no generic designs)
- ✅ Consistent with your bus tracking problem
- ✅ Mobile-first approach
- ✅ Accessible and usable
- ✅ Ready to show instructors/employers
- ✅ Can guide your React development

---

## 🚀 NEXT STEPS

1. ✅ Copy the prompt above
2. ✅ Go to Google Stitch (or Figma/Adobe XD)
3. ✅ Paste the prompt
4. ✅ Generate designs
5. ✅ Save designs to your project
6. ✅ Link designs in your GitHub README
7. ✅ Use as reference while coding React components

---

**This prompt gives Google Stitch (or similar AI design tool) everything it needs to create professional-grade UI/UX for your bus tracking app.** 🎨

The designs will show exactly what each screen should look like, making it much easier to code the React components afterwards!

