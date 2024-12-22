## Capacity Planning for Rate Limiter

1. Determine the expected traffic load on the rate limiter system. eg. 10,000 requests / min.

2. Define the rate limiting algorithm and policies to be implemented. This includes setting limits on the number of requests allowed per unit of time.

3. Calculate the maximum number of requests per second (RPS) that the rate limiter needs to handle. This can be done by dividing the expected traffic load by the desired limit.

4. Identify the hardware and infrastructure components required to support the calculated RPS. Consider factors such as CPU, memory, network bandwidth, and storage.

5. Determine the scalability requirements of the rate limiter system. This involves assessing whether the system needs to handle increasing traffic in the future and planning for horizontal or vertical scaling accordingly.

6. Perform load testing to validate the capacity planning assumptions and identify any bottlenecks or performance issues.

7. Monitor the rate limiter system in production to ensure it is operating within the planned capacity. Make adjustments as necessary based on real-time traffic patterns and usage.

8. Regularly review and update the capacity planning as the traffic load and requirements of the rate limiter system evolve over time.
