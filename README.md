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

### Environment Variables

Before deploying, ensure you set the `SUPABASE_KEY` environment variable in your deployment platform:

**Vercel:**
```bash
vercel env add SUPABASE_KEY
```

**Netlify:**
- Go to Site settings → Build & deploy → Environment
- Add `SUPABASE_KEY` with your Supabase anonymous key

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
