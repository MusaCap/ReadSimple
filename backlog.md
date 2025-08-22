# Backlog: Self-Publishing Book Platform (Pay-Per-Chapter Model)

---

## Epic 1: Author Publishing  
**Goal:** Allow authors to create, upload, and manage books/chapters.  

### User Stories  
1. **Book Creation**  
   - As an author, I can create a book with a title, genre, and description.  
   - **Acceptance Criteria:**  
     - Authors can enter metadata (title, genre, description).  
     - Book saved in draft mode until at least one chapter is uploaded.  

2. **Chapter Upload**  
   - As an author, I can upload a new chapter (title, text, optional price).  
   - **Acceptance Criteria:**  
     - Chapters linked to a specific book.  
     - Author can save as draft or publish immediately.  
     - Price field supports free (0) or a decimal value.  

3. **Chapter Management**  
   - As an author, I can edit, reorder, or delete unpublished chapters.  
   - **Acceptance Criteria:**  
     - Published chapters can be updated (with version history).  
     - Chapter order (numbering) can be modified before publishing.  

4. **Analytics Dashboard**  
   - As an author, I can view reads, unlocks, and revenue per chapter.  
   - **Acceptance Criteria:**  
     - Dashboard shows metrics (daily/weekly/monthly).  
     - Revenue calculated based on chapter unlocks × price × (1 - platform fee).  

---

## Epic 2: Reader Experience  
**Goal:** Provide readers with discovery, engagement, and chapter access.  

### User Stories  
1. **Book Discovery**  
   - As a reader, I can browse books by genre, trending, or new releases.  
   - **Acceptance Criteria:**  
     - Books displayed with title, author, description, cover image.  
     - Search by keyword (title, author, genre).  

2. **Chapter Unlock**  
   - As a reader, I can unlock chapters using credits or micropayments.  
   - **Acceptance Criteria:**  
     - If chapter is free, reader can open without credits.  
     - If paid, reader prompted to confirm unlock before access.  
     - Reader history tracks unlocked chapters.  

3. **Reading Interface**  
   - As a reader, I can read chapters in a clean, mobile-friendly UI.  
   - **Acceptance Criteria:**  
     - Supports dark/light mode.  
     - Saves reading progress per chapter.  

4. **Community Interaction**  
   - As a reader, I can leave reviews, ratings, and comments on chapters/books.  
   - **Acceptance Criteria:**  
     - 1–5 star rating system.  
     - Reviews limited to 500 characters.  
     - Comment moderation enabled.  

---

## Epic 3: Payments & Payouts  
**Goal:** Handle transactions for readers and payouts for authors.  

### User Stories  
1. **Credit Purchase**  
   - As a reader, I can purchase credits via Stripe/PayPal.  
   - **Acceptance Criteria:**  
     - Reader wallet updated immediately after payment confirmation.  
     - Failed transactions show clear error messages.  

2. **Wallet & Transactions**  
   - As a reader, I can see my credit balance and past transactions.  
   - **Acceptance Criteria:**  
     - Balance displayed in header/dashboard.  
     - Transaction history includes amount, date, and type (purchase/unlock).  

3. **Author Earnings**  
   - As an author, I can view total earnings and pending payouts.  
   - **Acceptance Criteria:**  
     - Dashboard shows breakdown by book and chapter.  
     - Author sees pending vs. completed payouts.  

4. **Payout Processing**  
   - As an admin, I can process payouts for authors.  
   - **Acceptance Criteria:**  
     - Payouts triggered manually or automatically (monthly).  
     - Status updates: pending → completed → failed (if applicable).  

---

## Epic 4: Admin & Moderation  
**Goal:** Ensure platform integrity through moderation and oversight.  

### User Stories  
1. **Content Moderation**  
   - As an admin, I can review and flag inappropriate content.  
   - **Acceptance Criteria:**  
     - Flagging system in place for users.  
     - Admin dashboard displays flagged items with actions (approve/reject/remove).  

2. **Fraud Detection**  
   - As an admin, I can detect abnormal activity (bot reads, credit fraud).  
   - **Acceptance Criteria:**  
     - Alerts generated for suspicious spikes in reads/unlocks.  
     - Admin can temporarily freeze an account.  

3. **User Management**  
   - As an admin, I can suspend or ban users who violate terms.  
   - **Acceptance Criteria:**  
     - Suspension removes access to platform functions.  
     - Ban deletes account and revokes access to payouts.  

4. **Payout Oversight**  
   - As an admin, I can review payout requests before processing.  
   - **Acceptance Criteria:**  
     - Admin dashboard shows pending payouts with author details.  
     - Approve/reject option with audit trail.  

---

## Epic 5: Platform Infrastructure (Tech/DevOps)  
**Goal:** Support scalability, security, and reliability.  

### User Stories  
1. **Authentication & Roles**  
   - As a user, I can register and log in as an author, reader, or admin.  
   - **Acceptance Criteria:**  
     - Role assigned during onboarding.  
     - JWT-based authentication.  

2. **Content Storage**  
   - As a developer, I want chapters stored securely in cloud storage.  
   - **Acceptance Criteria:**  
     - Use AWS S3/Blob with CDN delivery.  
     - Content encrypted at rest and in transit.  

3. **Logging & Analytics**  
   - As a developer, I want system logs for debugging and tracking.  
   - **Acceptance Criteria:**  
     - Centralized log storage (e.g., CloudWatch).  
     - Errors and API usage tracked.  

---

# Sprint Breakdown (Initial Plan)

### Sprint 1: Core Author & Book Setup (2 weeks)  
- Implement user authentication and roles.  
- Build `BOOK` and `CHAPTER` models.  
- Author dashboard: create book, upload/publish chapters.  

### Sprint 2: Reader Experience (2 weeks)  
- Implement browsing/search (genre, trending).  
- Chapter unlock logic with mock credits.  
- Reader UI for chapter reading + progress save.  

### Sprint 3: Payments & Payouts (2 weeks)  
- Integrate Stripe/PayPal for credit purchase.  
- Build wallet + transaction history.  
- Author payout dashboard + admin payout approval.  

### Sprint 4: Admin & Moderation (2 weeks)  
- Admin dashboard for flagged content.  
- Fraud detection alerts.  
- User suspension/ban flow.  

### Sprint 5: Infrastructure & Analytics (2 weeks)  
- Logging and monitoring setup.  
- Deploy cloud storage for chapters.  
- Basic analytics dashboard for admins.  
