# Personal Blog

A modern, full-stack blog platform built with Next.js and Prisma, featuring a clean interface for sharing technical articles, project insights, and development experiences.

## Features

- 📝 Dynamic blog post management with MDX support
- 🎨 Responsive, modern UI design
- 🔍 SEO optimized with meta tags and RSS feed
- 💾 PostgreSQL database with Prisma ORM
- 🚀 Deployed on Vercel with continuous deployment
- 📱 Mobile-friendly reading experience
- 🏷️ Tag and category organization
- 💬 Code syntax highlighting for technical content

## Tech Stack

**Frontend:**
- Next.js 14 (App Router)
- React
- TypeScript
- Tailwind CSS

**Backend:**
- Prisma ORM
- PostgreSQL
- REST API routes

**DevOps:**
- Vercel (hosting & CI/CD)
- GitHub (version control)
- Neon/Supabase (database hosting)

## Getting Started

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL database (local or cloud)
- Git

### Installation

1. Clone the repository
```bash
git clone https://github.com/KaanIsmet/personal-blog.git
cd personal-blog
```

2. Install dependencies
```bash
npm install
```

3. Set up environment variables
```bash
cp .env.example .env
```

Add your database connection string:
```
DATABASE_URL="postgresql://user:password@localhost:5432/blog_db"
```

4. Initialize the database
```bash
npx prisma migrate dev
npx prisma generate
```

5. Run the development server
```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

## Database Schema

```prisma
model Post {
  id          String   @id @default(cuid())
  title       String
  slug        String   @unique
  content     String
  excerpt     String?
  published   Boolean  @default(false)
  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
  tags        Tag[]
}

model Tag {
  id    String @id @default(cuid())
  name  String @unique
  posts Post[]
}
```

## Project Structure

```
personal-blog/
├── app/                  # Next.js app directory
│   ├── blog/            # Blog routes
│   ├── about/           # About page
│   └── api/             # API routes
├── components/          # React components
├── lib/                 # Utility functions
├── prisma/             # Database schema & migrations
├── public/             # Static assets
└── styles/             # Global styles
```

## Deployment

This project is configured for seamless deployment on Vercel:

1. Push code to GitHub
2. Import project in Vercel dashboard
3. Add `DATABASE_URL` environment variable
4. Deploy automatically on every push to main

## Development Roadmap

- [x] Initial blog setup with Next.js + Prisma
- [x] Basic post creation and rendering
- [x] Responsive design
- [ ] Search functionality
- [ ] Comments system (Giscus integration)
- [ ] Newsletter subscription
- [ ] Analytics integration
- [ ] Dark mode toggle
- [ ] Reading time estimates

## Scripts

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run start        # Start production server
npm run lint         # Run ESLint
npx prisma studio    # Open Prisma Studio (database GUI)
npx prisma migrate   # Run database migrations
```

## Content Management

Blog posts are written in MDX format and stored in the database. To create a new post:

1. Use the admin interface (coming soon) or Prisma Studio
2. Write content in Markdown with optional JSX components
3. Set `published: true` to make it live

## Contributing

This is a personal project, but suggestions and feedback are welcome! Feel free to open an issue or submit a pull request.

## License

MIT License - feel free to use this code for your own projects.

## Contact

**Kaan Ismet Okul**
- Email: Ismet.Kaan.Okul@gmail.com
- LinkedIn: [linkedin.com/in/kaan-okul](https://linkedin.com/in/kaan-okul)
- GitHub: [@KaanIsmet](https://github.com/KaanIsmet)

---

Built with ☕ and code by Kaan Okul
