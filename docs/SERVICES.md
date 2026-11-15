# PrePilot — Services Architecture

# Module 2.1 — Code Runner Service

**Status:** Architecture Definition

## 1. Purpose

The Code Runner Service is responsible for securely compiling and executing programming code submitted by candidates during coding assessments and practice sessions.

## 2. Supported Programming Languages

Initial language support:

- Java
- Python
- C
- C++

Additional languages may be introduced in future versions.

## 3. Core Components

### 3.1 Execution API
- Receive code execution requests.
- Validate request information.
- Forward requests to the execution system.
- Return execution status.

### 3.2 Language Manager
- Identify the selected language.
- Select the appropriate compiler or interpreter.
- Manage language-specific configurations.

### 3.3 Sandbox Environment
- Execute untrusted code in isolation.
- Restrict filesystem access.
- Restrict network access.
- Prevent access to application secrets.
- Clean up execution environments.

### 3.4 Compiler and Interpreter
- Compile Java, C and C++ programs.
- Interpret Python programs.
- Capture compilation errors.

### 3.5 Execution Engine
- Execute compiled or interpreted programs.
- Capture standard output.
- Capture standard error.
- Monitor execution status.

### 3.6 Test Case Manager
- Manage input test cases.
- Compare actual and expected outputs.
- Calculate test case results.
- Support hidden test cases.

### 3.7 Resource Limiter
- CPU limits
- Memory limits
- Execution time limits
- Process limits
- Output size limits

### 3.8 Result Processor
- Return execution results.
- Return compilation errors.
- Return runtime errors.
- Return timeout status.
- Return test case statistics.

## 4. Execution Workflow

1. Candidate submits code.
2. Backend API validates the request and permissions.
3. API sends an execution job to the Code Runner.
4. Code Runner identifies the programming language.
5. An isolated execution environment is created.
6. Code is compiled or interpreted.
7. Program executes against permitted test cases.
8. Output is captured and evaluated.
9. Execution environment is destroyed.
10. Results are returned to the API.
11. Candidate receives the results.

## 5. Security Requirements

- Strong execution isolation.
- No unrestricted network access.
- CPU and memory restrictions.
- Execution timeout enforcement.
- Filesystem restrictions.
- Process isolation.
- Temporary storage cleanup.
- Protection against fork bombs and resource exhaustion.
- No access to backend credentials or secrets.
- Secure job communication.

## 6. Communication

The Code Runner communicates with the Backend API through a controlled execution interface.

Long-running execution tasks should be handled asynchronously using a job queue.

The Code Runner must not access the production database directly.

## 7. Monitoring

- Execution success rate
- Compilation failure rate
- Runtime failure rate
- Average execution time
- Timeout frequency
- Resource consumption
- Queue processing time

## 8. Development Phases

1. Define execution request and response formats.
2. Evaluate sandbox technologies.
3. Implement isolated execution.
4. Add language support.
5. Implement test case evaluation.
6. Add resource restrictions.
7. Integrate with Backend API.
8. Perform security testing.

## 9. Definition of Completion

- Supported languages execute correctly.
- Test cases are evaluated accurately.
- Resource limits are enforced.
- Untrusted code is isolated.
- Execution results reach the Backend API.
- Security testing is completed.

**Architecture rule:** Never execute candidate-submitted code directly inside the PrePilot API server or an unrestricted host environment.



---

# Module 2.2 — Background Workers

**Status:** Architecture Definition  
**Technology:** NestJS, TypeScript, Redis and BullMQ

## 1. Purpose

The Background Workers system processes time-consuming, scheduled and asynchronous tasks without blocking normal API requests.

It improves application responsiveness and helps PrePilot process tasks reliably.

## 2. Core Components

### 2.1 Job Queue
- Store pending background jobs.
- Maintain job status.
- Distribute jobs to available workers.
- Support job prioritization.

### 2.2 Worker Processor
- Retrieve jobs from queues.
- Execute assigned tasks.
- Update job status.
- Handle processing failures.

### 2.3 Scheduler
- Schedule recurring tasks.
- Execute time-based operations.
- Manage scheduled notifications.
- Trigger periodic maintenance tasks.

### 2.4 Email Worker
- Send registration emails.
- Send verification emails.
- Send password reset emails.
- Send application confirmation emails.
- Send interview invitations.

### 2.5 Notification Worker
- Process candidate notifications.
- Process employer notifications.
- Generate application updates.
- Handle notification delivery.

### 2.6 Resume Processing Worker
- Process uploaded resume files.
- Extract supported document text.
- Prepare resume information for further processing.
- Report processing status.

### 2.7 AI Background Worker
- Process longer AI tasks.
- Generate requested reports.
- Handle asynchronous AI operations.
- Store task results securely.

### 2.8 Retry Manager
- Retry temporary failures.
- Apply configurable retry limits.
- Use retry delays.
- Handle permanently failed jobs.
- Support failed-job inspection and recovery.

### 2.9 Monitoring
- Track pending jobs.
- Track completed jobs.
- Track failed jobs.
- Monitor processing time.
- Monitor worker availability.

## 3. Background Job Categories

Initial proposed queues:

- Email Queue
- Notification Queue
- Resume Processing Queue
- AI Processing Queue
- Scheduled Tasks Queue

Queues may be separated or combined based on workload and operational requirements.

## 4. Job Processing Workflow

1. A user performs an action.
2. Backend API validates the request.
3. Backend API completes the required primary database operation.
4. A background job is created.
5. The job enters the appropriate queue.
6. An available worker retrieves the job.
7. The worker processes the task.
8. Job status is updated.
9. Failed jobs are retried according to configured policies.
10. Final results are recorded where required.

## 5. Technology Stack

- NestJS
- TypeScript
- Redis
- BullMQ

## 6. Reliability Requirements

- Retry policies
- Failed-job handling
- Job status tracking
- Duplicate-processing protection
- Idempotent job processing
- Graceful worker shutdown
- Queue monitoring
- Controlled concurrency

## 7. Security Requirements

- Validate job payloads.
- Do not store passwords or secrets in job payloads.
- Protect access to Redis.
- Restrict worker permissions.
- Secure sensitive file processing.
- Avoid exposing private user data in logs.
- Apply appropriate retention policies.

## 8. Communication

The Backend API creates background jobs through BullMQ.

Workers consume jobs from Redis-backed queues and communicate with authorized backend modules or external providers as required.

Workers must not bypass application authorization or business rules.

## 9. Development Phases

1. Configure Redis.
2. Integrate BullMQ with NestJS.
3. Create queue infrastructure.
4. Implement email worker.
5. Implement notification worker.
6. Implement resume processing worker.
7. Implement AI background processing.
8. Configure retry and failure handling.
9. Implement monitoring.
10. Perform reliability and security testing.

## 10. Definition of Completion

- Jobs enter queues correctly.
- Workers process jobs successfully.
- Failed jobs are handled safely.
- Retry policies work.
- Duplicate processing is controlled.
- Job execution is monitored.
- Sensitive data is protected.

**Architecture rule:** Background Workers handle asynchronous operations independently. Critical business transactions must be completed safely by the backend before dependent jobs are processed.