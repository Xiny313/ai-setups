# Make.com — Gmail → Notion Automation Setup Guide

Automatically save every email you star in Gmail as a structured entry in Notion. No manual copy-paste.

## What It Is
Make.com (formerly Integromat) connects apps with visual automation flows called "scenarios." This guide builds one specific flow: star a Gmail → it creates a Notion database entry with the subject, sender, body, and date.

## What You Need
- Free Make.com account
- Gmail account
- Notion account with a database set up (see Step 1 below)

## Step 1 — Set Up Your Notion Database

1. In Notion, create a new page → click **+ Add a database** → choose **Table**
2. Add these properties:
   - **Subject** (Title — default)
   - **From** (Text)
   - **Date** (Date)
   - **Body** (Text)
3. Name the database something like "Email Inbox"
4. Copy the database URL — you'll need it in Make

## Step 2 — Build the Automation in Make

1. Go to [make.com](https://make.com) and create a free account
2. Click **+ Create a new scenario**
3. Click the **+** circle → search for **Gmail** → select **Watch Emails**
   - Connect your Gmail account when prompted
   - Set trigger: **Label = Starred** (or any label you choose)
   - Set **Maximum number of results**: 1
4. Click **+** after the Gmail module → search for **Notion** → select **Create a Database Item**
   - Connect your Notion account when prompted
   - Select your "Email Inbox" database
   - Map fields:
     - Subject → `{{1.subject}}`
     - From → `{{1.from[].name}} <{{1.from[].address}}>`
     - Date → `{{1.date}}`
     - Body → `{{1.snippet}}`
5. Click **Run once** to test — star an email in Gmail and check Notion
6. If it works, click **Schedule** → set to run every 15 minutes
7. Click **Activate scenario**

## Free Tier Limits
- 1,000 operations/month
- 2 active scenarios
- Runs every 15 minutes minimum

## Core Plan ($9/mo)
10,000 operations/month, 1-minute intervals, unlimited scenarios.

---
*Part of the [@opti.algo](https://instagram.com/opti.algo) AI tools series*
