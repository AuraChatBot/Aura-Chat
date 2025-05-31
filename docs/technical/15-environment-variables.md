# Environment Variables Configuration

This document outlines the environment variables configuration for the Pheme Protocol. Each component of the system requires specific environment variables for proper functionality.

## Overview

The Pheme Protocol uses a multi-layered environment configuration approach:
- Frontend (Next.js application)
- Backend (API services)
- Smart Contracts (Ethereum and other chains)
- AI Workers (Validation network)
- Infrastructure (CI/CD and deployment)

## Component-Specific Variables

### Frontend Variables (`frontend/.env`)

```env
# Web3 Configuration
NEXT_PUBLIC_WALLETCONNECT_PROJECT_ID=your_project_id
NEXT_PUBLIC_DEFAULT_CHAIN=1 # Ethereum Mainnet

# API Configuration
NEXT_PUBLIC_API_URL=http://localhost:3001
NEXT_PUBLIC_WEBSOCKET_URL=ws://localhost:3001

# Pheme Protocol Settings
NEXT_PUBLIC_PHEME_CONTRACT_ADDRESS=your_contract_address
NEXT_PUBLIC_MIN_STAKE_AMOUNT=1000000000000000000 # 1 PHEME in wei
NEXT_PUBLIC_DEFAULT_GAS_LIMIT=300000

# Analytics & Monitoring (Optional)
NEXT_PUBLIC_ANALYTICS_ID=your_analytics_id
```

### Backend Variables (`backend/.env`)

```env
# Server Configuration
PORT=3001
NODE_ENV=development
API_VERSION=v1

# Database Configuration
DATABASE_URL=postgresql://user:password@localhost:5432/pheme_db
REDIS_URL=redis://localhost:6379

# Authentication
JWT_SECRET=your_jwt_secret
JWT_EXPIRY=24h
ADMIN_API_KEY=your_admin_api_key

# Blockchain Integration
PROVIDER_URL=your_provider_url
CONTRACT_ADDRESS=your_contract_address
VALIDATOR_PRIVATE_KEY=your_validator_private_key

# Rate Limiting & Security
RATE_LIMIT_WINDOW=15m
RATE_LIMIT_MAX_REQUESTS=100
CORS_ORIGINS=http://localhost:3000
```

### Smart Contracts Variables (`contracts/.env`)

```env
# Network Configuration
HARDHAT_NETWORK=hardhat
RPC_URL=your_rpc_endpoint
PRIVATE_KEY=your_deployment_wallet_private_key

# Contract Verification
ETHERSCAN_API_KEY=your_etherscan_api_key
POLYGONSCAN_API_KEY=your_polygonscan_api_key
OPTIMISM_API_KEY=your_optimism_api_key

# Deployment Settings
INITIAL_SUPPLY=1000000000000000000000000 # 1M PHEME
TREASURY_ADDRESS=your_treasury_address
VALIDATOR_THRESHOLD=5
```

### AI Worker Variables (`workers/.env`)

```env
# Worker Configuration
WORKER_ID=worker_1
MODEL_ENDPOINT=your_model_endpoint
MODEL_API_KEY=your_api_key

# Network Settings
VALIDATOR_NODE_URL=http://localhost:3001
WEBSOCKET_ENDPOINT=ws://localhost:3001/worker
```

## CI/CD Environment Variables

These variables should be added as GitHub Actions secrets:

### Build & Test
```env
NODE_VERSION=18
HARDHAT_NETWORK=hardhat
TEST_PRIVATE_KEY=test_private_key
TEST_RPC_URL=test_rpc_url
```

### Deployment Infrastructure
```env
# AWS Configuration
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=your_aws_region

# Docker Registry
DOCKER_USERNAME=your_docker_username
DOCKER_PASSWORD=your_docker_password

# Production Database
PROD_DATABASE_URL=your_production_database_url
```

## Environment Setup Guide

### Local Development Setup

1. Create environment files:
   ```bash
   cp frontend/.env.example frontend/.env
   cp backend/.env.example backend/.env
   cp contracts/.env.example contracts/.env
   cp workers/.env.example workers/.env
   ```

2. Configure local variables:
   - Use development endpoints and local databases
   - Set up test wallets and contracts
   - Configure minimal validator settings

### Production Setup

1. Infrastructure Requirements:
   - Secure key management service (AWS KMS, HashiCorp Vault)
   - Production-grade databases with backups
   - Load balancers and CDN configuration

2. Security Considerations:
   - Use different values for all environments
   - Rotate secrets regularly
   - Implement proper access controls
   - Monitor environment variable usage

3. Deployment Process:
   - Use CI/CD secrets management
   - Implement automated environment validation
   - Maintain separate configurations per environment

## Best Practices

1. **Security**:
   - Never commit sensitive values
   - Use strong, unique values
   - Implement secret rotation
   - Monitor for exposed secrets

2. **Organization**:
   - Group related variables
   - Use clear, descriptive names
   - Document all variables
   - Maintain example files

3. **Validation**:
   - Validate environment on startup
   - Implement type checking
   - Provide clear error messages
   - Test with different configurations

## Troubleshooting

Common issues and solutions:

1. **Missing Variables**:
   - Check `.env.example` files
   - Verify all required variables
   - Confirm naming matches exactly

2. **Invalid Values**:
   - Validate format and encoding
   - Check for trailing spaces
   - Verify environment-specific values

3. **Security Issues**:
   - Audit for exposed secrets
   - Review access permissions
   - Check for weak values

## Related Documentation

- [Development Setup](./20-developer-setup.md)
- [Deployment Guide](./40-deployment.md)
- [Security Guidelines](./05-security.md)
- [CI/CD Pipeline](./07-ci-cd.md) 