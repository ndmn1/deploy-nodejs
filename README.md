# Deploy Node.js API

A simple, production-ready Node.js REST API built with Express.js for deployment purposes.

## Features

- ✅ RESTful API endpoints
- ✅ Health check endpoint for monitoring
- ✅ Security middleware (Helmet)
- ✅ CORS enabled
- ✅ Request logging
- ✅ Error handling
- ✅ JSON validation
- ✅ Clean, modular code

## Quick Start

### Install Dependencies

```bash
npm install
```

### Development

```bash
npm run dev
```

### Production

```bash
npm start
```

## API Endpoints

### Health Check

- `GET /health` - Server health and metrics

### Users API

- `GET /api/users` - Get all users
- `GET /api/users/:id` - Get user by ID
- `POST /api/users` - Create new user
- `PUT /api/users/:id` - Update user
- `DELETE /api/users/:id` - Delete user

## Example Usage

### Create a user

```bash
curl -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name": "John Doe", "email": "john@example.com"}'
```

### Get all users

```bash
curl http://localhost:3000/api/users
```

### Health check

```bash
curl http://localhost:3000/health
```

## Deployment

### Environment Variables

- `PORT` - Server port (default: 3000)

### Docker Deployment

```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install --omit=dev
COPY . .
EXPOSE 3000
CMD ["npm", "start"]
```

### PM2 Deployment

```bash
npm install -g pm2
pm2 start server.js --name "deploy-api"
pm2 startup
pm2 save
```

### Heroku Deployment

```bash
heroku create your-app-name
git push heroku main
```

## Production Considerations

- Replace in-memory storage with a database (PostgreSQL, MongoDB, etc.)
- Add authentication/authorization
- Implement rate limiting
- Add input validation with Joi or similar
- Set up monitoring and logging
- Use environment variables for configuration
- Add unit and integration tests

## License

ISC
