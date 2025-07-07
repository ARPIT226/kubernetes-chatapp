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

## nginx-ingress controller
<img width="917" alt="image" src="https://github.com/user-attachments/assets/8bf624b8-97d4-41e9-bd6d-8258750cdd18" />

## For ingress controller, changed the nginx svc type to clusterIP so that only ingress controller can manage and route traffic to the nginx and nginx ip is not exposed globally. (more secure)
<img width="395" alt="image" src="https://github.com/user-attachments/assets/56f267a0-646f-4204-b20f-15945c7af9f5" />

## Application is accessible from the nginx-ingress-controller's external ip (<externalIP>/home)
All the routes having prefix "/home" will be redirected to the home page as set in the configuration. (/home/abc, /home/apple, etc)

<img width="959" alt="image" src="https://github.com/user-attachments/assets/fc96a1ae-1b2b-4201-9777-a36eda129e0a" />

## Access locally using custom domain (confined access)
Set the IP and a custom dns in the /etc/hosts which allows us to access the application using the domain name but restricted to the instance only

<img width="959" alt="image" src="https://github.com/user-attachments/assets/837ceeff-24c5-48bb-9d23-e2a143e655f1" />

## Accessing application using the domain set
<img width="620" alt="image" src="https://github.com/user-attachments/assets/973c37d6-1933-4cbc-85b0-2728305e4457" />

## ALB-ingress-controller implementation
<img width="620" alt="image" src="https://github.com/user-attachments/assets/1e243d88-4fbe-4e43-a933-cb317a87db0f" />

## Accessing application using ALB-ingress-controller DNS
<img width="959" alt="image" src="https://github.com/user-attachments/assets/ba4a5a39-41c6-44ba-8c9b-dc8d4dbd0416" />

## Auto Scaling -------------------------
(install metric server if not present and describe resource capacity and limit of each type of pod)

## Horizontal Pod Autoscalar in the cluster
<img width="431" alt="image" src="https://github.com/user-attachments/assets/716c277b-e0e5-42db-87fb-7c4eef78c3aa" />

## Current pods status
<img width="327" alt="image" src="https://github.com/user-attachments/assets/ecf0479b-b1b1-4636-b096-315ce67a1c7f" />

## Increased the load on both the pods using an infintite loop for testing using below cmds
``` while true; do wget -q -O- http://nginx; done ``` 
``` while true; do wget -q -O- http://django:8000/; done ```

## Current cpu limit exceeds (2% -> 126%) on both django and nginx pods
<img width="471" alt="image" src="https://github.com/user-attachments/assets/6a35527f-73f3-4a59-8e2e-086ddb0aa681" /> <img width="434" alt="image" src="https://github.com/user-attachments/assets/e939f7c4-8083-4974-970d-c9922bba6fb9" />

## Automatically others django-pods and nginx-pods got added up to handle the huge incoming traffic
<img width="309" alt="image" src="https://github.com/user-attachments/assets/42206156-6365-492f-8184-74a4dcbf3413" /> <img width="310" alt="image" src="https://github.com/user-attachments/assets/789e4fab-c77c-4409-a733-ee965dbfc932" />

## And automically scales down as the load decreases
<img width="331" alt="image" src="https://github.com/user-attachments/assets/fa82f19b-e43f-4b7d-9b52-9c5aa8a601b6" />

## VPA description before inforcing load
<img width="293" alt="image" src="https://github.com/user-attachments/assets/34f72b2d-0801-4936-bf11-f3da7a51dba8" />

## After giving load, the CPU usage increased hence VPA responded with a higher CPU recommendation (25m → 49m).
<img width="302" alt="image" src="https://github.com/user-attachments/assets/d57a1a7e-541c-46d7-ba0c-26ede5693385" />

## Cluster auto scaling
Created a test Deployment requesting high resources:

```
requests:
  cpu: "1600m"
  memory: "2.5Gi"
```

<img width="949" alt="image" src="https://github.com/user-attachments/assets/41de7a79-3813-46bc-9a78-e564f65a1b81" />

Logs show that Expanding Node Group and 1 more node is needed

Total nodes would be 2->3
<img width="484" alt="image" src="https://github.com/user-attachments/assets/57ab6023-e2ef-4602-9c58-d09dd329f1d1" />


