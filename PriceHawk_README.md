# PriceHawk

PriceHawk is a modern price tracking tool that monitors product prices across online retailers.  It scrapes product details from Amazon and other e‑commerce sites, stores the data in a MongoDB database, and notifies users when there are changes in price.  With PriceHawk you can set price alerts, track discounts, view price history and comparisons, and make data‑driven purchasing decisions—all through a clean, user‑friendly interface.

## Features

- **Real‑Time Price Monitoring:**  Continuously scrape current product prices from Amazon and store them in a database.  Users can add products to their watch list and see the latest prices at a glance.
- **Alerts & Notifications:**  Set target prices and receive email notifications when a product’s price drops below your desired threshold.
- **Price History & Charts:**  View historical pricing trends for each tracked product.  Visualise price changes over time so you know the best time to buy.
- **Product Comparisons:**  Compare prices and discounts across multiple products to find the best value.  Filter and sort by price, discount percentage, or other metadata.
- **Responsive Web App:**  Built with Next.js and Tailwind CSS for a fast and mobile‑friendly user interface.  Includes reusable components such as a search bar, product cards, price info modal, and subscription form.

## Technologies Used

PriceHawk makes use of several modern JavaScript libraries and frameworks:

- **Next.js:**  A React framework for building web applications.  It powers both the frontend and backend of the app.
- **Tailwind CSS:**  A utility‑first CSS framework used for styling components and creating custom designs.
- **TypeScript:**  A statically typed superset of JavaScript used throughout the codebase for type safety.
- **Mongoose:**  An ODM (Object Data Modelling) library for MongoDB and Node.js used to define schemas and interact with the MongoDB database.
- **Nodemailer:**  A module for Node.js applications used for sending email notifications.
- **Axios:**  A promise‑based HTTP client used by the server to make requests to scrape product details.
- **Cheerio:**  A fast, flexible HTML parser for the server side used to extract data from product pages.
- **React Responsive Carousel:**  A lightweight carousel component for React, used to display images on the home page.
- **Google Fonts:**  Free fonts used for typography throughout the application.

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) installed on your system.
- A [MongoDB](https://www.mongodb.com/) instance (local or hosted) with a connection URI.
- An email account (for sending notifications) and associated SMTP credentials.

### Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/iamayushisachan/PriceHawk.git
   cd PriceHawk
   ```

2. **Install dependencies:**

   ```bash
   npm install
   ```

3. **Configure environment variables:**

   Create a `.env.local` file in the root of the project and define the following variables:

   ```env
   MONGODB_URI=<your MongoDB connection string>
   NODEMAILER_HOST=<SMTP host>
   NODEMAILER_PORT=<SMTP port>
   NODEMAILER_USER=<your SMTP username>
   NODEMAILER_PASS=<your SMTP password>
   BASE_URL=http://localhost:3000
   ```

### Running Locally

To start the development server, run:

```bash
npm run dev
```

This will build and serve the Next.js application at `http://localhost:3000`.  You can now navigate to the site in your browser and test price tracking features locally.

### Building for Production

To create an optimized production build, run:

```bash
npm run build
npm run start
```

This will compile the application and serve it with optimisations enabled.  When deploying to a hosting provider, ensure that your environment variables are set appropriately.

## Project Structure

```
PriceHawk/
├─ pages/             # Next.js pages (home, product pages, API routes)
├─ components/        # Reusable React components (search bar, product card, modal, etc.)
├─ utils/             # Utility functions for scraping and formatting data
├─ models/            # Mongoose models defining product schemas
├─ public/            # Static assets including images and fonts
├─ styles/            # Tailwind CSS configuration and global styles
├─ scripts/           # Serverless functions used for scraping and notifications
├─ package.json       # Project metadata and scripts
└─ README.md          # This documentation file
```

## Contributing

Contributions to PriceHawk are welcome!  Feel free to open issues or submit pull requests to report bugs, suggest new features, or improve the documentation.  Please follow the existing coding style and conventions.

1. Fork this repository.
2. Create a new branch: `git checkout -b my-feature`.
3. Make your changes and commit them with clear messages.
4. Push your branch and open a pull request.

## License

This project is licensed under the **MIT License**.  See the [LICENSE](LICENSE) file for details.

## Acknowledgements

- This project was inspired by the need to track fluctuating prices and save money when shopping online.
- Thanks to the maintainers of Next.js, Tailwind CSS, Mongoose, and other open‑source libraries used in this project.
