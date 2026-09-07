# SplitSnap
A photo-in, fair-split-out bill splitter — split tax and service charge by what you actually ate, not by headcount.
SplitSnap 🧾

Split restaurant bills fairly, from a single photo.

SplitSnap solves the group-dinner math problem everyone gets wrong: dividing tax and service charge evenly by headcount, even when one person only had a Coke and someone else shared the biryani.

Upload a photo of the bill, tell it who ate what, and get an exact per-person breakdown, with tax and service charge split proportionally to what each person actually ordered, not divided evenly by the number of people at the table.

How it works:-
Upload : Snap a photo of the bill. An AI vision model (Gemini) extracts a structured breakdown: every line item, quantity, price, subtotal, GST, service charge, discount, and total.

Review : Nothing gets calculated blindly. Low-confidence fields (smudged prices, faded thermal print, handwriting) are flagged for you to check and correct before any math runs.

Assign : Add the people at the table. Tag each item to one person, a few people (split evenly shared appetizers, a biryani for two), or everyone.

Split : Get an exact per-person total: item subtotal + their fair share of tax and service charge, correctly proportional to what they ate.

Why this is harder than it looks

Most bill splitting apps just divide the total by the number of people, or split tax evenly regardless of who ordered what. That's the wrong answer everyone quietly accepts. SplitSnap computes each person's share of tax, service charge, and discounts in proportion to their item subtotal — so the person who only had a Coke doesn't subsidize the table's shared appetizers.

It also treats OCR as fallible by design: every extracted field carries a confidence score, and a human review step sits between "photo in" and "math runs," so a misread ₹450 doesn't silently become someone's dinner bill.

Tech
Single-page React app — upload → review → assign → result, no chat interface, no login, no database
Structured extraction via Google Gemini's multimodal API, validated against a strict schema
Rounding-reconciled math so per-person totals always sum exactly to the printed bill total
Setup
bash
git clone <repo-url>
cd splitsnap
npm install
Copy-Item .env.example .env   # then add your VITE_GEMINI_API_KEY
npm run dev

A "Use a sample bill" demo mode is available for trying the app without an API key.

Built because the argument over the bill is a genuine engineering problem dressed up as a social one — and every group has it.
<img width="2878" height="1534" alt="image" src="https://github.com/user-attachments/assets/49c88fe1-de63-42bb-ad55-18f13da63e43" />
