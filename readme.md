# Patient Management System Microservices Architecture

## Overview

A production ready healthcare microservices application to implement and showcase actual backend engineering concepts: distributed services, inter-service communication, event streaming, cloud infrastructure, security and testing.

## What I Built

Core CRUD API (Spring Boot) for patient records using PostgreSQL Request validation using DTO, custom exception handling, and OpenAPI documentation.
Billing Service: Synchronous calls to Patient Service using **gRPC** and Protocol Buffers for efficient and strongly typed calls.

- **Apache Kafka**: Asynchronously consumes patient events, allowing patient events to be processed by the Analytics Service without being coupled to the core transaction flow.
  Provides user authentication using the popular **Spring Security** library, password encryption/decryption, and generation and validation of **JWT** tokens.
- **API Gateway**: This acts as the central entry point, has routing capabilities, JWT validation filters and centralized exception handling for all downstream services.
  All services are dockerized with their own database and configuration, so that they are consistent in local and cloud environments.
- Testing: Integration test suite covering authentication, authorization and patient endpoints in a dedicated test project.
  Infrastructure as Code: Provided VPC, RDS databases, MSK (Kafka), and ECS clusters using AWS CloudFormation, and tested them locally with LocalStack before rolling it out to the cloud.

## How I Did It

I built the system service by service, adding one distributed pattern by one after a standalone Spring Boot API: synchronous gRPC calls for tightly coupled transactions, event-driven decoupling with Kafka and a common gateway layer for authentication, and routing. Early on, infrastructure was codified using CloudFormation, allowing the whole stack the networking, databases, container orchestration, and load balancing to be deployed repeatably and tested in a safe way in AWS LocalStack (before touching real AWS resources).

## Impact

This turns out to be a fully functional, cloud-deployable microservices reference architecture that showcases the full suite of skills required for designing, communicating between services, securing services, testing services for observability, packaging services in containers, and automating infrastructure skills that are applicable to enterprise-scale distributed systems.
