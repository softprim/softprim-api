# Technical Documentation – YouTube Stats API

This document provides the response formats and potential error messages returned by the API.

---

## Endpoint
```
POST https://api.softprim.ro/stats/youtubeStats
```

### Required Header
```
X-API-KEY: CLIENT_TOKEN
```

### JSON Body
```
{
    "links": "url1,url2,url3"
}
```

---

## Successful Response Structure
```
{
    "status": "ok",
    "error": null,
    "data": {
        "VIDEO_ID": {
            "views": 123,
            "likes": 45,
            "comments": 10,
            "uploadedAt": "2024-01-05T12:00:00Z",
            "title": "Video Title",
            "thumbnails": {...},
            "channelTitle": "Channel Name",
            "language": "en",
            "liveStatus": "none"
        }
    }
}
```

---

## Possible Errors

### 1. Invalid or Missing Token
```
{
    "status": "error",
    "error": "Unauthorized access",
    "data": null
}
```

### 2. Invalid JSON Body
```
{
    "status": "error",
    "error": "Invalid JSON body. Example: {"links":"url1,url2"}",
    "data": null
}
```

### 3. No Valid YouTube Video URLs Found
```
{
    "status": "error",
    "error": "No valid video IDs found.",
    "data": null
}
```


---

## Custom API Development

SoftPrim also provides development of custom APIs tailored to specific workflows, integrations, or data models.  
For custom requests, contact: request@softprim.ro
