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
