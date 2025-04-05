# 🌾 AgriConnect Platform – masterplan.md

## 1. App Overview & Objectives

**AgriConnect** is a web platform built to empower farmers by giving them direct control over how they sell their produce. The platform enables farmers to list crops, connect directly with consumers, collaborate in farmer groups, and bypass exploitative intermediaries — particularly those offering rates below Minimum Support Price (MSP). 

**Core Objective:**  
Help farmers secure better, fairer prices by acting as their own retailers and facilitating trust-based, direct sales.

---

## 2. Target Audience

### 👨‍🌾 Farmers (Primary)
- Small to mid-size landholders
- Tech-aware or assisted by someone digitally literate
- Seeking alternatives to traditional mandis or intermediary-led sales

### 🛒 End Consumers (Hackathon MVP Focus)
- Urban/suburban buyers interested in farm-fresh produce
- Health-conscious or ethically-minded individuals
- Looking to support local farmers and bypass supermarkets

*(Future Phases)*
- 🏪 Offline Retailers
- 🧑‍🤝‍🧑 Farmer Collectives / Group Buyers

---

## 3. Core Features & Functionality

### For Farmers
- Account registration with identity + farming proof
- Secure document upload & admin-led manual verification
- Role-based access (verified users can list produce)
- Listings management: crop name, price, quantity, photos, availability
- Inventory dashboard
- Order notifications
- Messaging (basic or simulated)
- Option to join/form farmer groups
- Group coordination for bulk sales (future phase)

### For End Consumers (MVP Scope)
- Browse listings without login (filtered by crop, location)
- Basic signup (name, phone, address)
- Add to cart & place order
- Order passed to farmer, who handles follow-up and delivery

---

## 4. High-Level Technical Stack Recommendations

### 💾 Backend / Infrastructure
- **Firebase (Preferred)**  
  - Authentication (Firebase Auth)
  - Firestore (NoSQL DB for users, listings, orders)
  - Firebase Storage (for secure document uploads)
  - Firebase Functions (for business logic, optional)
  - Real-time updates out of the box

**Alternative:** Supabase (PostgreSQL + RLS + real-time subscriptions)

### 🌐 Frontend
- **React** with TailwindCSS (for rapid UI development)
- UI component libraries: Material UI or DaisyUI (via Tailwind)

---

## 5. Conceptual Data Model

**Users Collection:**
- id, name, phone, address
- role: `farmer` / `consumer` / `admin`
- verificationStatus: `pending` / `verified` / `rejected`
- uploadedDocs: [URLs]
- cropTypes, bio (optional for farmers)

**Produce Listings:**
- listingId, farmerId
- crop name, variety, description
- price per unit, unit type
- availability dates, quantity, min order qty
- images (URLs)
- status: `active` / `inactive`

**Orders:**
- orderId, listingId, consumerId, farmerId
- quantity, status (e.g., "Placed", "Preparing", "Delivered")
- consumer contact details

**FarmerGroups (Future Phase):**
- groupId, members, groupListings, chat thread

---

## 6. User Interface Design Principles

- **Visual Style:** Earthy, organic, trustworthy
  - Colors: Olive green, saddle brown, orange accents
  - Fonts: Open Sans (body), Merriweather (headings)
- **Layout:** Clean, modular sections with cards for listings and users
- **Assets:** Use high-quality images of real farms, produce
- **Icons:** From Font Awesome or Material Icons
- **Responsiveness:** Fully mobile-friendly (important for farmer accessibility)

---

## 7. Security Considerations

- **File Storage:** Use BaaS storage with rules to restrict doc access to admin only
- **RBAC (Role-Based Access Control):**  
  - Farmers can list only if verified  
  - Admin-only access to document review dashboard  
  - Consumers can browse/list without login, but must log in to order
- **Consumer Verification:** Skipped in MVP; fake orders mitigated by letting farmers verify before delivery
- **Payment:** Handled offline or simulated for MVP

---

## 8. Development Phases

### 🔹 Phase 1 (Hackathon MVP)
- Farmer registration & document upload
- Admin document review dashboard
- Listing creation and management
- Public browsing of produce
- Consumer signup + order flow
- Role-based permissions
- Firebase backend (auth, database, storage)

### 🔹 Phase 2 (Post Hackathon)
- Verified offline retailers
- Full messaging/chat interface
- Farmer groups & group listings
- Consumer verification (optional)
- Payment integration (UPI or escrow-style)
- Logistics support module

---

## 9. Potential Challenges & Suggested Solutions

| Challenge | Suggested Solution |
|----------|--------------------|
| Ensuring farmer trust | Use strong visual storytelling + explain verification clearly |
| Fake orders | Keep contact info visible to farmers for validation |
| Role complexity | Use BaaS roles and security rules for simple RBAC |
| Slow manual verification | Build a scalable admin dashboard with filters/search |
| Limited time for complex features | Focus on delivering end-to-end flow for one path (Farmer ➜ Consumer) |

---

## 10. Future Expansion Possibilities

- Launch multilingual support (Hindi, regional languages)
- Launch Android app (low-bandwidth optimized)
- Smart recommendations based on location + season
- Integrate with government agri schemes or subsidies
- Build community forum or Q&A board for farmers
- Real-time logistics tracking via delivery partners

---
