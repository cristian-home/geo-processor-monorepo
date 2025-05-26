# CANDIDATE ASSESSMENT - SENTIMENT ANALYSIS

## Overview

Build a minimal "geo-processor" microservice ecosystem that works with map coordinates:

1. **Python service (FastAPI)** exposing one endpoint to process a list of latitude/longitude points.
   Expect a JSON body of the form:

   ```json
   {
     "points": [
       { "lat": 40.7128, "lng": -74.0060 },
       { "lat": 34.0522, "lng": -118.2437 },
       ...
     ]
   }
   ```

   - If the top-level points field is missing, not an array, empty, or any entry lacks numeric lat/lng, return 400 Bad Request with a clear error message.
   - Scan all lat values to find:
     - north = maximum latitude
     - south = minimum latitude
   - Scan all lng values to find:
     - east = maximum longitude
     - west = minimum longitude

   # Compute the centroid

   - Simply average the coordinates:
     ```python
     centroid_lat = sum(p["lat"] for p in points) / len(points)
     centroid_lng = sum(p["lng"] for p in points) / len(points)
     ```

## Return a well-formed JSON response

```json
{
  "centroid": { "lat": 37.3825, "lng": -96.1248 },
  "bounds": {
    "north": 40.7128,
    "south": 34.0522,
    "east": -74.006,
    "west": -118.2437
  }
}
```

- FastAPI + Pydantic makes validation and serialization trivial.
- Use Python's built-in `min()`, `max()`, and `sum()` for the math.
- Keep the service stateless—caching is handled at the NestJS layer.
- Document your function signatures and error responses clearly in code and in your README.

2. **NestJS API** forwarding requests to the Python service, validating input, caching results.

3. **Next.js frontend** letting a user submit coordinates, then visualizing the computed bounding box and centroid on a simple map.

# Deliverables

1. Repository, either mono or multi repo approach and document your reasoning behind it
2. Readme file with all decisions, instructions on how to run
3. Python repo
4. NestJS repo
5. NextJS repo
