# Environment Variables Documentation

This document outlines all environment variables required for the Pheme Protocol project, organized by component and deployment environment.

## Frontend Environment Variables (`frontend/.env`)

```env
# Required for Web3 Integration
NEXT_PUBLIC_WALLET_CONNECT_PROJECT_ID=your_wallet_connect_project_id
NEXT_PUBLIC_API_URL=http://localhost:3001 # Backend API URL (use appropriate URL for each environment)

# Optional Analytics & Monitoring
NEXT_PUBLIC_ANALYTICS_ID=your_analytics_id # If using analytics service
```

## Backend Environment Variables (`backend/.env`)

```env
# Database Configuration
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# API Configuration
PORT=3001
NODE_ENV=development # or production

# JWT Authentication
JWT_SECRET=your_jwt_secret
JWT_EXPIRY=24h

# Rate Limiting
RATE_LIMIT_WINDOW=15m
RATE_LIMIT_MAX_REQUESTS=100
```

## Smart Contracts Environment Variables (`contracts/.env`)

```env
# Network Configuration
HARDHAT_NETWORK=hardhat # or mainnet, testnet, etc.
RPC_URL=your_rpc_endpoint
PRIVATE_KEY=your_deployment_wallet_private_key

# Contract Verification
ETHERSCAN_API_KEY=your_etherscan_api_key
```

## CI/CD Environment Variables (GitHub Actions Secrets)

These variables need to be added to your GitHub repository's secrets:

### Build & Test
```env
NODE_VERSION=18 # Set in workflow file
HARDHAT_NETWORK=hardhat # Set in workflow file
```

### Smart Contract Deployment & Testing
```env
PRIVATE_KEY=your_deployment_wallet_private_key
RPC_URL=your_rpc_endpoint
ETHERSCAN_API_KEY=your_etherscan_api_key
```

### Infrastructure & Deployment
```env
# AWS Configuration
AWS_ACCESS_KEY_ID=your_aws_access_key
AWS_SECRET_ACCESS_KEY=your_aws_secret_key
AWS_REGION=your_aws_region

# Docker Registry
DOCKER_USERNAME=your_docker_username
DOCKER_PASSWORD=your_docker_password

# Database (Production)
PROD_DATABASE_URL=your_production_database_url
```

## Environment Setup Instructions

1. **Local Development**:
   - Copy the appropriate `.env.example` file in each directory to `.env`
   - Fill in the values according to your local setup
   - Never commit `.env` files to the repository

2. **CI/CD Setup**:
   - Add all CI/CD variables as GitHub Actions secrets
   - Navigate to Repository Settings → Secrets and Variables → Actions
   - Click "New repository secret" for each variable

3. **Production Deployment**:
   - Ensure all production variables are properly set in your deployment platform
   - Use secure secret management services when possible
   - Regularly rotate sensitive credentials

## Security Notes

- Never commit sensitive values to the repository
- Use strong, unique values for secrets
- Regularly rotate production credentials
- Use environment-specific values for different deployments
- Consider using a secrets management service for production

## Troubleshooting

If you encounter environment-related issues:

1. Verify all required variables are set
2. Check for proper formatting of values
3. Ensure environment files are in the correct locations
4. Confirm variable names match exactly as specified
5. Check for any conflicting values between environments 