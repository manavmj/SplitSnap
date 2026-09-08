# SplitSnap
A photo-in, fair-split-out bill splitter — split tax and service charge by what you actually ate, not by headcount.

SplitSnap solves the group-dinner math problem everyone gets wrong: dividing tax and service charge evenly by headcount, even when one person only had a Coke and someone else shared the biryani.

Upload a photo of the bill, tell it who ate what, and get an exact per-person breakdown — with tax and service charge split proportionally to what each person actually ordered.

How it works
Upload — Snap a photo of the bill. Gemini's vision model extracts a structured breakdown: every line item, quantity, price, subtotal, GST, service charge, discount, and total.
Review — Nothing gets calculated blindly. Low-confidence fields (smudged prices, faded thermal print, handwriting) are flagged for you to check and correct before any math runs.
Assign — Add the people at the table. Tag each item to one person, a few people (split evenly), or everyone.
Split — Get an exact per-person total: item subtotal + their fair share of tax and service charge, correctly proportional to what they ate.
Why this is harder than it looks

Most bill-splitting apps just divide the total by the number of people. SplitSnap computes each person's share of tax, service charge, and discounts in proportion to their item subtotal — so the person who only had a Coke doesn't subsidize the table's shared appetizers. It also treats OCR as fallible by design: every extracted field carries a confidence score, and a human review step sits between "photo in" and "math runs."

Tech
Single-page React app (Vite) — upload → review → assign → result
Structured extraction via Google Gemini's multimodal API
Rounding-reconciled math so per-person totals always sum exactly to the printed bill total
Getting started
Prerequisites
Node.js (v18 or later recommended)
A free Google Gemini API key
1. Clone the repo
bash
git clone https://github.com/<your-username>/splitsnap.git
cd splitsnap
2. Install dependencies
bash
npm install
3. Set up your API key

Copy the example environment file:

bash
cp .env.example .env      # macOS/Linux
Copy-Item .env.example .env   # Windows PowerShell

Open .env and add your Gemini API key:

VITE_GEMINI_API_KEY=your_actual_gemini_key
4. Run the app
bash
npm run dev

Open the local URL shown in your terminal (usually http://localhost:5173) in your browser.

No API key yet?

Click "Use a sample bill" on the upload screen to try the full review → assign → split flow with demo data — no key required.

Build for production
bash
npm run build

Built because the argument over the bill is a genuine engineering problem dressed up as a social one — and every group has it.

**Screenshots:**

<img width="2878" height="1534" alt="image" src="https://github.com/user-attachments/assets/49c88fe1-de63-42bb-ad55-18f13da63e43" />
<img width="2850" height="1532" alt="image" src="https://github.com/user-attachments/assets/d2bd87aa-3e68-46ba-bd38-d376408a0ada" />
<img width="1398" height="1482" alt="image" src="https://github.com/user-attachments/assets/02d3f43f-bb51-4fe0-8d61-e647bdd84aac" />



