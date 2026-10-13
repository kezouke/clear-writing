# Style Examples

These examples are fictional. Reuse their structure, not their facts.

## Explain a concept

Overloaded:

> It is important to note that caching represents a significant performance optimization mechanism that enables improved efficiency of repeated computational operations.

Clear:

> A cache stores a result so the next request can reuse it. For example, a service retrieves an exchange rate from an external API once, then serves the saved rate for five minutes. This reduces API calls, but the rate can become stale during those five minutes.

The explanation retains the mechanism, example, and limitation.

## Preserve uncertainty

Source: latency rose from 80 to 120 ms while the request queue grew. The cause
has not been established.

Incorrect compression:

> The queue increased latency by 50%.

Clear:

> Latency rose from 80 to 120 ms, a 50% increase. The request queue grew during the same period. These observations do not establish whether the queue caused the increase.

A rewrite must not turn coincidence into a proven cause. Add the measurement
period if the source provides it.

## Explain a calculation

Overloaded:

> To ensure a deep understanding, it is essential to consider the fundamental distinction between business performance indicators and actual movements of monetary resources.

Clear:

> A company sells an item for 150 that cost it 100. The profit is 50. The customer will pay next month, so the sale has brought in no cash yet. Profit records the result of the sale; the cash arrives later. This example excludes taxes and other expenses.

A concrete situation establishes the distinction. The assumptions keep it
accurate.

## Report technical work

Overloaded:

> Comprehensive work was conducted to enhance system reliability through important improvements to error handling.

Clear:

> Added retries after HTTP 429. A retry respects Retry-After and stops after three attempts. Checks for a successful retry and exhausted attempts passed.

Report only changes and checks that actually happened.
