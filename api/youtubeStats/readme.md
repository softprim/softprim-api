# YouTube Stats API – Overview

The YouTube Stats API is a professional service developed by SoftPrim, designed to provide fast, structured, and reliable access to official YouTube video statistics.  
It is optimized for commercial platforms, reporting dashboards, automated systems, marketing agencies, and enterprise integrations.

This API allows you to retrieve:
- view counts
- like counts
- comment counts
- upload date
- video title
- available thumbnails
- channel name
- video language
- live status

The service is secured with individual client tokens and offers fast, standardized JSON responses suitable for any modern application.

## Key Advantages
- High performance with multiple simultaneous requests.
- Clean and predictable JSON structure.
- Stable and production-ready.
- Internal logging for traceability.
- Technical support included.
- Option to request fully custom APIs tailored to your business needs.

## Endpoint

```
POST https://api.softprim.ro/stats/youtubeStats
```

## Basic Usage

Example request:

```
POST https://api.softprim.ro/stats/youtubeStats
Headers:
  X-API-KEY: {YOUR_TOKEN}

Body:
{
    "links": "https://youtu.be/abc123, https://www.youtube.com/watch?v=xyz789"
}
```

## Access Token

You may have received a token together with this documentation.

If you do not yet have an active token, you can request one by emailing:
request@softprim.ro

Suggested subject line:
“Requesting Access Token – YouTube Stats API”


## Additional Documentation

More technical information, including full error descriptions and response formats, is available in **docs.md**.
