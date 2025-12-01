# YouTube MP3 Download API – Documentation

## Overview
This API allows clients to download the audio track (in **MP3 format**) of any public YouTube video by providing a valid YouTube link.  
All requests require a valid **API key** sent via header authentication.

API keys can be purchased by contacting: **request@softprim.ro**

---

## Base URL
```
https://vps.softprim.ro/ytconvert
```

---

## Authentication

All API requests **must** include the following HTTP header:

```
X-API-KEY: your_api_key_here
```

If the header is missing or invalid, the response will be:

```json
{
  "error": true,
  "message": "Invalid API Key"
}
```

---

## Endpoint: Download YouTube MP3

### **GET** `/ytconvert`

### Required Query Parameters

| Name         | Type   | Required | Description |
|--------------|--------|----------|-------------|
| `youtubelink` | string | Yes      | A valid YouTube link (supports both long and short URLs). |

Example accepted formats:
```
https://www.youtube.com/watch?v=VIDEO_ID
https://youtu.be/VIDEO_ID
```

---

## Response Format

### Success (200)

```json
{
  "error": false,
  "youtube_id": "VIDEO_ID",
  "file": "https://vps.softprim.ro/downloads/VIDEO_ID.mp3",
  "cached": false
}
```

#### Field Descriptions
- **error** – always `false` when the request succeeds  
- **youtube_id** – extracted video ID  
- **file** – direct downloadable MP3 link  
- **cached** – `true` if the file already existed on the server, `false` if freshly processed  

---

## Error Responses

### Missing YouTube link
```json
{
  "error": true,
  "message": "Missing youtubelink"
}
```

### Invalid YouTube link
```json
{
  "error": true,
  "message": "Invalid YouTube URL"
}
```

---

## Caching Mechanism

If a video was previously converted:
- the server returns the existing MP3 immediately  
- `cached: true` is included in the response  
- no reprocessing occurs  
- greatly improves performance and speed  

---

## Example Requests

### Using cURL
```bash
curl -G "https://vps.softprim.ro/ytconvert"      --data-urlencode "youtubelink=https://youtu.be/dQw4w9WgXcQ"      -H "X-API-KEY: YOUR_API_KEY_HERE"
```

### Using JavaScript
```javascript
fetch("https://vps.softprim.ro/ytconvert?youtubelink=https://youtu.be/dQw4w9WgXcQ", {
    headers: { "X-API-KEY": "YOUR_API_KEY_HERE" }
})
.then(res => res.json())
.then(console.log);
```

---

## Getting an API Key

API keys are provided **against payment**.

To request one, contact:

📧 **request@softprim.ro**

---

## Terms & Notes
- You must comply with YouTube’s Terms of Service.
- Do not misuse the API for scraping or mass downloading.
- SoftPrim is not responsible for how you use the downloaded content.
- Abuse may lead to API key suspension.

---

## Changelog

### v1.0 – Initial Release
- MP3 extraction
- API key authentication
- YouTube link validation
- Caching support
- Clean internal logging for server errors

---

© SoftPrim – All rights reserved.
