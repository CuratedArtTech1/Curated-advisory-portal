# Curated-advisory-portal

An advisory portal application with Supabase integration.

## Setup

1. Clone the repository
2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file based on `.env.example`:
   ```bash
   cp .env.example .env
   ```

4. Add your Supabase credentials to the `.env` file:
   - `SUPABASE_KEY`: Your Supabase anonymous key (found in your Supabase project settings)

## Supabase Configuration

The Supabase client is configured in `lib/supabase.js` with:
- **URL**: `https://crcncviqauycimvrmueb.supabase.co`
- **Key**: Loaded from the `SUPABASE_KEY` environment variable

## Usage

Import the Supabase client in your application:

```javascript
import supabase from './lib/supabase.js'

// Use the supabase client
const { data, error } = await supabase
  .from('your_table')
  .select('*')
```

## Deployment

### Quick Deploy to Netlify (Copy & Paste)

**Your repository:** `https://github.com/CuratedArtTech1/Curated-advisory-portal`

**Step 1: Get your Supabase Key**
1. Go to https://supabase.com/dashboard
2. Select your project
3. Go to Project Settings → API
4. Copy the `anon` `public` key

**Step 2: Deploy via Netlify UI**
1. Go to https://app.netlify.com/start
2. Click "Import from Git" → "GitHub"
3. Paste your repo URL: `https://github.com/CuratedArtTech1/Curated-advisory-portal`
4. Click on your repository to select it
5. Configure settings:
   - **Build command:** Leave empty (or `npm install` if needed)
   - **Publish directory:** `.`
6. Click "Show advanced" → "New variable"
   - **Key:** `SUPABASE_KEY`
   - **Value:** [Paste your Supabase anon key here]
7. Click "Deploy site"

**Step 3: Verify**
- Once deployed, your site will be live at `https://[random-name].netlify.app`
- The Supabase client will automatically use your environment variable

### Alternative: Deploy via Netlify CLI

```bash
# Install Netlify CLI
npm install -g netlify-cli

# Login to Netlify
netlify login

# Clone and navigate to your repo
git clone https://github.com/CuratedArtTech1/Curated-advisory-portal.git
cd Curated-advisory-portal

# Install dependencies
npm install

# Deploy (follow prompts, then add SUPABASE_KEY via UI)
netlify deploy
```

After deployment, add your `SUPABASE_KEY`:
1. Go to https://app.netlify.com
2. Select your site
3. Site settings → Build & deploy → Environment → Environment variables
4. Add variable: `SUPABASE_KEY` = [Your Supabase anon key]

### Environment Variables

Before deploying, ensure you set the `SUPABASE_KEY` environment variable in your deployment platform:

**Vercel:**
```bash
vercel env add SUPABASE_KEY
```

**Netlify:**
1. Connect your repository to Netlify:
   - Go to [netlify.com](https://netlify.com) and sign in
   - Click "Add new site" → "Import an existing project"
   - Choose your Git provider and select this repository
2. Configure build settings (if needed):
   - Build command: `npm run build` (or leave empty if no build step)
   - Publish directory: `.` (or your build output directory)
3. Add environment variable:
   - Go to Site settings → Build & deploy → Environment → Environment variables
   - Click "Add a variable"
   - Key: `SUPABASE_KEY`
   - Value: Your Supabase anonymous key (from https://supabase.com/dashboard → Project Settings → API)
4. Click "Deploy site"

**Heroku:**
```bash
heroku config:set SUPABASE_KEY=your_supabase_anon_key
```

**AWS/Azure/GCP:**
- Configure environment variables in your service configuration (Lambda, App Service, Cloud Functions, etc.)

**Docker:**
```bash
docker run -e SUPABASE_KEY=your_supabase_anon_key your-image
```

### General Deployment Steps

1. Push your code to your repository
2. Connect your deployment platform to your repository
3. Set the `SUPABASE_KEY` environment variable in your platform's settings
4. Deploy the application

The Supabase URL is already configured in the code and does not need to be set as an environment variable.

## Project Structure

```
.
├── lib/
│   └── supabase.js    # Supabase client configuration
├── .env.example       # Environment variable template
├── .gitignore         # Git ignore rules
├── package.json       # Project dependencies
└── README.md          # This file
```
