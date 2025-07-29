# system-design-saas
Conceptual system design for a hipotetical SaaS

# The Business

Our SaaS is a professional photo album where a photographer can upload photos into albuns and sell the photos for one specific client or to the public. The client select the desired photos for a fixed price per picture, and receive a link to download a zip file containing the purchased files.

# Microservices Architecture Proposal

## Service Decomposition

### User Service

This Service will be responsible to store essential user data like name, surname, email and role (Photographer/Client/Admin). For security reasons, we dont will store sensible data of credit cards, delegating this feature for a payment gateway.

### Album Service

This service will be responsible to manage the uploads to a object store service (like AWS S3 or Google Coud Storage) and organize the associated data like album's name, bucket folder link, visibility, owner and client. Everytime that a new photo is uploaded, an event is sended to the message queue and the message consumed by the Thumbnail Service that creates a thumbnail image to be presented to the clients. 

### Thumbnail Service

This service is responsible to create a thumbnail for every uploaded image, decreasing the resolution and applying a watermark.

### Jobs Service

This service will implement scheduled jobs to do operations like delete expired albumns, expire purchase links, collect data to generate selling reports and any other background operation.

### Checkout Service

This service is responsible to manage the payments status and comunication with our payment gateway. When a succesfull payment 

### Download Service

This service will create a zip file with the purchased photos and stores the generated link, 

## Service Discovery & Communication

## High Level Diagram

# Database Design and Data Management

## Database Choice

## Schema Design

## Scalability & Data Partitioning

# REST API Design

## Endpoint Design

## Versioning & Documentation

## Security & Rate Limiting

# Additional Considerations

## Scalability & Fault Tolerance:

## Testing & Monitoring:

Briefly outline your approach to testing and monitoring the backend services, including unit tests, integration tests, and observability (logging, metrics, alerts).
