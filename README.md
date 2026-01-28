
# Astrology MVP - Vedic + Nadi + Numerology

## Quick Start

1. **Database setup:**
```bash
psql -U postgres -f 01_create_schema.sql
```

2. **Environment:**
```bash
cp .env.template .env
# Fill DB credentials and API keys
```

3. **Install & run:**
```bash
npm install
npm run dev  # or npm start
```

4. **Test onboarding:**
```bash
curl -X POST http://localhost:3000/api/v1/astro/natal-chart \
  -H 'Content-Type: application/json' \
  -d '{
    "birth_date": "1986-08-07",
    "birth_time": "06:40:00",
    "latitude": 30.5,
    "longitude": 79.39,
    "timezone": "+05:30"
  }'
```

## Architecture

- **Astro Service:** VedicAstroAPI / DivineAPI wrapper
- **Numerology Service:** RoxyAPI / Astrology-API.io wrapper
- **Nadi Service:** Custom rules engine (your IP)
- **Fusion Service:** Orchestrates all 3 + outputs guidance
- **Daily Cron:** Runs at 4 AM, generates predictions for all users

## Replace Mock APIs

1. **Vedic:** Get API key from vedicastroapi.com or divineapi.com
2. **Numerology:** Get key from roxyapi.com or astrology-api.io
3. **Nadi:** Expand rules in /api/v1/nadi/windows endpoint

## Next Steps

1. Add WhatsApp integration (whatsapp-business-api)
2. Add user auth (JWT)
3. Add web dashboard (React frontend)
4. Add ML feedback loop (outcome_score → model retraining)

## Scale to Production

- Move to AWS RDS (PostgreSQL)
- Add Redis queue for daily jobs
- Deploy to Vercel / Railway / Render
- Add rate limiting and API caching

**Timeline to 10K users:** 4-6 weeks development
**Monthly cost:** $350-850 (see previous message)
