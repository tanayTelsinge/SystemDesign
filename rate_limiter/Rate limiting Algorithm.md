When to Use Each Algorithm
- Fixed Window: Simple, low-traffic systems.
- Sliding Window Counter: Balances precision and memory efficiency.
- Sliding Window Log: High-precision requirements.
- Token Bucket: Allows bursts; suitable for APIs.
- Leaky Bucket: Enforces smooth, constant request rates.
- Concurrent Limiting: Resource-constrained systems.

1. Fixed Window Algorithm
  Concept:
  - Divide time into fixed intervals (e.g., 1-minute windows).
  - Count requests in the current window.
  - If the count exceeds the limit, reject requests.
  Pros:
  - Simple to implement.
  - Suitable for low-traffic systems.
  Cons:
  - Boundary issue: Bursts at the end of one window may overflow into the next.
  Example:
  - Limit: 60 requests per minute.
  - If 60 requests are received in the first 59 seconds, the next request will be rejected.

2. Sliding Window Counter
  Concept:
  - Divide the time window into smaller slots (e.g., seconds in a 1-minute window).
  - Track counts for recent slots and sum them up for the sliding window.
  Pros:
  - Mitigates boundary issues compared to Fixed Window.
  - Efficient in terms of memory and processing.
  Cons:
  - Less precise than Sliding Window Log.
  Example:
  - Limit: 60 requests per minute.
  - Count requests across the last 60 seconds dynamically.

3. Sliding Window Log
  Concept:
  - Store exact timestamps of each request.
  - Count requests within the last time window (e.g., last 1 minute).
  Pros:
  - Most accurate algorithm.
  - Eliminates boundary issues completely.
  Cons:
  - High memory overhead for storing timestamps.
  - Less efficient at scale.
  Example:
  - Limit: 60 requests per minute.
  - For each request, check timestamps to count recent ones.

4. Token Bucket Algorithm
  Concept:
  - Tokens are added to a bucket at a fixed rate.
  - Each request consumes a token.
  - If the bucket is empty, the request is rejected or delayed.
  Pros:
  - Allows burst handling (up to bucket size).
  - Simple and efficient.
  Cons:
  - May allow bursts beyond the average rate temporarily.
  Example:
  - Limit: 10 tokens/second, bucket size: 100.
  - Up to 100 requests can be handled instantly if tokens are available.

5. Leaky Bucket Algorithm
  Concept:
  - Requests are added to a "bucket" (queue).
  - The bucket processes requests at a fixed rate, like water leaking from a bucket.
  - Excess requests overflow and are rejected.
  Pros:
  - Smoothens traffic, ensuring a consistent request rate.
  - Prevents bursts completely.
  Cons:
  - Does not allow bursts.
  Example:
  - Limit: 10 requests/second.
  - Requests exceeding this rate are dropped immediately.

6. Concurrent Request Limiting
  Concept:
  - Limits the number of concurrent requests being processed at any given time.
  - If the limit is reached, additional requests are queued or rejected.
  Pros:
  - Useful for services with limited resources (e.g., database connections).
  Cons:
  - Does not enforce a rate over time.
  Example:
  - Limit: 100 concurrent requests.
  - 101st request is queued or rejected.