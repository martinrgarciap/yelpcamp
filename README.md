# YelpCamp

YelpCamp is a full-stack campground review application built with Node.js,
Express, MongoDB, EJS, Passport, Cloudinary, and Mapbox. Users can register,
log in, create campground listings, upload images, view campground locations on
interactive maps, and leave reviews.

## Features

- User registration, login, logout, and session-based authentication
- Create, read, update, and delete campground listings
- Image uploads with Cloudinary
- Campground geocoding and maps with Mapbox
- Reviews with ratings
- Authorization for campground owners and review authors
- Server-side validation with Joi
- Flash messages for user feedback
- Basic security middleware with Helmet and MongoDB query sanitization

## Tech Stack

- Node.js
- Express
- MongoDB and Mongoose
- EJS and EJS Mate
- Passport and Passport Local Mongoose
- Cloudinary and Multer
- Mapbox
- Bootstrap

## Getting Started

### Prerequisites

Make sure you have these installed:

- Node.js
- npm
- MongoDB, either local or hosted
- A Mapbox account and access token
- A Cloudinary account

### Installation

Install dependencies:

```bash
npm install
```

Create a `.env` file in the project root:

```bash
DB_URL=mongodb://localhost:27017/yelp-camp
SECRET=your-session-secret
MAPBOX_TOKEN=your-mapbox-token
CLOUDINARY_CLOUD_NAME=your-cloudinary-cloud-name
CLOUDINARY_KEY=your-cloudinary-key
CLOUDINARY_SECRET=your-cloudinary-secret
```

If `DB_URL` is not set, the app falls back to:

```bash
mongodb://localhost:27017/yelp-camp
```

### Seed the Database

The project includes a seed script that creates sample campground data:

```bash
node seeds/index.js
```

Note: the seed script uses a hard-coded author id, so make sure that user exists
in your database before relying on seeded campground ownership.

### Run the App

Start the server:

```bash
npm start
```

Then visit:

```bash
http://localhost:3000
```

## Routes

### Authentication

- `GET /register` - show registration form
- `POST /register` - create a new user
- `GET /login` - show login form
- `POST /login` - log in
- `GET /logout` - log out

### Campgrounds

- `GET /campgrounds` - list all campgrounds
- `GET /campgrounds/new` - show new campground form
- `POST /campgrounds` - create a campground
- `GET /campgrounds/:id` - show one campground
- `GET /campgrounds/:id/edit` - show edit form
- `PUT /campgrounds/:id` - update a campground
- `DELETE /campgrounds/:id` - delete a campground

### Reviews

- `POST /campgrounds/:id/reviews` - create a review
- `DELETE /campgrounds/:id/reviews/:reviewId` - delete a review

## Project Structure

```text
.
├── app.js
├── cloudinary/
├── controllers/
├── middleware.js
├── models/
├── public/
├── routes/
├── schemas.js
├── seeds/
├── utils/
└── views/
```

## Environment Variables

| Variable | Purpose |
| --- | --- |
| `DB_URL` | MongoDB connection string |
| `SECRET` | Session and cookie signing secret |
| `MAPBOX_TOKEN` | Mapbox API token for geocoding and maps |
| `CLOUDINARY_CLOUD_NAME` | Cloudinary cloud name |
| `CLOUDINARY_KEY` | Cloudinary API key |
| `CLOUDINARY_SECRET` | Cloudinary API secret |
| `PORT` | Optional server port, defaults to `3000` |

## Notes

- Uploaded campground images are stored in the `YelpCamp` Cloudinary folder.
- Reviews are deleted automatically when their campground is deleted.
- In production, set strong secrets and use a hosted MongoDB connection string.
