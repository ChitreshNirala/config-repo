# Config Repository for Movie Ticket Booking Platform

This repository contains centralized configuration files for all microservices in the Movie Ticket Booking Platform.

## Structure

```
config-repo/
├── discovery-service.properties          # Eureka Server configuration
├── config-service.properties             # Config Server configuration
├── api-gateway.properties                # API Gateway configuration
├── user-management-service.properties    # User service configuration
├── theatre-management-service.properties # Theatre service configuration
├── booking-management-service.properties # Booking service configuration
├── payment-service.properties            # Payment service configuration
├── notification-service.properties       # Notification service configuration
└── README.md                             # This file
```

## Configuration Details

### Database Configuration
- **MySQL Services**: User, Booking, Payment services
  - Host: localhost:3306
  - Username: root
  - Password: Test@12345

- **PostgreSQL Services**: Theatre Management service
  - Host: localhost:5432
  - Username: postgres
  - Password: postgres

### Message Queue
- **Kafka**: localhost:9092 (used by Booking, Payment, Notification services)

### Service Discovery
- **Eureka Server**: localhost:8761

### External Services
- **Stripe API**: Configure your test/live keys in payment-service.properties
- **Email Service**: Configure Gmail credentials in notification-service.properties

## Environment-Specific Configurations

For different environments, create additional files:

- `{service-name}-dev.properties` - Development environment
- `{service-name}-prod.properties` - Production environment
- `{service-name}-test.properties` - Testing environment

## Security Notes

⚠️ **Important**: Never commit sensitive information like:
- Real database passwords
- Production API keys
- Private keys
- Personal email credentials

Use environment variables or Spring Cloud Config Server encryption for sensitive data in production.

## Usage

The Config Server will automatically load these configurations when services start up. Each service will receive its configuration based on its `spring.application.name` property.

## Updating Configuration

1. Make changes to the appropriate `.properties` file
2. Commit and push to this repository
3. Restart the affected microservice(s) or use Spring Boot Actuator refresh endpoint

## Production Deployment

For production:
1. Use encrypted values for sensitive data
2. Configure production database URLs and credentials
3. Set up proper Eureka server URLs
4. Configure production Kafka cluster
5. Set up production email service

---

**Repository**: https://github.com/ChitreshNirala/config-repo
**Platform**: Movie Ticket Booking Platform
**Version**: 1.0.0
