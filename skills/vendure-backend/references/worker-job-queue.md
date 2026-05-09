# Worker and Job Queue

## Use This Reference For

- Long-running tasks
- Bulk import or export
- Notifications, indexing, or batch processing
- Any feature that should not block an API request

## Core Rule

If a task can noticeably delay an API response or depends on retries, move it behind a worker and queue.

## Worker Boundary

- Bootstrap the worker through the project's worker entrypoint rather than from a request path.
- Keep API mutations responsible for scheduling work, not for performing the work inline.
- Keep queued payloads small and domain-oriented so jobs stay easy to reason about.

## Job Queue Design

- Create a queue around a business capability, not around a generic verb.
- Put job handling code near the service that owns the capability.
- Make retry behavior deliberate for tasks that touch external systems.
- Return the scheduling result to the caller when immediate completion is not required.

## Typical Fits

- Search indexing
- Bulk catalog updates
- File import and export
- Email or webhook dispatch
- Background synchronization with external systems

## Review Checklist

1. Could this task block the request path.
2. Does it need retries or separate operational visibility.
3. Does it depend on worker-only infrastructure.
4. Should the caller receive a queued status instead of a final domain result.
