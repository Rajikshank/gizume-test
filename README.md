LinkBait
Create beautiful shareable link bundles with AI-generated thumbnails.

LinkBait takes one or more URLs, understands their content, creates a social-card-style thumbnail, lets the user edit the final text and layout, and publishes a unique share URL with a stable OG image.

Overview
Most link sharing tools only give you a plain list of links.

LinkBait adds a much better layer on top:

it crawls the links
it generates artwork related to the content
it gives the user an editor to refine the thumbnail
it publishes a social-ready image for the final short link
That means the shared URL looks much better on platforms like X, LinkedIn, WhatsApp, Discord, and Facebook.
 
How It Works
User enters URLs
    ↓
App crawls page metadata
    ↓
AI generates SVG artwork + draft copy
    ↓
User edits title, subtitle, font, colors, and layout
    ↓
App renders final PNG with next/og
    ↓
PNG is attached as the OG image for the share URL
    ↓
User shares the bundle anywhere
Main Features
Add one or more URLs to a single bundle
Crawl page metadata and OG signals
Generate content-aware thumbnail artwork
Edit share title and subtitle in a dedicated editor
Adjust font, alignment, size, colors, and text position
Publish a final PNG for social sharing
Create a unique public bundle URL
Show all links on a clean public share page
Example Use Cases
Creator link collections
Product launch bundles
Newsletter issue roundups
Resource collections
Event or campaign landing links
Curated reading lists
Tech Stack
Framework: Next.js 16 App Router
Language: TypeScript
Styling: Tailwind CSS 4 + shadcn/ui
Animation: Framer Motion
Database: Supabase
Crawling: Cheerio
AI generation: Groq SDK
Image rendering: next/og
Deployment: Vercel
Project Structure
src/
  agents/         Generation orchestration
  app/            Pages, routes, server actions
  components/     UI and editor components
  lib/            Shared logic and data helpers
  tools/          Crawl, SVG generation, rendering, storage

public/
  fonts/          Bundled fonts used by the renderer

supabase/
  schema.sql      Database schema
Important Routes
/ Landing page
/editor/[code] Thumbnail editor
/s/[code] Public share page
/dashboard Bundle dashboard
API Endpoints
POST /api/generate Generate a new bundle draft
GET /api/jobs/[code] Check generation status
GET /api/editor/[code] Load editor data
POST /api/regenerate-svg Regenerate artwork or copy
POST /api/convert-svg Publish the final PNG
Editor Features
The editor is the heart of the app.

Users can:

edit the share title
edit the share subtitle
switch font family
change layout template
change alignment
change title size
adjust colors
move the text block
preview before publishing
publish the final social image
Environment Variables
Create a .env.local file:

NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
GROQ_API_KEY=your_groq_api_key
NEXT_PUBLIC_SITE_URL=http://localhost:3000
Local Development
Install dependencies:

npm install
Start the development server:

npm run dev
Open:

http://localhost:3000
Production Build
Before deploying, run:

npm run lint
npx next build --webpack
If both pass and the environment variables are configured correctly, the app is ready for deployment.

Deployment
Recommended platform: Vercel

Deployment Checklist
Connect the repository to Vercel
Add the required environment variables
Apply the schema in supabase/schema.sql
Configure Supabase storage for generated thumbnails
Verify the public share route /s/[code]
Confirm the OG image appears correctly on shared links
Production Notes
For this app to stay reliable in production:

the editor preview and published PNG must stay in sync
generated SVG artwork should remain text-free
the editor text must be the final source of truth
crawl failures should degrade gracefully
uploaded PNGs should remain stable for social crawlers
next/og output must stay compatible with Vercel runtime constraints


Who Built This ds
Developed by Rajikshan