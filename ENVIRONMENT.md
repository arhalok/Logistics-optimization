# Environment and Setup Contract

## Required repository files
- `.env.example` contains variable names and safe placeholder values only.
- `.gitignore` excludes `.env.local`, secrets, build artifacts and local database files.
- `README.md` documents exact install, dev, test, lint and build commands.

## Example variable names
```dotenv
NEXT_PUBLIC_APP_NAME="Kirana Setu Demo"
NEXT_PUBLIC_MAP_TILE_URL=""
DATABASE_URL=""
NEXT_PUBLIC_SUPABASE_URL=""
NEXT_PUBLIC_SUPABASE_ANON_KEY=""
SUPABASE_SERVICE_ROLE_KEY=""
OSRM_BASE_URL=""
VROOM_BASE_URL=""
ROUTING_MODE="demo"
PAYMENT_MODE="simulated"
```

Do not require every variable if the related provider is not configured. Validate environment variables at startup and show a clear integration status. Never expose a service-role key through a `NEXT_PUBLIC_` variable.

## Expected scripts
The actual scripts depend on the chosen package manager, but README should document equivalents for:
- development server
- lint
- typecheck
- unit tests
- end-to-end tests if configured
- production build
- seed/reset demo data

Do not claim a command exists until it has been added to `package.json`.
