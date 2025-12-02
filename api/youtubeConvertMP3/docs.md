# SoftPrim YouTube Conversion API – Official Documentation

## Overview
The **SoftPrim YouTube Conversion API** provides a fast, scalable, and reliable solution for converting YouTube videos into audio files through an asynchronous processing system.  
It is designed for developers who need high‑performance media extraction for web platforms, mobile apps, bots, and automation services.

Our system uses a **job‑queue architecture**, ensuring stable, non‑blocking conversions even under high load.

All requests **require a valid API key**, sent through HTTP headers.

For commercial access, API keys can be purchased by contacting:  
📧 **request@softprim.ro**

---

## Base URL
```
https://vps.softprim.ro/
```

---

# Authentication

Every request to the API must include the following HTTP header:

```
X-API-KEY: YOUR_API_KEY_HERE
```

Requests without a valid key will be rejected with:

```json
{
  "error": true,
  "message": "Invalid API Key"
}
```

API keys are managed securely and issued on request.  
For commercial use, bulk processing, or enterprise-tier usage, contact:

📧 **request@softprim.ro**

---

# Endpoints

## 1. `/ytconvert`
### Description
Starts a new YouTube audio conversion job.

### Method
```
GET /ytconvert?youtubelink=URL&format=mp3
```

### Query Parameters
| Parameter | Required | Description |
|----------|----------|-------------|
| `youtubelink` | Yes | Valid YouTube link (full or short URL) |
| `format` | No | Output format, default: `mp3` |

### Example Request
```
GET https://vps.softprim.ro/ytconvert?youtubelink=https://youtu.be/VIDEO_ID
```

### Successful Response
```json
{
  "error": false,
  "status": "queued",
  "job_id": "VIDEOID_mp3",
  "check_url": "https://vps.softprim.ro/ytstatus?id=VIDEOID_mp3"
}
```

This indicates your job has been added to the queue and will be processed shortly.

---

## 2. `/ytstatus`
### Description
Returns the current status of a conversion job.

### Method
```
GET /ytstatus?id=JOB_ID
```

### Example Responses

#### Pending
```json
{ "status": "pending" }
```

#### Downloading
```json
{
  "status": "downloading",
  "id": "VIDEOID"
}
```

#### Finished
```json
{
  "status": "finished",
  "file": "https://vps.softprim.ro/download/VIDEOID.mp3"
}
```

#### Error
```json
{
  "status": "error",
  "debug": [...]
}
```

---

# Workflow Summary

### 1. You call `/ytconvert`
- You send a YouTube link.
- The API validates it.
- A job file is created in the processing queue.
- You receive a `job_id`.

### 2. Worker processes the job
- Downloads audio using `yt-dlp`.
- Converts it into the requested format.
- Saves output to the public download directory.
- Writes a final status file.

### 3. You call `/ytstatus`
- Check until status = `finished`.
- Receive the direct download URL.

---

# Example Usage

### Conversion Request
```
GET https://vps.softprim.ro/ytconvert?youtubelink=https://youtu.be/VIDEO
```

### Status Check
```
GET https://vps.softprim.ro/ytstatus?id=VIDEO_mp3
```

### Download File
```
https://vps.softprim.ro/download/VIDEO.mp3
```

---

# API Key Access

SoftPrim offers a stable and production‑ready conversion service with:
- high‑speed worker processing  
- scalable queue system  
- enterprise-level uptime  
- commercial SLA availability  

To obtain an API key, contact:

📧 **request@softprim.ro**

Keys are delivered instantly after payment confirmation.

---

# Integration Example (JavaScript Fetch)

```javascript
fetch("https://vps.softprim.ro/ytconvert?youtubelink=https://youtu.be/VIDEO", {
  headers: { "X-API-KEY": "YOUR_API_KEY" }
})
.then(res => res.json())
.then(console.log);
```

---

# Requirements and Notes
- You must comply with YouTube Terms of Service.
- Do not use the API for scraping or mass copyright infringement.
- Abuse or illegal usage may result in key suspension.
- Processing times vary depending on video length & system load.

---

# Changelog
### v1.0 – Initial Public Release
- Conversion queue
- Status tracking
- Full download URL responses
- Secure API Key authentication
- Worker‑based asynchronous pipeline

---

© SoftPrim – All Rights Reserved.
