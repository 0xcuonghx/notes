# BullMq

- Queue
  - id
  - status
  - removal
- Worker
  - events
  - concurrency
  - graceful shutdown: other worker take stalled of shutdown worker
  - Process busy because nodejs single threads
    - Stalled jbos
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

- Redis
