# LoreLog

> **A personal learning tracker built to turn long-term learning goals into structured plans and keep a record of what I actually did.**

LoreLog is a web application I am building **for myself**.

I wanted a way to take something vague like:

```text
"Become good at AI/ML"
```

and turn it into something I can actually work through:

```text
AI/ML
├── Mathematics
│   ├── Linear Algebra
│   ├── Probability
│   └── Statistics
│
├── Machine Learning
│   ├── Regression
│   ├── Classification
│   └── Decision Trees
│
└── Deep Learning
    ├── Neural Networks
    ├── CNNs
    └── Transformers
```

But I also wanted to keep track of what actually happened after creating the plan.

That led to the core idea behind LoreLog:

> **What I plan to learn ≠ What I actually did.**

---

# Why I Made LoreLog

Most simple productivity systems answer:

> **"Did I complete this task?"**

That isn't really what I wanted.

When learning something over months or years, I want to know:

* What am I trying to learn?
* How did I break it down?
* What am I supposed to work on next?
* What did I actually work on today?
* How much time did I spend?
* What have I completed?
* What have I neglected?
* What did I struggle with?
* What have I actually learned over time?

A learning roadmap tells me **what I intend to do**.

A daily log tells me **what I actually did**.

LoreLog is meant to connect the two.

It is not intended to be a commercial productivity product. It is a personal project that I am building to solve my own problem while also using the project to learn how real applications are designed and built.

---

# The Core Idea

LoreLog separates **planned learning** from **actual activity**.

### Planned Learning

This describes the structure of what I want to learn.

```text
Main Plan
└── Sub Plan
    └── Plan Item
```

### Actual Learning

This describes what I actually did.

```text
Daily Activity
├── Date
├── Main Plan
├── Sub Plan
├── Plan Item
├── Description
├── Time Spent
├── Status
└── Notes
```

For example:

```text
Machine Learning
└── Supervised Learning
    └── Linear Regression
```

could result in:

```text
August 17, 2026

Machine Learning
→ Supervised Learning
→ Linear Regression

Activity:
"Studied gradient descent and implemented a basic example."

Time:
1h 40m

Status:
Completed
```

The **plan represents the journey**.

The **activity represents the journey that actually happened**.

Multiple activities can exist on the same day:

```text
August 17

├── Machine Learning
│   └── Linear Regression
│
├── DSA
│   └── Arrays
│
└── Web Development
    └── Express Middleware
```

This means a day isn't reduced to a single checkbox.

---

# How LoreLog Organizes Learning

LoreLog uses a hierarchical structure to break large learning goals into smaller pieces.

```text
Main Plan
    ↓
Sub Plan
    ↓
Plan Item
    ↓
Daily Activity
```

## 1. Main Plan

A large learning objective.

Examples:

```text
Machine Learning
Web Development
Data Structures & Algorithms
Competitive Programming
System Design
```

---

## 2. Sub Plan

A major section inside a Main Plan.

Example:

```text
Machine Learning
└── Supervised Learning
```

---

## 3. Plan Item

A concrete topic that needs to be learned.

Example:

```text
Machine Learning
└── Supervised Learning
    └── Linear Regression
```

Plan Items are the actual pieces of knowledge that make up the learning roadmap.

---

## 4. Daily Activity

An Activity records something that actually happened.

Example:

```text
Date:
August 17, 2026

Main Plan:
Machine Learning

Sub Plan:
Supervised Learning

Plan Item:
Linear Regression

What I did:
Studied gradient descent and implemented a basic example.

Time:
1h 40m

Status:
Completed
```

---

# How It Works

The basic workflow is intentionally simple.

```text
Create a Main Plan
        ↓
Break it into Sub Plans
        ↓
Break those into Plan Items
        ↓
Choose what to work on
        ↓
Actually do the work
        ↓
Record the Activity
        ↓
Save it
        ↓
Review it later
```

## Example

Suppose I create:

```text
Machine Learning
└── Supervised Learning
    ├── Linear Regression
    ├── Logistic Regression
    └── Decision Trees
```

I work on Linear Regression on August 17.

I open the calendar, select August 17, and create an Activity:

```text
Machine Learning
→ Supervised Learning
→ Linear Regression

"Studied gradient descent and implemented a simple example."

1h 40m
Completed
```

That Activity becomes part of my permanent learning history.

Later, selecting August 17 should allow me to see what I actually worked on that day.

---

# Calendar & Learning History

The calendar is more than a date picker.

It represents my learning history.

Selecting a date should show the Activities recorded for that day.

For example:

```text
August 17

Activities
────────────────────────

Machine Learning
→ Linear Regression
→ 1h 40m

Data Structures
→ Arrays
→ 45m

Web Development
→ Express Middleware
→ 1h
```

Over time, this creates a historical record of my learning.

The calendar can eventually become a visual activity/consistency map showing how consistently I have been working.

---

# What LoreLog Will Track

LoreLog is intended to track several connected pieces of information.

### Plans

The learning structure:

```text
Main Plan
→ Sub Plan
→ Plan Item
```

### Activities

What I actually worked on.

### Time

How much time I spent on an Activity.

### Status

Whether something is started, in progress, or completed.

### History

A chronological record of Activities.

### Daily Reviews

A lightweight reflection on what happened during the day.

Possible review questions:

```text
What did I accomplish?

What did I struggle with?

What should I work on next?
```

### Progress

Progress derived from the underlying learning structure and Activity data.

For example:

```text
Machine Learning

████████████░░░░

Plan Items:
18 / 24 completed

Activities:
37

Total Learning Time:
42h 15m

Last Activity:
Today
```

Where possible, progress should be **calculated from the underlying data rather than manually maintained**.

---

# Tech Stack

LoreLog is being built with a modern web stack.

## Frontend

### React

Used to build the interactive application and component-based user interface.

### TypeScript

Used for type safety and to make the application's data structures and relationships explicit.

### Tailwind CSS

Used for styling and building the application's UI.

---

## Backend / Backend Services

### Supabase

Supabase provides the backend services LoreLog needs without requiring me to build an entire backend infrastructure from scratch.

It is responsible for:

* Authentication
* PostgreSQL database
* Database APIs
* Persistent data storage
* Row Level Security

---

## Database

### PostgreSQL

PostgreSQL stores LoreLog's persistent data, including:

* Main Plans
* Sub Plans
* Plan Items
* Daily Activities
* Daily Reviews
* User-related data

---

## Authentication

### Supabase Auth

Supabase Auth handles:

* Login
* User identity
* Sessions
* Authentication state

LoreLog is currently designed as a **single-user application**, so there is no need for a public registration system.

---

# Architecture

The basic architecture is:

```text
                    USER
                     │
                     ↓
                WEB BROWSER
                     │
                     ↓
                FRONTEND APP
                     │
              ┌──────┴──────┐
              ↓             ↓
        SUPABASE AUTH   SUPABASE CLIENT
                            │
                            ↓
                       POSTGRESQL
```

The frontend is responsible for:

* Rendering the interface
* Handling user interaction
* Managing UI state
* Sending requests
* Displaying returned data

Supabase is responsible for:

* Authentication
* Persistent data
* PostgreSQL
* Database APIs
* Database-level access control

---

# Data Model

The core data model follows the learning hierarchy.

```text
USER
 │
 ↓
MAIN PLAN
 │
 ├── SUB PLAN
 │      │
 │      └── PLAN ITEM
 │              │
 │              └── DAILY ACTIVITY
 │
 └── ...
```

The conceptual model is:

```text
MainPlan
├── id
├── name
├── description
└── order

SubPlan
├── id
├── main_plan_id
├── name
├── description
├── order
└── status

PlanItem
├── id
├── sub_plan_id
├── name
├── description
├── order
└── status

DailyActivity
├── id
├── plan_item_id
├── date
├── description
├── time_spent
├── status
└── notes

DailyReview
├── id
├── date
├── accomplishments
├── struggles
└── next_steps
```

The actual database schema may evolve as the application is developed.

The important distinction is that **Plans describe the intended learning structure, while Activities describe actual work performed against that structure.**

---

# Example Data Flow

When I record an Activity:

```text
USER
 │
 │ Selects:
 │ Machine Learning
 │ → Supervised Learning
 │ → Linear Regression
 │
 ↓
Writes Activity
 │
 ↓
Clicks SAVE
 │
 ↓
FRONTEND
 │
 ↓
SUPABASE CLIENT
 │
 ↓
POSTGRESQL
 │
 ↓
ACTIVITY STORED
 │
 ↓
DATABASE RESPONSE
 │
 ↓
FRONTEND UPDATES
 │
 ↓
ACTIVITY APPEARS IN HISTORY
```

When I reopen the application:

```text
FRONTEND
   ↓
Request Activities
   ↓
SUPABASE
   ↓
POSTGRESQL
   ↓
Return Data
   ↓
FRONTEND
   ↓
Display Calendar / History
```

The important part is understanding that the UI isn't the permanent source of truth.

The database is.

---

# Security

Even though LoreLog is currently intended for only me, security is still part of the architecture.

The application uses:

### Supabase Authentication

To establish who is accessing the application.

### Database Authorization

To determine what authenticated users are allowed to access.

### Row Level Security

Database-level policies can enforce access rules so that security does not depend only on frontend restrictions.

The frontend should **never be treated as the security boundary**.

---

# Development Philosophy

LoreLog is also a learning project.

The goal isn't:

> **"Get an AI to generate the entire application."**

The goal is:

> **"Understand what I am building before implementing it."**

I am deliberately using the project to learn software engineering concepts through an actual application.

The development process follows:

```text
WHAT
  ↓
WHY
  ↓
DATA
  ↓
RELATIONSHIPS
  ↓
ARCHITECTURE
  ↓
SECURITY
  ↓
IMPLEMENTATION
  ↓
TESTING
  ↓
ITERATION
```

Before implementing a feature, I want to understand:

* What problem does it solve?
* What data does it need?
* Why does that data exist?
* What does it communicate with?
* What happens when something changes?
* What happens when something fails?
* Why was a particular implementation chosen?

AI can help with implementation, but the objective is to **understand and be able to explain the resulting system**, not blindly accept generated code.

---

# Development Roadmap

LoreLog is being developed incrementally.

## Phase 1 — Product Definition

* [x] Define the purpose of LoreLog
* [x] Define Main Plan → Sub Plan → Plan Item → Activity hierarchy
* [x] Separate planned work from actual activity
* [ ] Finalize MVP requirements

## Phase 2 — Domain & Data Design

* [x] Identify core entities
* [x] Define relationships
* [ ] Finalize data model
* [ ] Identify edge cases
* [ ] Define data lifecycle

## Phase 3 — Supabase Foundation

* [ ] Create Supabase project
* [ ] Configure PostgreSQL database
* [ ] Configure authentication
* [ ] Connect frontend to Supabase
* [ ] Configure environment variables
* [ ] Design Row Level Security policies

## Phase 4 — Authentication

* [ ] Login screen
* [ ] Authentication flow
* [ ] Session handling
* [ ] Protected application routes
* [ ] Logout
* [ ] Authentication error handling

## Phase 5 — Learning Plans

* [ ] Main Plans
* [ ] Sub Plans
* [ ] Plan Items
* [ ] Create/edit/delete functionality
* [ ] Ordering
* [ ] Completion state

## Phase 6 — Daily Activities

* [ ] Select date
* [ ] Select Main Plan
* [ ] Select Sub Plan
* [ ] Select Plan Item
* [ ] Write Activity
* [ ] Record time
* [ ] Set status
* [ ] Save Activity
* [ ] Edit Activity
* [ ] Delete Activity

## Phase 7 — Calendar

* [ ] Monthly calendar
* [ ] Date navigation
* [ ] Activity indicators
* [ ] Daily Activity view
* [ ] Activity filtering
* [ ] Historical navigation

## Phase 8 — Dashboard

* [ ] Today's Activities
* [ ] Current Plans
* [ ] Next Plan Item
* [ ] Recent Activity
* [ ] Progress overview
* [ ] Learning statistics

## Phase 9 — Progress

* [ ] Plan completion
* [ ] Sub Plan completion
* [ ] Plan Item completion
* [ ] Total learning time
* [ ] Activity statistics
* [ ] Consistency tracking
* [ ] Monthly summaries

## Phase 10 — Daily Reviews

* [ ] Daily reflection
* [ ] Accomplishments
* [ ] Difficulties
* [ ] Next steps
* [ ] Historical reviews

## Phase 11 — Security & Reliability

* [ ] Review authentication
* [ ] Review RLS policies
* [ ] Test unauthorized access
* [ ] Validate database constraints
* [ ] Handle failed requests
* [ ] Handle empty states
* [ ] Handle loading states
* [ ] Handle network failures

## Phase 12 — UI/UX Polish

* [ ] Responsive design
* [ ] Navigation improvements
* [ ] Animations
* [ ] Loading states
* [ ] Empty states
* [ ] Error states
* [ ] Accessibility
* [ ] Theme support if necessary
* [ ] Performance improvements

---

# MVP

The first version is intentionally small.

```text
Authentication
      +
Main Plans
      +
Sub Plans
      +
Plan Items
      +
Calendar
      +
Daily Activities
      +
Basic Progress
```

The fundamental loop is:

```text
Create Plan
     ↓
Break Plan Down
     ↓
Choose What To Work On
     ↓
Do The Work
     ↓
Record What Actually Happened
     ↓
Review History
     ↓
Continue
```

If this core loop isn't useful, adding more features won't solve the underlying problem.

---

# Current Status

**Early development — architecture and planning stage.**

The current focus is on:

1. Defining the product
2. Designing the domain model
3. Designing the database
4. Understanding authentication
5. Designing the application architecture
6. Establishing the MVP
7. Implementing incrementally

Implementation is intentionally following the architecture rather than being created first and understood later.

---

# What I'm Learning

LoreLog is being used as a practical way to learn how a real web application fits together.

Through building it, I want to understand:

### Frontend

* React
* TypeScript
* Component architecture
* State management
* Forms
* UI interactions
* Data fetching

### Backend & Database

* Supabase
* PostgreSQL
* Database relationships
* CRUD operations
* Data modeling
* Constraints
* Persistent storage

### Authentication & Security

* Authentication
* Authorization
* Sessions
* Row Level Security
* Protected routes
* Secure data access

### Software Architecture

* Separation of responsibilities
* Data flow
* Application architecture
* Feature organization
* Error handling
* Testing

### Engineering Thinking

Most importantly, LoreLog is helping me practice thinking in terms of:

```text
What?
Why?
How?
What data?
What relationship?
What can fail?
How do I test it?
```

---

# Future Ideas

These are ideas for later, not requirements for the first version.

## "What Should I Work On Next?"

Use the Plan Item structure to identify unfinished topics.

```text
Machine Learning

✓ Linear Regression
✓ Logistic Regression
→ Decision Trees       ← NEXT
○ Random Forest
○ Gradient Boosting
```

The goal is to reduce the friction of deciding what to study next.

---

## Learning Analytics

Potential analytics could include:

* Learning consistency
* Time distribution across plans
* Neglected topics
* Frequently revisited topics
* Long inactivity periods
* Weekly summaries
* Monthly reports
* Progress trends

---

## Knowledge Relationships

The hierarchy could eventually evolve into a more connected knowledge model.

For example:

```text
Linear Algebra
      ↓
Neural Networks
      ↓
Backpropagation
      ↓
Deep Learning
      ↓
Computer Vision
```

This would allow relationships between concepts to exist beyond a simple parent-child hierarchy.

---

## AI-Assisted Reflection

AI could eventually help analyze the history and generate:

* Weekly summaries
* Progress reports
* Weak-area detection
* Revision suggestions
* Personalized next steps

However, AI should remain an enhancement.

The core application should still work without AI.

---

# Testing Philosophy

LoreLog should be tested according to actual user behavior, not just whether individual UI components render.

### Authentication

```text
Logged out
→ Cannot access dashboard

Logged in
→ Can access dashboard

Logout
→ Dashboard becomes inaccessible
```

### Plans

```text
Create Main Plan
→ Create Sub Plan
→ Create Plan Item
→ Verify hierarchy
```

### Activities

```text
Select Date
→ Select Plan Item
→ Create Activity
→ Save
→ Refresh
→ Activity still exists
```

### Security

```text
Unauthorized request
→ Database rejects request
```

The goal isn't simply:

> "The UI looks correct."

It is:

> **"The entire system behaves correctly."**

---

# Long-Term Goal

LoreLog is meant to become a reliable personal record of my learning.

Not just:

> **"Did I study today?"**

But:

> **What am I trying to learn?**

> **How did I break it down?**

> **What did I actually work on?**

> **How much time have I invested?**

> **What have I completed?**

> **Where have I been inconsistent?**

> **What should I work on next?**

And eventually:

> **How has my knowledge evolved over months and years?**

---

# Philosophy

> **Plan deliberately.**
> **Work consistently.**
> **Record honestly.**
> **Review continuously.**

**LoreLog** is my attempt to keep that history.
