# WhatsWay

**WhatsWay** is a WhatsApp Business communication and engagement platform designed to help businesses manage customer conversations, contacts, campaigns, chatbot automation, and team workflows from one dashboard.

It combines a shared inbox, CRM capabilities, bulk messaging, template management, automation, AI-assisted features, and reporting in a full-stack web application.

## Features

- **Shared Inbox:** Manage customer conversations, assign chats to agents, and track message delivery and read statuses.
- **Contact Management:** Organize contacts, groups, tags, and customer information.
- **Campaign Management:** Create and monitor WhatsApp messaging campaigns using contacts, CSV data, or API-based workflows.
- **Message Templates:** Manage template content, languages, variables, buttons, and supported media.
- **Chatbot Automation:** Configure automated responses and visual conversation flows.
- **AI Assistant:** Access AI-related functionality and settings.
- **Multi-Channel Support:** Configure multiple WhatsApp Business channels.
- **CRM and Lead Management:** Organize customer interactions and lead information.
- **Analytics and Reports:** Review campaign performance, messaging activity, and reports.
- **Team Management:** Manage users, roles, permissions, and conversation assignments.
- **Integrations:** Support for WhatsApp Business Platform, cloud storage, email, AI, and payment services.

Feature availability depends on configuration, integrations, and deployment status.

## Technology Stack

| Component | Technologies |
|---|---|
| Frontend | React, TypeScript, Vite |
| UI | Tailwind CSS, Radix UI, Lucide React |
| Backend | Node.js, Express |
| Real-time communication | Socket.IO |
| Database | PostgreSQL |
| ORM and schema management | Drizzle ORM, Drizzle Kit |
| Validation | Zod, Drizzle Zod |
| File storage integrations | AWS S3, Google Cloud Storage |
| Messaging | WhatsApp Business Platform / Cloud API |
| AI integration | OpenAI API |
| Payments | Razorpay, Stripe |
| Build tools | TypeScript, esbuild |

## Project Structure

```text
whatsway/
├── client/              # React frontend
│   └── src/
│       └── pages/       # Application pages
├── server/              # Express backend
│   ├── config/          # Configuration
│   ├── controllers/     # Request handlers
│   ├── cron/            # Scheduled tasks
│   ├── middlewares/     # Server middleware
│   ├── repositories/    # Data access
│   ├── routes/          # API routes
│   ├── services/        # Business logic and integrations
│   ├── db.ts            # Database connection
│   └── index.ts         # Server entry point
├── shared/
│   └── schema.ts        # Shared database schemas
├── migrations/          # Database migrations
├── prisma/              # Prisma-related resources
├── .env.example         # Environment configuration template
├── drizzle.config.js    # Drizzle configuration
└── package.json
```

## Prerequisites

- Node.js
- npm
- PostgreSQL
- WhatsApp Business Platform credentials for messaging functionality
- Optional API credentials for integrations you intend to use

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/pradeep8577/whatsway.git
cd whatsway
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Copy the example environment file:

```bash
cp .env.example .env
```

Configure the values in `.env` for your environment.

| Variable | Purpose |
|---|---|
| `DATABASE_URL` | PostgreSQL connection |
| `SESSION_SECRET` | Session security |
| `PORT` | Application server port |
| `APP_URL` | Public application URL |
| `WHATSAPP_API_VERSION` | WhatsApp API version |
| `WHATSAPP_BUSINESS_ACCOUNT_ID` | Business Account ID |
| `WHATSAPP_ACCESS_TOKEN` | WhatsApp API access token |
| `WHATSAPP_PHONE_NUMBER_ID` | WhatsApp phone number ID |
| `WHATSAPP_WEBHOOK_VERIFY_TOKEN` | Webhook verification |
| `OPENAI_API_KEY` | Optional AI integration |
| `SMTP_HOST`, `SMTP_PORT`, `SMTP_USER`, `SMTP_PASS` | Optional email configuration |
| `REDIS_URL` | Optional Redis configuration |
| `RAZORPAY_KEY_ID`, `RAZORPAY_KEY_SECRET` | Optional Razorpay integration |
| `STRIPE_SECRET_KEY`, `STRIPE_PUBLISHABLE_KEY` | Optional Stripe integration |

**Security:** Never commit real API keys, access tokens, database credentials, or session secrets to Git.

### 4. Set up PostgreSQL

Create a PostgreSQL database and configure `DATABASE_URL`.

Review the schema and migration files before applying changes. For development environments, the repository provides these commands:

```bash
npm run db:generate
npm run db:push
```

Alternatively:

```bash
npm run db:update
```

Take a backup before making schema changes to an existing production database.

### 5. Start the development server

```bash
npm run dev
```

The example configuration uses port `5000`. Open the configured local URL in your browser.

### 6. Build and run in production

```bash
npm run build
npm start
```

Configure production environment variables, HTTPS, database access, and webhook URLs before deployment.

## Available Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start development server |
| `npm run build` | Build frontend and bundle backend |
| `npm start` | Start production server |
| `npm run check` | Run TypeScript checks |
| `npm run db:generate` | Generate database migrations |
| `npm run db:push` | Apply schema changes |
| `npm run db:update` | Generate and apply schema changes |
| `npm run seed` | Run database seed script |
| `npm run db:studio` | Open Drizzle Studio |
| `npm run studio` | Open Prisma Studio on port 4444 |

## WhatsApp Business API Setup

1. Create or configure a Meta developer app.
2. Set up the WhatsApp Business Platform account and phone number.
3. Obtain the required API credentials.
4. Configure the WhatsApp environment variables.
5. Set up a publicly accessible HTTPS webhook endpoint.
6. Configure webhook verification and subscribe to the required events.
7. Configure approved message templates as needed.
8. Test inbound messages, outbound messages, and delivery-status updates before production use.

Message delivery and template approval are subject to Meta's platform requirements and account configuration.

## Deployment

The repository includes production build scripts and a PM2 ecosystem configuration.

Recommended deployment considerations:

- Use a supported Node.js runtime.
- Configure PostgreSQL backups and restricted database access.
- Serve the application over HTTPS.
- Store credentials securely.
- Configure WhatsApp webhook endpoints.
- Ensure Socket.IO WebSocket connections work through the reverse proxy.
- Monitor application logs and errors.
- Test database migrations and recovery procedures.

## Security Recommendations

- Store credentials in environment variables or a secrets manager.
- Restrict CORS to trusted origins in production.
- Validate incoming requests and webhook payloads.
- Enforce authentication and role-based authorization.
- Apply rate limits and monitor suspicious activity.
- Follow WhatsApp consent, opt-in, template, and messaging policies.
- Maintain appropriate opt-out and suppression handling.
- Keep dependencies updated and review security advisories.

## Troubleshooting

**Database connection errors**
- Verify `DATABASE_URL` and database connectivity.
- Check whether the required schema has been applied.

**WhatsApp messaging errors**
- Check the access token, phone number ID, API version, permissions, and template status.

**Webhook verification failures**
- Verify the webhook URL and verification token.

**Real-time updates not working**
- Check Socket.IO connectivity and WebSocket support in your proxy configuration.

**Build or type errors**
- Run `npm run check` and `npm run build` and review the reported errors.

## Contributing

1. Fork the repository.
2. Create a feature branch.
3. Make your changes and test them.
4. Run `npm run check` and `npm run build`.
5. Submit a pull request describing the changes.

## License

The project declares the MIT license in `package.json`. Ensure the repository includes a matching `LICENSE` file with the applicable terms.

## Author

**Pradeep Pawar**

- GitHub: https://github.com/pradeep8577
- LinkedIn: https://www.linkedin.com/in/pradeep-pawar-6541541aa/
