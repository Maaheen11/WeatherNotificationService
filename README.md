# Weather Notification System

Designed and developed a weather notification system using a microservices architecture to deliver timely weather alerts to subscribed users. The performance is compared across three GCP deployment strategies: Serverless (Cloud Run), Containerized (Google Kubernetes Engine), and VM-Based (Compute Engine).

## Project Overview

This project explores the **impact of cloud deployment models** on the performance of a weather-based notification system. It uses real-time weather data to send notifications via email or SMS to users based on their preferences.

## Authors
- Swaifa Haque  
- Dhivya Mohan  
- Pegah Pourabdollah  
- Anila Satyavolu  
- Maaheen Yasin  

## Architecture

The system follows a microservices design with the following core components:

1. **User Subscription Service**: Collects user details (location, email/SMS preferences) and stores them in Google BigQuery.
2. **Weather API Service**: Fetches weather data using [WeatherStack](https://weatherstack.com/) based on user locations.
3. **Notification Service**: Orchestrated by Google Cloud Scheduler, this service sends personalized alerts using [SendGrid](https://sendgrid.com/).

![System Architecture](https://github.com/user-attachments/assets/e445fc66-aeb3-4f0d-bbf4-dc9cd4547825)

## Deployment Models

Each microservice is containerized with Docker and deployed on the following GCP platforms:

### 1. Cloud Run
- Fully managed serverless platform.
- Scales automatically based on requests.
- Cost-efficient for infrequent workloads.

### 2. Google Kubernetes Engine (GKE)
- Autopilot mode with horizontal pod autoscaling.
- High availability with a replication factor of 3.
- Exposed via LoadBalancer services.

### 3. Google Compute Engine (VM)
- Manual Docker container deployment on virtual machines.
- Offers fine-grained control over the environment.
- Serves as a baseline for performance comparison.

## Results

Performance metrics were collected using Google Cloud Monitoring.

### Latency
- **Cloud Run**: 1.7s  
- **Kubernetes**: 4.1s  
- **Compute Engine**: 2.8s  

### CPU Utilization
- Serverless showed the lowest utilization since it is event-driven.
- Kubernetes and VMs had higher usage due to continuous activity.

  ![image](https://github.com/user-attachments/assets/50edcb5d-02f8-4faa-b0ad-0947575fec0d)


**Conclusion**: Cloud Run offers the best balance between performance and cost for this workload.

## Security & Monitoring

- HTTPS-based communication secured using Google-issued OIDC tokens.
- Logs, latency, and resource utilization tracked via GCP Cloud Monitoring.

## Technologies Used

- Python (Flask)
- Docker
- Google Cloud Platform (Cloud Run, GKE, Compute Engine)
- BigQuery
- SendGrid
- WeatherStack API
- Google Cloud Scheduler
- Google Cloud Monitoring

## Repository

Explore the source code and setup instructions:

🔗 [Weather Notification Service Repository](https://github.com/dhivya94m/WeatherNotificationService)

