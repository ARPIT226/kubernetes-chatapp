## Creating pods and services
<img width="354" alt="image" src="https://github.com/user-attachments/assets/a9b72e0a-a419-419d-91fe-710da71c5c4f" />

## Pods status
<img width="345" alt="image" src="https://github.com/user-attachments/assets/274770fb-6120-4cc3-9231-56740222460b" />

## Services running
<img width="710" alt="image" src="https://github.com/user-attachments/assets/502081f4-9325-4016-ba83-84a17e5d379d" />

## Accessing application using DNS
<img width="959" alt="image" src="https://github.com/user-attachments/assets/3cc813b0-2571-4ad0-b58c-1722258911fd" />

## User registration
<img width="959" alt="image" src="https://github.com/user-attachments/assets/7e06d75b-2a71-4bb6-9bb0-35fc2a655c54" />

## User registration successfull
<img width="941" alt="image" src="https://github.com/user-attachments/assets/5f3871c4-69ff-4751-9688-d2b87775e282" />

## Health check test
To test Kubernetes liveness probe behavior, I intentionally misconfigured the NGINX pod (e.g., invalid config or broken /health endpoint). As a result, the container repeatedly failed the liveness probe and was restarted several times. Eventually, Kubernetes marked the pod as CrashLoopBackOff, indicating that it’s stuck in a failure loop and cannot recover without manual intervention.

<img width="361" alt="image" src="https://github.com/user-attachments/assets/fd933c7f-b3cb-4fd5-ade2-46635031326a" />

## Pod status watch after correcting the configuration
<img width="322" alt="image" src="https://github.com/user-attachments/assets/deeda7c4-58d4-42b1-8a83-b8d2f4128692" />
