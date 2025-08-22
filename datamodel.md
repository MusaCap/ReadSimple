# Data Model: Self-Publishing Book Platform

---

## Entity Relationship Diagram (ERD)

```mermaid
erDiagram
    USER ||--o{ BOOK : authors
    USER ||--o{ READER_ACTIVITY : reads
    BOOK ||--o{ CHAPTER : contains
    CHAPTER ||--o{ READER_ACTIVITY : tracked_by
    USER ||--o{ PAYOUT : receives

    USER {
        int id
        string name
        string email
        enum role (author, reader, admin)
    }

    BOOK {
        int id
        int author_id
        string title
        string genre
        string description
        datetime created_at
    }

    CHAPTER {
        int id
        int book_id
        int chapter_number
        string title
        text content
        decimal price
        datetime published_at
    }

    READER_ACTIVITY {
        int id
        int user_id
        int chapter_id
        datetime timestamp
        enum action (unlock, read)
    }

    PAYOUT {
        int id
        int author_id
        decimal amount
        datetime payout_date
        enum status (pending, completed, failed)
    }
ables & Attributes
USER
Field	Type	Description
id	int (PK)	Unique identifier for user
name	string	User’s full name
email	string	User’s email (unique)
role	enum	author, reader, or admin
BOOK
Field	Type	Description
id	int (PK)	Unique identifier for book
author_id	int (FK)	Reference to USER.id (author)
title	string	Title of the book
genre	string	Book genre
description	string	Short description
created_at	datetime	When book was created
CHAPTER
Field	Type	Description
id	int (PK)	Unique identifier for chapter
book_id	int (FK)	Reference to BOOK.id
chapter_number	int	Order in book (1, 2, 3…)
title	string	Chapter title
content	text	Chapter text content
price	decimal	Price per chapter (0 if free)
published_at	datetime	Date/time of publication
READER_ACTIVITY
Field	Type	Description
id	int (PK)	Unique identifier for activity
user_id	int (FK)	Reference to USER.id (reader)
chapter_id	int (FK)	Reference to CHAPTER.id
timestamp	datetime	When action occurred
action	enum	unlock, read
PAYOUT
Field	Type	Description
id	int (PK)	Unique identifier for payout
author_id	int (FK)	Reference to USER.id (author)
amount	decimal	Amount paid out
payout_date	datetime	When payout was issued
status	enum	pending, completed, failed
Key Relationships

One Author → Many Books (USER → BOOK)

One Book → Many Chapters (BOOK → CHAPTER)

One Reader → Many Reads (USER → READER_ACTIVITY)

One Author → Many Payouts (USER → PAYOUT)

One Chapter → Many Reader Activities (CHAPTER → READER_ACTIVITY)
