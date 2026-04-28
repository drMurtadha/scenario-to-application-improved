# 📖 FROM SCENARIO TO APPLICATION
## Complete Improved Guide - All Content in One File

**Version:** 2.0 | **Updated:** April 2026  
**For:** First-year Informatics Students | **Tool:** Claude Haiku 4.5

---

## 🎯 START HERE: Quick Navigation

### Your Situation?

**I have an app idea:**
→ Jump to [Section 2: The Framework](#section-2-the-framework)

**I don't have an idea:**
→ Jump to [Section 3: Common Mistakes](#section-3-common-mistakes) → [Section 4: 5 Real Examples](#section-4-5-complete-real-world-scenarios)

**I want to understand everything:**
→ Read this entire document top to bottom

**I'm teaching this:**
→ Jump to [Section 6: Teaching Guide](#section-6-teaching-and-integration-guide)

**I'm stuck and need help:**
→ Jump to [Section 8: Troubleshooting](#section-8-troubleshooting-quick-answers)

---

## SECTION 1: WHY THIS MATTERS

### The Problem Students Face

Most first-year Informatics students skip crucial steps:

```
❌ WRONG WAY
"I want to build an app" 
→ Choose tech stack 
→ Start coding 
→ Realize it doesn't solve anything

✅ RIGHT WAY
"What real problem?" 
→ Understand users 
→ Design process 
→ Then build
```

### The Statistics

- **70%** of student projects fail from poor planning
- **80%** of project failures are "solved wrong problem"
- **30%** of projects are actually used by target users
- **90%** of successful projects started with clear problem understanding

### Why Scenario-First Thinking Works

A well-defined scenario reveals:

- **Who** uses your system and why
- **What** process currently exists
- **Where** the pain points are
- **Why** the application will improve things
- **How** users will interact with it

---

## SECTION 2: THE FRAMEWORK

### The 8-Point Scenario Analysis

Every good scenario answers these 8 questions:

| # | Question | Example |
|---|----------|---------|
| 1 | **Target User** | Who is the primary person using this? | Mahasiswa semester 3 Teknik Informatika |
| 2 | **Context** | Where and when do they work? | Di perpustakaan UTM, during research hours |
| 3 | **Current Process** | What do they do manually today? | Cari jurnal via catalog fisik, catat referensi manual |
| 4 | **Pain Point** | What frustrates them? | Pencarian lambat, duplikasi referensi, format inconsistent |
| 5 | **Impact** | Why does it matter? | Tugas akhir tertunda, kehilangan waktu berharga |
| 6 | **Proposed Solution** | What should the app do? | Integrated digital journal finder with auto-citation |
| 7 | **Key Data** | What information is needed? | Journal title, authors, year, DOI, keywords, local availability |
| 8 | **Success Measure** | How do we know it works? | Waktu pencarian berkurang 50%, 0 duplikasi referensi |

---

## SECTION 3: COMMON MISTAKES TO AVOID

### ❌ Mistake 1: Over-Scoping

**What happens:**
```
"I'll build a complete academic management system!"
(tries to do: student grades, attendance, library, complaints, etc.)
```

**Why it fails:** First-year student can't build 7 modules in 4 weeks

**✅ How to avoid:**
```
Ask the "Cutting Questions":
- What's the SINGLE biggest pain point?
- Can I deliver minimum version in 2 weeks?
- Which 3 functions are absolutely critical?
- What can I defer to "Version 2.0"?
```

### ❌ Mistake 2: Solving for the Wrong User

**What happens:** You design for imagined users, not real ones

**✅ How to avoid:**
```
ASK ACTUAL USERS:
- How do you currently handle this task?
- What frustrates you most?
- What would make it easier?
- How many times per week would you use this?
```

### ❌ Mistake 3: Missing the Real Problem

**Example:**
```
Idea: "Make a homework tracking app"
Truth: Problem isn't tracking—it's motivation
Real solution: Might need gamification, not just lists
```

**✅ How to avoid:** Keep asking "Why?" five times

### ❌ Mistake 4: Building Before Designing

**What happens:** Code 2 weeks, then realize workflow is wrong

**✅ How to avoid:**
```
Follow this strict sequence:
1. Problem understanding (no code)
2. Requirements (on paper/doc)
3. Database design (on spreadsheet)
4. UI mockups (wireframes)
5. THEN code (based on solid plan)
```

### ❌ Mistake 5: Ignoring Edge Cases

**What happens:** App works for normal case but breaks for unusual ones

**✅ How to avoid:**
```
For each requirement, ask:
- What could go wrong here?
- How do we prevent it?
- What error message helps user fix it?
```

---

## SECTION 4: 5 COMPLETE REAL-WORLD SCENARIOS

### Scenario 1: Research Paper Library Management System

#### Raw Problem
```
"Students struggle to organize research papers for their thesis. 
They keep PDFs in messy folders and can't find them when they need them."
```

#### 8-Point Analysis

| Point | Answer |
|-------|--------|
| **1. Target User** | Final-year Informatics students doing thesis research |
| **2. Context** | At university, library, home office; during research phases |
| **3. Current Process** | Download PDFs → Save to folders → Search manually |
| **4. Pain Points** | Can't find papers, duplicate downloads, citation format inconsistency |
| **5. Impact** | Literature review takes 2x longer |
| **6. Proposed Solution** | Upload PDFs → auto-extract metadata → tagging system → integrated notes → export citations |
| **7. Key Data** | Paper ID, title, authors, year, keywords, PDF file, notes, tags |
| **8. Success Measure** | Literature review time reduced by 40% |

#### Database Structure
```
Sheet 1: PAPERS
- paper_id, title, authors, year_published, pdf_filename, date_added, rating, summary

Sheet 2: TAGS
- tag_id, tag_name, description

Sheet 3: PAPER_TAGS
- paper_id, tag_id, date_tagged

Sheet 4: NOTES
- note_id, paper_id, note_text, date_created, page_number
```

---

### Scenario 2: Campus Bus Schedule & Route Planner

#### Raw Problem
```
"Getting from my dorm to classes by bus is unpredictable. 
Bus times on the website are outdated."
```

#### 8-Point Analysis

| Point | Answer |
|-------|--------|
| **1. Target User** | UTM students living in dorms/off-campus, commuting 3-5x/week |
| **2. Context** | Morning rush (7-9 AM) getting to class |
| **3. Current Process** | Check website (outdated) or just wait and hope |
| **4. Pain Points** | No real-time bus location, outdated schedule, no capacity info |
| **5. Impact** | Students late to class, stress, miss important lectures |
| **6. Proposed Solution** | Real-time bus tracking → notification when bus arrives → route planner |
| **7. Key Data** | Bus ID, route ID, stop locations (GPS), scheduled time, actual arrival time, capacity |
| **8. Success Measure** | Average wait time < 10 min; lateness incidents decrease 80% |

---

### Scenario 3: Lab Equipment Booking System

#### Raw Problem
```
"Lab equipment is shared between 5 projects. 
We constantly have conflicts when two projects need the microscope at the same time."
```

#### 8-Point Analysis

| Point | Answer |
|-------|--------|
| **1. Target User** | Research lab members (grad students, lab staff) |
| **2. Context** | Planning experiments, need equipment for 2-8 hours |
| **3. Current Process** | Email lab manager → wait → hope no conflict → manually schedule |
| **4. Pain Points** | Double-booking conflicts, equipment damaged, no visibility on availability |
| **5. Impact** | Experiments delayed 1-2 weeks per conflict |
| **6. Proposed Solution** | Booking app with calendar view → one-click reservation → notifications |
| **7. Key Data** | Equipment ID, name, location, available hours, reservation_date, duration, status |
| **8. Success Measure** | Zero double-bookings; equipment available within 24 hours 95% of time |

---

### Scenario 4: Student Mental Health Resources Finder

#### Raw Problem
```
"I'm feeling stressed and need help, but I don't know which counselor 
to contact or what mental health resources are available."
```

#### 8-Point Analysis

| Point | Answer |
|-------|--------|
| **1. Target User** | UTM students experiencing stress, anxiety, pressure |
| **2. Context** | Late night, during exam period, using phone |
| **3. Current Process** | Google search → find university website → look for phone number → call or go in person |
| **4. Pain Points** | Hard to find right resource, shame/hesitation to call, unknown wait times |
| **5. Impact** | Students suffer alone; mental health issues worsen |
| **6. Proposed Solution** | "What are you feeling?" → matches to resource → shows availability → book or get phone # |
| **7. Key Data** | Concern type, counselor name, specialty, availability, phone, location |
| **8. Success Measure** | 50% more students reach out for help; average wait time < 3 days |

---

### Scenario 5: Sustainable Commute Planner (Carpooling)

#### Raw Problem
```
"I commute 45 minutes to campus alone every day. 
I'd save money and help environment if I could carpool, but I don't know anyone commuting from my area."
```

#### 8-Point Analysis

| Point | Answer |
|-------|--------|
| **1. Target User** | UTM students/staff living 30+ minutes away, commuting 3+ days/week |
| **2. Context** | Planning commute every weekday morning |
| **3. Current Process** | Drive alone OR post on Facebook → wait for responses → organize manually |
| **4. Pain Points** | No easy way to find partners, no trust/safety mechanism, logistics messy |
| **5. Impact** | Pollution, traffic, high commute cost |
| **6. Proposed Solution** | Carpool app: enter address → view others commuting same route → request to join → rate drivers |
| **7. Key Data** | User ID, home address, work address, commute days, departure time, capacity, rating |
| **8. Success Measure** | 200+ users; 50 active carpools; avg 400kg CO2 prevented per month |

---

## SECTION 5: CLAUDE HAIKU PROMPTS (Ready to Copy-Paste)

### Prompt 1: Problem Statement Clarification

```
You are an experienced software engineer mentoring a first-year Informatics student 
on application development. The student has a rough application idea but lacks clarity.

Your task: Help them understand the real problem before jumping to solutions.

STUDENT'S IDEA:
[PASTE THEIR 1-2 SENTENCE IDEA HERE]

Please help by:

1. **Identify the Core Problem**
   - What real-world issue is this trying to solve?
   - Is this a genuine problem or a solution in search of a problem?

2. **Define Target Users**
   - Who specifically would use this? (role, location, context)
   - How many users realistically?
   - What is their technical skill level?

3. **Analyze Current Process**
   - How do users currently handle this task?
   - What steps are involved?
   - Where does it fail or frustrate them?

4. **Extract Pain Points**
   - List 3-5 specific frustrations
   - Rate severity (high/medium/low)
   - How often do these occur?

5. **Define Impact**
   - What happens if the problem isn't solved?
   - How would the application improve things?
   - Measurable benefits?

6. **Realistic Scope Check**
   - Can a first-year student build a prototype in 4 weeks?
   - What's the minimum viable version?
   - What features should be deferred?

Use simple language. Be direct. Point out unrealistic ideas without being harsh.
Format your response as numbered sections with clear headings.
```

---

### Prompt 2: Functional & Non-Functional Requirements

```
Act as a Software Requirements Engineer. A student is developing an application based on this scenario:

SCENARIO:
[PASTE FULL PROBLEM STATEMENT HERE]

Generate:

1. **FUNCTIONAL REQUIREMENTS** (What the app must do)
   - Use format: "The system shall [action] so that [user benefit]"
   - Generate 5-7 requirements
   - Rank by priority (Must Have / Should Have / Nice to Have)

2. **NON-FUNCTIONAL REQUIREMENTS** (How well it performs)
   - Performance: Response time targets
   - Security: Data protection needs
   - Usability: Learning curve
   - Reliability: Uptime/availability
   - Scalability: How many users?

3. **USER STORIES** (Perspective of actual users)
   For each user type, write:
   "As a [user type], I want to [action], so that [benefit]"
   Generate at least 4 stories per user type

4. **CONSTRAINTS & ASSUMPTIONS**
   - Technical constraints
   - Business constraints
   - Assumptions about user behavior

Format as clean lists. Keep language simple for student readers.
```

---

### Prompt 3: Database Design for Google Sheets

```
You are designing a database structure for a student prototype using Google Sheets.

APPLICATION IDEA:
[PASTE APPLICATION IDEA OR SCENARIO HERE]

REQUIRED DELIVERABLE:

1. **Sheet Architecture**
   - How many sheets do you need? Name each one.
   - What's the purpose of each sheet?

2. **Data Structure for Each Sheet**
   For every sheet, provide:
   - Column names (use snake_case)
   - Data type (text, number, date, dropdown, etc.)
   - Example of 2-3 sample records

3. **Relationships**
   - Which sheets reference which?
   - Show using simple diagrams
   - Explain how to maintain data consistency

4. **Data Entry Workflow**
   - Who enters data into each sheet?
   - In what sequence should sheets be populated?
   - Any automatic calculations or formulas?

5. **Query Examples**
   - Show 2-3 common questions users might ask
   - Demonstrate how to find answers in your sheet structure

Use clear column names. Make it simple enough for non-technical person.
```

---

### Prompt 4: Project README Generator

```
Create a professional but student-friendly GitHub README.md file for this project:

PROJECT TITLE:
[PASTE APPLICATION TITLE]

SCENARIO:
[PASTE FULL PROBLEM STATEMENT]

APPLICATION PURPOSE:
[PASTE 2-3 SENTENCE DESCRIPTION OF WHAT IT DOES]

MAIN FUNCTIONS:
[PASTE LIST OF 5-7 KEY FEATURES]

TOOLS & TECHNOLOGIES:
[PASTE: Google Sheets, Google Stitch, Claude Haiku, GitHub, etc.]

---

Generate a complete README that includes:

1. **Project Title** (with emoji if appropriate)
2. **Quick Summary** (1 paragraph, clear problem + solution)
3. **Problem Statement** (2-3 paragraphs describing the real issue)
4. **Proposed Solution** (How the application solves it)
5. **Target Users** (Who benefits, how many, their context)
6. **Main Features** (Bulleted list with brief explanations)
7. **System Workflow** (User journey description)
8. **Database Structure** (Reference to Google Sheets with table list)
9. **User Interface** (Reference to designs, screen names)
10. **Installation & Usage** (How to access/use the prototype)
11. **Future Improvements** (3-5 features for later versions)
12. **Development Process** (What did you learn?)
13. **Author & Date** (Student name, semester, institution)

Use markdown formatting properly. Include section anchors. Keep language simple.
```

---

### Prompt 5: User Story & Acceptance Criteria Generator

```
You are writing detailed user stories for a student development project.

APPLICATION CONTEXT:
[PASTE APPLICATION IDEA]

For each of these user types, generate a detailed user story with acceptance criteria:

USER TYPE 1: [PASTE PRIMARY USER ROLE]
USER TYPE 2: [PASTE SECONDARY USER ROLE]
USER TYPE 3: [PASTE ADMIN/OPERATOR ROLE IF APPLICABLE]

---

For EACH user type, provide:

**USER STORY:**
As a [user type], I want to [action], so that [benefit].

**DETAILED SCENARIO (Given-When-Then format):**
- Given [initial context/condition]
- When [user performs action]
- Then [expected result/outcome]

**ACCEPTANCE CRITERIA:**
- Criterion 1: [Specific, measurable, testable]
- Criterion 2: [Specific, measurable, testable]
- Criterion 3: [Specific, measurable, testable]

**EDGE CASES:**
- What if [unusual situation]? System should [expected behavior]

**NOTES:**
- Any assumptions?
- Dependencies on other stories?
- Estimated effort (small/medium/large)

Generate 3-4 stories per user type, focusing on most important workflows first.
Use realistic scenarios based on how students actually work.
```

---

## SECTION 6: GOOGLE STITCH UI/UX DESIGN PROMPT

### The Complete Design Brief

```markdown
DESIGN CHALLENGE: Create an Beautiful, Intuitive Web Application Interface

=== PROJECT CONTEXT ===
Application Name: [INSERT YOUR APP NAME HERE]
Problem It Solves: [BRIEF 1-SENTENCE PROBLEM]
Target Users: [e.g., Students, Faculty, Staff - describe them briefly]

=== MAIN USER FUNCTIONS ===
[List the 5-7 most important actions users perform]

=== DESIGN REQUIREMENTS ===

✨ VISUAL STYLE:
- Color Palette: Modern (suggest primary & secondary colors)
- Typography: Clean, readable fonts
- Icon Style: Minimalist, intuitive
- Overall Feel: Professional yet approachable

🎯 USER EXPERIENCE PRINCIPLES:
- Minimize clicks to accomplish tasks (ideally 3 clicks maximum)
- Mobile-first responsive design
- Clear feedback for every user action
- Consistent navigation and layout

♿ ACCESSIBILITY:
- High contrast for readability
- Keyboard navigation support
- Alt text for images
- Simple language, avoid jargon

=== REQUIRED SCREENS ===

1. **LANDING/HOME SCREEN**
   - Hero headline (what problem does this solve?)
   - Quick stats or benefits
   - Clear call-to-action button
   - Navigation menu

2. **AUTHENTICATION SCREENS**
   - Login Screen
   - Register/Signup Screen
   - Password Reset Screen

3. **MAIN DASHBOARD**
   - Welcome message with user's name
   - Summary widgets
   - Navigation to main functions
   - Quick actions buttons
   - User profile menu

4. **PRIMARY FUNCTION SCREEN** (Most important user action)
   - Clear form or interface
   - Inline help/hints
   - Progress indicators if multi-step
   - Cancel & Save buttons
   - Success confirmation

5. **SECONDARY FUNCTION SCREEN**
   - Consistent layout with primary function
   - Filter/search capabilities
   - Table or card display of results
   - Actions per item

6. **DETAIL/VIEW SCREEN**
   - Breadcrumb navigation
   - Edit button
   - Related information
   - Print or export option

7. **ADMIN/MANAGEMENT DASHBOARD** (if applicable)
   - Statistical dashboard
   - User/data management table
   - Settings and configuration
   - Reports section

8. **MOBILE RESPONSIVE VERSION**
   - Stack all elements vertically
   - Hamburger menu for navigation
   - Larger touch targets
   - Bottom navigation for main functions

=== INTERACTION PATTERNS ===

Show designs for:
- **Loading States:** How does user know app is working?
- **Error Messages:** What happens when something goes wrong?
- **Empty States:** What does screen look like with no data yet?
- **Success Confirmations:** How do users know their action worked?
- **Modal Dialogs:** For confirmations and important info

=== DELIVERABLES ===

Please provide:
1. **Wireframe Sketches** for each screen
   - Simple, labeled layouts
   - Show all key elements
   - Include annotations

2. **Visual Design Mockups** (or detailed descriptions)
   - Color scheme applied
   - Typography shown
   - Icons placed
   - Visual hierarchy clear

3. **User Flow Diagram**
   - Show how user moves between screens
   - Highlight the critical path

4. **Component Library** (Optional)
   - Standard buttons (default, primary, danger)
   - Form inputs
   - Cards and containers
   - Navigation patterns

5. **Design Notes**
   - Design decisions and rationale
   - Accessibility considerations
   - Performance optimizations
   - Browser/device compatibility notes

=== DESIGN PHILOSOPHY ===

✅ DO:
- Keep it simple - one clear purpose per screen
- Use whitespace effectively
- Make CTAs prominent
- Test readability at smaller sizes
- Use existing UI patterns users know

❌ DON'T:
- Overload screens with information
- Use decorative elements without purpose
- Hide important actions in menus
- Use small text for important info
- Implement features "just because"

Generate comprehensive designs that answer all these points.
Include detailed descriptions if actual graphics aren't available.
Make it professional enough to show classmates, but realistic for what a student can build.
```

---

## SECTION 7: 30-MINUTE HANDS-ON ACTIVITY

### Part 1: Problem Discovery (8 minutes)

**Activity:**
1. **Individual** (3 min): Write a 2-sentence app idea
2. **With Claude Haiku** (5 min): Paste into Problem Clarification Prompt
3. **Read & Extract** (2 min): Identify your 8-point analysis

**Expected Output:**
A clear problem statement answering: Who? What? Where? Why? How?

---

### Part 2: Requirements Definition (7 minutes)

**Activity:**
1. **Copy** (1 min): Your problem statement from Part 1
2. **With Claude Haiku** (4 min): Paste into Functional Requirements Prompt
3. **Review** (2 min): Identify 3-4 critical functional requirements

**Expected Output:**
5-7 functional requirements + 3-4 user stories

---

### Part 3: UI/UX Sketching (8 minutes)

**Activity:**
1. **Prepare** (1 min): List your app's main 5 screens
2. **With Google Stitch Prompt** (5 min): Request wireframe designs
3. **Review & Iterate** (2 min): Note what you'd change

**Expected Output:**
Wireframe sketches showing user interface layout

---

### Part 4: Data Modeling (4 minutes)

**Activity:**
1. **With Claude Haiku** (3 min): Use Database Prompt
2. **Extract** (1 min): Get your Google Sheets structure

**Expected Output:**
3-4 sheet names with column definitions

---

### Part 5: Documentation (3 minutes)

**Activity:**
1. **With Claude Haiku** (2 min): Generate README
2. **Save** (1 min): Export to text file

**Expected Output:**
Professional GitHub README.md

---

## SECTION 8: TROUBLESHOOTING - QUICK ANSWERS

### **Problem: Claude Haiku gives vague answers**

**Solution:** Be more specific

```
❌ VAGUE:
"How should I design the user interface?"

✅ SPECIFIC:
"I'm building a complaint system for students. 
The main task is 'submit complaint with photo.' 
What are the steps I should show on screen?"
```

---

### **Problem: Prompt takes too long**

**Solution:** Reduce scope of question

```
❌ TOO MUCH:
"Generate all requirements, user stories, database, 
and UI design for my entire application"

✅ FOCUSED:
"Generate 5 functional requirements for the 'submit complaint' feature"
```

---

### **Problem: Your idea is too big**

**Solution:** Ask these cutting questions

```
- What's the SINGLE biggest pain point?
- Can I deliver minimum version in 2 weeks?
- Which 3 functions are absolutely critical?
- What can I defer to "Version 2.0"?

Example:
Original: "Complete campus facility management system"
Cut to: "Student complaints + status tracking"
```

---

### **Problem: Don't know where to start**

**Solution:** Follow this decision tree

```
Do you have an app idea?
  ├─ YES → Use Prompt 1 (Problem Clarification)
  └─ NO → 
      ├─ What frustrates YOU? (transportation, studying, connecting)
      ├─ What do peers struggle with?
      ├─ What campus process is broken?
      └─ Pick ONE problem

Then continue with Prompts 2-5
```

---

### **Problem: Can't decide which prompt to use**

**Solution:** Use this selector table

| I need... | Use This Prompt |
|-----------|-----------------|
| Validate my rough idea | Prompt 1 |
| Get functional requirements | Prompt 2 |
| Design database | Prompt 3 |
| Create GitHub README | Prompt 4 |
| Write detailed user stories | Prompt 5 |
| Design UI/screens | Google Stitch Prompt |

---

### **Problem: Not sure if scope is realistic**

**Solution:** Ask Claude directly

```
Copy this into Claude:
"Is this a good student project? Rate feasibility 1-10. Why?

[Describe your full feature list]"

Claude will either:
- Confirm scope is good ✅
- Suggest removing features ⚠️
- Warn you it's too big ❌
```

---

## SECTION 9: QUICK REFERENCE SUMMARY

### ⏱️ Timeline At a Glance

```
YOU HAVE 30 MIN?
↓
Use 5 prompts with Claude Haiku
↓
OUTPUT: GitHub repo with project spec ✓

YOU HAVE 60 MIN?
↓
Read this entire document + use prompts
↓
OUTPUT: Deep understanding + start coding ✓

YOU HAVE 4 WEEKS?
↓
Follow complete workflow (planning + build + test)
↓
OUTPUT: Finished application + portfolio-quality documentation ✓
```

---

### ✅ Final Checklist Before You Start Coding

- [ ] Problem statement is clear (show to instructor)
- [ ] Target user is specific and validated
- [ ] Scope is realistic (3-5 core features)
- [ ] Success metric is measurable
- [ ] Functional requirements are listed (5-7)
- [ ] User stories are written (at least 3-4)
- [ ] UI wireframes exist for all major screens (5+)
- [ ] Database structure is defined (sheet names + columns)
- [ ] GitHub repo is created with README
- [ ] All documents linked in README

**Only when ALL boxes are ✅ → Start coding**

---

## SECTION 10: TEACHING AND INTEGRATION GUIDE

### For Instructors: 45-Minute Live Session

```
TIMELINE    | ACTIVITY              | ACTION
============+=======================+===========================
0-5 min     | Opening & motivation  | Explain why planning matters
5-10 min    | Explain framework     | Show the 8-point analysis
10-15 min   | Live demo with Claude | Use Prompt 1 on example idea
15-30 min   | Student activity      | Students work through all 5 prompts
30-40 min   | Demos & feedback      | Students show their GitHub repos
40-45 min   | Q&A & next steps      | Clarify common confusion points
```

**Student Outcome:** GitHub repo with complete project specification

---

### For Your Course: Integration Options

**Option 1: One-Time Workshop**
- When: During early course modules
- Duration: 45 minutes
- Format: Live or recorded
- Deliverable: Each student gets GitHub repo with project spec

**Option 2: Mandatory Process for All Projects**
- Every student project must include:
  - ✅ Problem statement (8-point analysis)
  - ✅ Requirements (from Prompt 2)
  - ✅ UI/UX designs (from Google Stitch prompt)
  - ✅ Database structure (from Prompt 3)
  - ✅ GitHub README (from Prompt 4)

**Option 3: Progressive Integration**
- Week 1: Introduction to problem analysis (lecture)
- Week 2: Activity: Analyze a scenario (in-class)
- Week 3: Assignment: Create requirements for own idea
- Week 4: Assignment: Design UI for your app
- Week 5: Assignment: Plan database
- Week 6-13: Students code projects using specifications
- Week 14: Final presentations (show how you followed process)

---

### Grading Rubric Example

```
Problem Understanding: 20%
  - Clear problem statement
  - Identified real users
  - Identified real pain points
  - Realistic scope

Requirements Quality: 20%
  - 5-7 functional requirements (clear and testable)
  - 3-4 user stories (proper format)
  - Non-functional requirements addressed

Design Quality: 20%
  - UI/UX wireframes for 5+ screens
  - Professional appearance
  - Mobile responsive
  - Accessibility considered

Code Implementation: 25%
  - Matches specification
  - Clean and organized
  - Error handling
  - Well-commented

Documentation: 15%
  - GitHub README complete
  - Design files linked
  - Database documented
  - Reflection included
```

---

## HOW TO USE THIS DOCUMENT

### If You're a Student with an App Idea:

1. **Read** Section 2: The Framework (5 min)
2. **Jump to** Section 5: Use Claude Haiku Prompts 1-5 (30 min)
3. **Create** GitHub repo with results
4. **Share** link with instructor

**Total time:** 45 minutes → Ready to code ✓

---

### If You're a Student WITHOUT an Idea:

1. **Read** Section 4: 5 Complete Real Scenarios (20 min)
2. **Find** one similar to your situation
3. **Follow** same process with your own idea
4. **Continue** as above

**Total time:** 60 minutes → Ready to code ✓

---

### If You're an Instructor:

1. **Read** Section 6: Teaching Guide (10 min)
2. **Read** Sections 2-3: Framework & Common Mistakes (15 min)
3. **Plan** which integration option works for your course
4. **Create** assignment rubric using example provided
5. **Schedule** 45-minute session with students

**Total time:** 1 hour → Ready to teach ✓

---

### If You're Self-Teaching:

1. **Read** this entire document top to bottom (90 min)
2. **Review** Section 4: Real Examples (20 min)
3. **Use** all 5 prompts with Claude Haiku for YOUR idea (30 min)
4. **Design** UI using Google Stitch Prompt (30 min)
5. **Create** GitHub repo with all results

**Total time:** 3 hours → Professional specification ✓

---

## FINAL CHECKLIST

Before you submit your project, verify you have:

- [ ] Problem statement clearly written (2-3 sentences)
- [ ] 8-point scenario analysis complete (all 8 points answered)
- [ ] 5-7 functional requirements (tested, specific)
- [ ] 3-4 user stories with acceptance criteria
- [ ] Non-functional requirements addressed
- [ ] Database structure designed (sheet names + columns)
- [ ] UI/UX wireframes for 5-6 main screens
- [ ] GitHub repository created with professional README
- [ ] All design documents linked in README
- [ ] Code matches your specification
- [ ] User testing feedback documented
- [ ] Reflection on learning process included

**Have all of these?** You're doing it right. 🎉

---

## KEY METRICS YOU SHOULD SEE

### After 30 Minutes:
- ✅ Clear problem statement
- ✅ 5-7 functional requirements
- ✅ 3-4 user stories
- ✅ Database structure
- ✅ GitHub repo with README

### After 4 Weeks:
- ✅ Working application
- ✅ Professional UI/UX designs
- ✅ Complete documentation
- ✅ User testing feedback
- ✅ Portfolio-quality project

### Success Indicators:
- **Can explain problem in one sentence** ✓
- **Know exactly who your users are** ✓
- **Have written requirements (not vague ideas)** ✓
- **GitHub shows planning, not just code** ✓
- **Users actually find your app helpful** ✓

---

## REMEMBER

> **The difference between a failed project and a successful one is often not code quality—it's problem understanding.**

When you truly understand the problem, the solution becomes obvious. The code is just the easy part.

---

**Version:** 2.0  
**Created:** April 2026  
**For:** First-year Informatics Students  
**With:** Claude Haiku 4.5  
**Time:** 30 minutes to plan, 4 weeks to build  
**Outcome:** Professional application + project portfolio

**Made with ❤️ for students who want to build things that matter.**

