# BullMq

- Queue
  - id
  - status
  - removal
- Worker
  - events
  - concurrency
  - graceful shutdown: other workers take stalled of shutdown worker
  - Process busy because nodejs single threads
    - Stalled jobs
    - Sandboxed processors
    
- Jobs
  - FIFO / LIFO
  - job id
  - job data
  - deduplication
  - delayed
  - repeated
  - prioritised

- Lifecycle of a job: https://docs.bullmq.io/guide/jobs/getters
- Job schedule
  - Interval
  - Cron
  - Custom
- Flows
  - parent-child strategies
- Metrics
- Rate limit
- Redis
