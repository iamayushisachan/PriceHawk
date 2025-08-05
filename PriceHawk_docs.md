# PriceHawk Documentation

Welcome to the documentation for **PriceHawk**!  This document provides a deeper look at the project architecture, explains how the scraping and notification pipeline works, and outlines possible areas for extension.

## Project Overview

PriceHawk is a full‑stack web application designed to track product prices.  The frontend is built with Next.js and Tailwind CSS, and interacts with a backend composed of serverless API routes.  The backend scraping logic fetches product details from Amazon, parses the HTML with Cheerio, stores data in MongoDB via Mongoose, and sends email alerts via Nodemailer when price conditions are met.  The modular design makes it easy to add support for more retailers or notification channels (e.g., SMS).

## Architecture

```
      +-------------+       +----------------+       +----------------+
User ─┤  Web Client ├──────▶│ Next.js API    │──────▶│ Scraping Logic │
      +-------------+       | routes         |       | (Cheerio/Axios)│
            ▲                +----------------+       +----------------+
            │                        │                        │
            │                        ▼                        │
            │                +----------------+               │
            │                │ MongoDB (via    │◀─────────────┘
            │                │ Mongoose)       │
            │                +----------------+
            │                        │
            │                        ▼
            │                +----------------+
            └───────────────┤ Notification   │
                             │ Service (Email)│
                             +----------------+
```

1. **Web Client:**  Provides a responsive UI where users search for products, view price histories, and manage alerts.
2. **API Routes:**  Serverless Next.js endpoints handle incoming requests from the client (e.g., `/api/trackProduct`, `/api/removeProduct`).  They validate input, query the database, and trigger scraping jobs.
3. **Scraping Logic:**  Uses Axios to fetch product pages and Cheerio to parse HTML and extract price data.  Extracted data is normalised and stored in MongoDB.
4. **Database (MongoDB):**  Stores product details, price history, and user subscriptions.  Mongoose models define the schema and ensure data integrity.
5. **Notification Service:**  When a price drop meets a user’s alert threshold, a serverless function uses Nodemailer to send an email notification.

## Key Files

- **`pages/index.tsx`** – The home page showing trending products and a search bar.
- **`pages/api/trackProduct.ts`** – An API route that accepts a product URL, initiates scraping, and stores results.
- **`pages/api/unsubscribe.ts`** – Removes a product from a user’s watch list and cancels alerts.
- **`scripts/scraper.ts`** – Contains helper functions using Axios and Cheerio to scrape product details.
- **`models/Product.ts`** – Defines the Mongoose schema for product details and price history.
- **`utils/notify.ts`** – Encapsulates email notification logic using Nodemailer.

## Extending the Project

Here are a few ideas for extending PriceHawk:

- **Support More Retailers:**  Add scraping modules for other e‑commerce sites.  You can abstract the scraper into separate modules and call the appropriate one based on the product URL domain.
- **Additional Notification Channels:**  Integrate SMS notifications via services like Twilio or push notifications via Firebase.
- **Dashboard with Charts:**  Use a charting library (e.g., Chart.js or Recharts) to visualise price histories with interactive graphs.
- **User Authentication:**  Implement an authentication system so users can have personalised watch lists and settings that persist across devices.
- **Automated Scheduling:**  Deploy a cron job (or scheduled Lambda) to periodically run scraping jobs without manual triggers.

## Conclusion

PriceHawk demonstrates how modern web technologies can be combined to build a useful tool for smart shopping.  Its architecture is modular and scalable, making it straightforward to maintain and extend.  Feel free to explore the codebase, raise issues if you encounter problems, and contribute improvements via pull requests!
