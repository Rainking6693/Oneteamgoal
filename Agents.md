\# Repository Guidelines



\# One Team Goal - Youth Sports Fundraising Platform



\## Project Structure \& Module Organization



One Team Goal follows a standard Next.js 14 structure with TypeScript. Source code is organized in `/pages` for Next.js pages and API routes, `/components` for React components grouped by feature (team-shops, donations, gear-design, coach-dashboard, etc.), `/lib` for utilities, Stripe integration, team management, and type definitions, and `/public` for static assets. The `/integrations` directory contains Stripe payment processing, Printful merchandise fulfillment, and email automation services.



\## Build, Test, and Development Commands



```bash

\# Start development server

npm run dev



\# Build for production

npm run build



\# Type checking

npm run type-check



\# Code quality checks

npm run lint



\# Comprehensive testing

npm run test:comprehensive



\# E2E testing

npm run test:e2e



\# Payment integration tests

npm run test:stripe-integration



\# Database tests

npm run test:db

```



\## Coding Style \& Naming Conventions



\- \*\*Indentation\*\*: 2 spaces (TypeScript/JavaScript)

\- \*\*File naming\*\*: kebab-case for components, camelCase for utilities

\- \*\*Function/variable naming\*\*: camelCase with descriptive names

\- \*\*Linting\*\*: ESLint with Next.js configuration, TypeScript strict mode enabled



\## Testing Guidelines



\- \*\*Framework\*\*: Jest for unit tests, Playwright for E2E testing

\- \*\*Test files\*\*: Located in `/tests` directory with feature-specific subdirectories

\- \*\*Running tests\*\*: Use `npm run test:comprehensive` for full test suite

\- \*\*Coverage\*\*: Comprehensive test coverage for payment flows, team shop creation, and merchandise fulfillment



\## Commit \& Pull Request Guidelines



\- \*\*Commit format\*\*: Descriptive messages focusing on feature/fix areas (e.g., "team-shops", "donations", "gear-design")

\- \*\*PR process\*\*: Team-based development with code review requirements

\- \*\*Branch naming\*\*: Feature branches with descriptive names



---



\# Repository Tour



\## 🎯 What This Repository Does



One Team Goal is a hassle-free fundraising platform specifically designed for youth sports teams. The platform enables coaches and team administrators to create custom team merchandise stores and accept donations without any upfront costs, inventory management, or shipping logistics. Teams can raise thousands of dollars in weeks through branded gear sales and direct donations via QR codes and shareable links.



\*\*Key responsibilities:\*\*

\- Custom team merchandise store creation with professional designs

\- Direct donation collection with QR codes and shareable links

\- Print-on-demand fulfillment with no inventory or shipping hassles

\- Coach dashboard for fundraising tracking and goal management

\- Automated payout system with fast bank transfers (1-2 days)



---



\## 🗃️ Architecture Overview



\### System Context

```

\[Team Registration] → \[One Team Goal Platform] → \[Custom Team Store]

&nbsp;      ↓                        ↓                        ↓

\[Merchandise Orders] → \[Print-on-Demand Fulfillment] → \[Direct Shipping]

&nbsp;      ↓                        ↓                        ↓

\[Donations \& Sales] → \[Payment Processing] → \[Coach Payouts]

```



\### Key Components

\- \*\*Team Store Builder\*\* - Custom merchandise store creation with team logos and branding

\- \*\*Print-on-Demand Integration\*\* - Printful API for merchandise production and fulfillment

\- \*\*Payment Processing\*\* - Stripe integration for donations, merchandise sales, and coach payouts

\- \*\*QR Code Generation\*\* - Dynamic QR codes for easy donation and store access

\- \*\*Coach Dashboard\*\* - Fundraising tracking, goal setting, and payout management

\- \*\*Team Member Tracking\*\* - Individual player fundraising progress and leaderboards

\- \*\*Email Automation\*\* - Order confirmations, shipping notifications, and fundraising updates

\- \*\*Mobile-Responsive Design\*\* - Optimized for parents and supporters on mobile devices



\### Data Flow

1\. Coach registers team and uploads logo for custom merchandise design

2\. Platform creates branded team store with hoodies, shirts, hats, and accessories

3\. QR codes and shareable links generated for easy access and promotion

4\. Supporters purchase merchandise or make direct donations

5\. Orders automatically fulfilled through print-on-demand service

6\. Funds tracked in real-time with automated payouts to coach bank account

7\. Email notifications sent for orders, shipping, and fundraising milestones



---



\## 📁 Project Structure \[Complete Directory Tree]



```

OneTeamGoal/

├── pages/                          # Next.js pages and API routes

│   ├── api/                        # Backend API endpoints

│   │   ├── teams/                  # Team management endpoints

│   │   │   ├── create.ts           # Team registration

│   │   │   ├── store.ts            # Team store generation

│   │   │   └── members.ts          # Team member management

│   │   ├── donations/              # Donation processing

│   │   │   ├── process.ts          # Donation payment handling

│   │   │   ├── qr-generate.ts      # QR code generation

│   │   │   └── tracking.ts         # Donation tracking

│   │   ├── merchandise/            # Product management

│   │   │   ├── catalog.ts          # Available products

│   │   │   ├── customize.ts        # Design customization

│   │   │   └── fulfill.ts          # Order fulfillment

│   │   ├── stripe/                 # Payment processing

│   │   │   ├── checkout.ts         # Payment sessions

│   │   │   ├── webhook.ts          # Payment webhooks

│   │   │   └── payouts.ts          # Coach payouts

│   │   ├── printful/               # Print-on-demand integration

│   │   │   ├── products.ts         # Product sync

│   │   │   ├── orders.ts           # Order processing

│   │   │   └── shipping.ts         # Tracking updates

│   │   ├── health.ts               # System health monitoring

│   │   └── cron/                   # Scheduled jobs

│   │       ├── payout-reminders.ts # Automated payouts

│   │       └── order-updates.ts    # Shipping notifications

│   ├── coach/                      # Coach dashboard

│   │   ├── index.tsx               # Main dashboard

│   │   ├── team-setup.tsx          # Team store creation

│   │   ├── fundraising.tsx         # Goal tracking

│   │   ├── payouts.tsx             # Payout management

│   │   └── settings.tsx            # Account settings

│   ├── team/                       # Team store pages

│   │   ├── \[teamId]/               # Dynamic team routes

│   │   │   ├── store.tsx           # Team merchandise store

│   │   │   ├── donate.tsx          # Donation page

│   │   │   └── progress.tsx        # Fundraising progress

│   │   └── join.tsx                # Team member registration

│   ├── auth/                       # Authentication pages

│   │   ├── coach-login.tsx         # Coach authentication

│   │   ├── signup.tsx              # Coach registration

│   │   └── callback.tsx            # OAuth callbacks

│   ├── onboarding.tsx              # New coach setup

│   ├── demo.tsx                    # Platform demo

│   ├── index.tsx                   # Marketing homepage

│   └── \_app.tsx                    # App configuration

├── components/                     # React components by feature

│   ├── team-shops/                 # Team store components

│   │   ├── StoreBuilder.tsx        # Store creation interface

│   │   ├── ProductGrid.tsx         # Merchandise display

│   │   ├── CustomDesigner.tsx      # Logo and design tools

│   │   └── StorePreview.tsx        # Store preview interface

│   ├── donations/                  # Donation components

│   │   ├── DonationForm.tsx        # Donation input form

│   │   ├── QRCodeDisplay.tsx       # QR code generation

│   │   ├── ShareButtons.tsx        # Social sharing

│   │   └── DonationTracker.tsx     # Progress tracking

│   ├── gear-design/                # Merchandise design

│   │   ├── LogoUploader.tsx        # Team logo upload

│   │   ├── DesignPreview.tsx       # Design preview

│   │   ├── ColorSelector.tsx       # Color customization

│   │   └── ProductVariants.tsx     # Size and style options

│   ├── coach-dashboard/            # Coach interface components

│   │   ├── FundraisingOverview.tsx # Key metrics display

│   │   ├── GoalSetting.tsx         # Fundraising goal management

│   │   ├── TeamMemberList.tsx      # Player management

│   │   └── PayoutHistory.tsx       # Payment history

│   ├── payment/                    # Payment processing

│   │   ├── CheckoutForm.tsx        # Stripe checkout

│   │   ├── PaymentStatus.tsx       # Transaction status

│   │   ├── PayoutSetup.tsx         # Bank account setup

│   │   └── TransactionHistory.tsx  # Payment tracking

│   ├── mobile/                     # Mobile-optimized components

│   │   ├── MobileStore.tsx         # Mobile team store

│   │   ├── MobileDonate.tsx        # Mobile donation flow

│   │   ├── QRScanner.tsx           # QR code scanning

│   │   └── MobileNav.tsx           # Mobile navigation

│   ├── email/                      # Email components

│   │   ├── OrderConfirmation.tsx   # Order email templates

│   │   ├── ShippingNotification.tsx # Shipping updates

│   │   ├── FundraisingUpdate.tsx   # Progress notifications

│   │   └── PayoutNotification.tsx  # Payout confirmations

│   └── ui/                         # Reusable UI components

│       ├── Button.tsx              # Button variants

│       ├── Modal.tsx               # Modal dialogs

│       ├── Card.tsx                # Content cards

│       ├── QRCode.tsx              # QR code component

│       └── Loading.tsx             # Loading states

├── lib/                           # Core utilities and services

│   ├── payment/                   # Payment processing

│   │   ├── stripe-client.ts       # Stripe API wrapper

│   │   ├── donation-processing.ts # Donation handling

│   │   ├── payout-management.ts   # Coach payouts

│   │   └── subscription-billing.ts # Future subscription features

│   ├── fulfillment/               # Merchandise fulfillment

│   │   ├── printful-client.ts     # Printful API integration

│   │   ├── order-processing.ts    # Order management

│   │   ├── shipping-tracking.ts   # Tracking updates

│   │   └── product-catalog.ts     # Available products

│   ├── teams/                     # Team management

│   │   ├── team-creation.ts       # Team registration

│   │   ├── store-generation.ts    # Store creation logic

│   │   ├── member-management.ts   # Player tracking

│   │   └── fundraising-goals.ts   # Goal setting and tracking

│   ├── design/                    # Design tools

│   │   ├── logo-processing.ts     # Logo upload and processing

│   │   ├── design-templates.ts    # Pre-made designs

│   │   ├── color-schemes.ts       # Color customization

│   │   └── mockup-generation.ts   # Product mockups

│   ├── database/                  # Database operations

│   │   ├── supabase-client.ts     # Supabase configuration

│   │   ├── teams.ts               # Team data layer

│   │   ├── donations.ts           # Donation records

│   │   ├── orders.ts              # Order management

│   │   └── payouts.ts             # Payout tracking

│   ├── auth/                      # Authentication utilities

│   │   ├── supabase-auth.ts       # Supabase auth config

│   │   ├── coach-authentication.ts # Coach login system

│   │   └── session-management.ts  # Session handling

│   ├── types/                     # TypeScript definitions

│   │   ├── team.types.ts          # Team data types

│   │   ├── payment.types.ts       # Payment types

│   │   ├── product.types.ts       # Merchandise types

│   │   ├── donation.types.ts      # Donation types

│   │   └── database.types.ts      # Database schema types

│   ├── utils/                     # Helper functions

│   │   ├── qr-generation.ts       # QR code creation

│   │   ├── image-processing.ts    # Image optimization

│   │   ├── validation.ts          # Input validation

│   │   ├── formatting.ts          # Data formatting

│   │   └── error-handling.ts      # Error management

│   ├── hooks/                     # Custom React hooks

│   │   ├── useTeam.ts             # Team management hooks

│   │   ├── usePayment.ts          # Payment processing

│   │   ├── useFundraising.ts      # Fundraising tracking

│   │   └── useMobile.ts           # Mobile optimization

│   └── constants/                 # Application constants

│       ├── sports-categories.ts   # Available sports

│       ├── product-catalog.ts     # Merchandise options

│       └── app-config.ts          # Global settings

├── integrations/                  # Integration-specific code

│   ├── printful/                  # Print-on-demand integration

│   │   ├── product-sync.ts        # Product catalog sync

│   │   ├── order-fulfillment.ts   # Order processing

│   │   ├── webhook-handlers.ts    # Printful webhooks

│   │   └── shipping-tracker.ts    # Delivery tracking

│   ├── stripe/                    # Payment integration

│   │   ├── payment-processor.ts   # Payment handling

│   │   ├── payout-automation.ts   # Automated payouts

│   │   ├── webhook-validator.ts   # Webhook security

│   │   └── subscription-manager.ts # Future subscription features

│   └── email/                     # Email service integration

│       ├── sendgrid-client.ts     # SendGrid integration

│       ├── template-manager.ts    # Email templates

│       └── automation-rules.ts    # Email automation

├── public/                        # Static assets

│   ├── images/                    # Application images

│   │   ├── logos/                 # Team logos

│   │   ├── products/              # Product images

│   │   ├── mockups/               # Design mockups

│   │   └── marketing/             # Marketing assets

│   ├── qr-codes/                  # Generated QR codes

│   ├── designs/                   # Team design assets

│   └── icons/                     # UI icons

├── styles/                        # Styling

│   ├── globals.css                # Global styles

│   ├── components/                # Component-specific styles

│   └── tailwind.config.js         # Tailwind configuration

├── tests/                         # Test files

│   ├── payment/                   # Payment processing tests

│   ├── teams/                     # Team management tests

│   ├── fulfillment/               # Order fulfillment tests

│   ├── components/                # Component tests

│   ├── api/                       # API endpoint tests

│   └── e2e/                       # End-to-end tests

├── docs/                          # Documentation

│   ├── api/                       # API documentation

│   ├── setup/                     # Setup guides

│   └── coach-guides/              # Coach documentation

├── scripts/                       # Build and deployment scripts

│   ├── build.js                   # Custom build script

│   ├── deploy.js                  # Deployment automation

│   └── seed-db.js                 # Database seeding

├── next.config.js                 # Next.js configuration

├── tailwind.config.js             # Tailwind CSS configuration

├── netlify.toml                   # Netlify deployment config

├── package.json                   # Dependencies and scripts

├── tsconfig.json                  # TypeScript configuration

├── .env.example                   # Environment variable template

├── .eslintrc.json                # ESLint configuration

├── jest.config.js                # Jest testing configuration

└── playwright.config.ts          # Playwright E2E configuration

```



\### Key Files to Know



| File | Purpose | When You'd Touch It |

|------|---------|---------------------|

| `pages/api/teams/create.ts` | Team registration endpoint | Adding new team features |

| `lib/payment/stripe-client.ts` | Stripe payment operations | Payment processing changes |

| `lib/fulfillment/printful-client.ts` | Printful integration | Adding new products |

| `components/team-shops/StoreBuilder.tsx` | Team store creation UI | Improving store setup |

| `lib/database/teams.ts` | Team data operations | Database schema changes |

| `pages/\_app.tsx` | App configuration and providers | Global app changes |

| `lib/types/team.types.ts` | Team data type definitions | Adding new team features |

| `next.config.js` | Next.js build configuration | Build optimization |

| `tailwind.config.js` | Design system configuration | UI/styling changes |

| `netlify.toml` | Deployment and serverless config | Infrastructure changes |



---



\## 🔧 Technology Stack



\### Core Technologies

\- \*\*Language:\*\* TypeScript (5.2+) - Full type safety across frontend and backend

\- \*\*Framework:\*\* Next.js 14 with App Router - Server-side rendering and API routes

\- \*\*Database:\*\* Supabase - PostgreSQL with real-time capabilities for team and order data

\- \*\*Styling:\*\* Tailwind CSS 3.4 - Utility-first CSS with sports-themed design system



\### Key Libraries

\- \*\*stripe\*\* - Payment processing for donations and merchandise sales

\- \*\*@supabase/supabase-js\*\* - Database operations and real-time updates

\- \*\*printful-sdk\*\* - Print-on-demand integration for merchandise fulfillment

\- \*\*qrcode\*\* - QR code generation for easy donation access

\- \*\*framer-motion\*\* - UI animations and micro-interactions

\- \*\*@headlessui/react\*\* - Accessible UI components

\- \*\*react-hook-form\*\* - Form handling with validation



\### Development Tools

\- \*\*Jest\*\* - Unit testing framework with payment flow mocks

\- \*\*Playwright\*\* - End-to-end testing for fundraising workflows

\- \*\*ESLint\*\* - Code quality and Next.js best practices

\- \*\*TypeScript\*\* - Static type checking and IntelliSense



---



\## 🌐 External Dependencies



\### Required Services

\- \*\*Supabase\*\* - Primary database for teams, donations, and orders

\- \*\*Stripe\*\* - Payment processing for donations and merchandise sales

\- \*\*Printful\*\* - Print-on-demand merchandise production and fulfillment

\- \*\*Netlify\*\* - Hosting platform with serverless functions and CDN



\### Optional Integrations

\- \*\*SendGrid\*\* - Email automation for order confirmations and notifications

\- \*\*Sentry\*\* - Error monitoring and performance tracking

\- \*\*Google Analytics\*\* - User behavior tracking and conversion metrics



\### Environment Variables



```bash

\# Required

STRIPE\_SECRET\_KEY=          # Payment processing

STRIPE\_PUBLISHABLE\_KEY=     # Client-side payments

PRINTFUL\_API\_KEY=          # Merchandise fulfillment

SUPABASE\_URL=              # Database connection

SUPABASE\_SERVICE\_KEY=      # Database admin access



\# Optional

SENDGRID\_API\_KEY=         # Email automation

SENTRY\_DSN=               # Error monitoring

GA\_MEASUREMENT\_ID=        # Analytics tracking

```



---



\## 📄 Common Workflows



\### Team Store Creation Workflow

1\. Coach registers and uploads team logo

2\. System generates custom merchandise designs with team branding

3\. Product catalog created with hoodies, shirts, hats, and accessories

4\. QR codes and shareable links generated for easy access

5\. Store goes live for supporters to purchase merchandise

6\. Orders automatically sent to Printful for fulfillment



\*\*Code path:\*\* `pages/coach/team-setup.tsx` → `pages/api/teams/create.ts` → `lib/teams/store-generation.ts` → `lib/fulfillment/printful-client.ts` → `components/team-shops/StorePreview.tsx`



\### Donation Processing Workflow

1\. Supporter scans QR code or visits team donation page

2\. Donation form displays with team information and progress

3\. Stripe processes payment securely

4\. Donation tracked in real-time on coach dashboard

5\. Email confirmation sent to donor

6\. Funds added to team's payout balance



\*\*Code path:\*\* `components/donations/QRCodeDisplay.tsx` → `components/donations/DonationForm.tsx` → `pages/api/donations/process.ts` → `lib/payment/donation-processing.ts` → `components/coach-dashboard/FundraisingOverview.tsx`



\### Merchandise Order Workflow

1\. Supporter visits team store and selects products

2\. Customized merchandise displays with team branding

3\. Stripe checkout processes payment

4\. Order automatically sent to Printful for production

5\. Product manufactured and shipped directly to customer

6\. Tracking information shared with customer and coach



\*\*Code path:\*\* `pages/team/\[teamId]/store.tsx` → `components/team-shops/ProductGrid.tsx` → `pages/api/stripe/checkout.ts` → `pages/api/printful/orders.ts` → `lib/fulfillment/order-processing.ts`



\### Coach Payout Workflow

1\. Coach sets up bank account for payouts

2\. Funds accumulate from donations and merchandise sales

3\. Automated payout system transfers funds weekly

4\. Coach receives notification of payout completion

5\. Dashboard displays payout history and pending balance



\*\*Code path:\*\* `components/payment/PayoutSetup.tsx` → `pages/api/stripe/payouts.ts` → `lib/payment/payout-management.ts` → `components/coach-dashboard/PayoutHistory.tsx`



---



\## 📈 Performance \& Scale



\### Performance Considerations

\- \*\*Image Optimization\*\* - Next.js Image component for fast logo and product loading

\- \*\*Payment Processing\*\* - Efficient Stripe integration with minimal API calls

\- \*\*QR Code Generation\*\* - Cached QR codes with dynamic team parameters

\- \*\*Mobile Optimization\*\* - Mobile-first design for parent and supporter access

\- \*\*Real-time Updates\*\* - Supabase subscriptions for live fundraising progress



\### Monitoring

\- \*\*Health Checks\*\* - `/api/health` monitors database, Stripe, and Printful integrations

\- \*\*Payment Tracking\*\* - Monitor donation processing and payout success rates

\- \*\*Order Fulfillment\*\* - Track Printful order completion and shipping times

\- \*\*User Analytics\*\* - Monitor team store visits and conversion rates

\- \*\*Error Tracking\*\* - Comprehensive error handling with fallback mechanisms



---



\## 🚨 Things to Be Careful About



\### 🔒 Security Considerations

\- \*\*Payment Security\*\* - Stripe PCI compliance for donation and merchandise payments

\- \*\*Team Data Protection\*\* - Secure team logo and member information storage

\- \*\*API Key Management\*\* - All service keys stored in environment variables

\- \*\*Input Validation\*\* - Sanitization for team data and payment information

\- \*\*Webhook Security\*\* - Stripe and Printful webhook signature validation



\### 💳 Payment Processing

\- \*\*Transaction Fees\*\* - Transparent fee structure for coaches and supporters

\- \*\*Payout Timing\*\* - Reliable 1-2 day payout schedule management

\- \*\*Failed Payments\*\* - Graceful handling of declined cards and retries

\- \*\*Refund Processing\*\* - Clear refund policy for merchandise and donations

\- \*\*Tax Compliance\*\* - Proper handling of sales tax where applicable



\### 📦 Merchandise Fulfillment

\- \*\*Printful Integration\*\* - Reliable order processing and status updates

\- \*\*Inventory Management\*\* - Print-on-demand eliminates inventory concerns

\- \*\*Shipping Tracking\*\* - Automated tracking updates to customers

\- \*\*Quality Control\*\* - Monitor product quality and customer satisfaction

\- \*\*Seasonal Demand\*\* - Handle peak fundraising seasons efficiently



\### 📱 Mobile Experience

\- \*\*Mobile Optimization\*\* - Ensure excellent mobile experience for parents

\- \*\*QR Code Scanning\*\* - Reliable QR code scanning and processing

\- \*\*Payment Forms\*\* - Mobile-friendly donation and purchase flows

\- \*\*Store Navigation\*\* - Intuitive mobile store browsing

\- \*\*Loading Performance\*\* - Fast page loads on mobile networks



\*Updated at: 2025-01-15 UTC\*

