# Digital Project Tracking System

A comprehensive multi-partner funded project management system with event sourcing, rules engine, and real-time financial tracking.

## Overview

This system provides a complete solution for managing complex projects funded by multiple partners. It features sophisticated financial controls, audit trails, compliance enforcement, and real-time monitoring capabilities.

### Key Features

- **Multi-Partner Funding**: Track contributions from multiple funding sources with independent budgets and rules
- **Event Sourcing**: Complete audit trail with immutable event history for full transparency
- **Rules Engine**: Flexible, configurable business rules for disbursement validation
- **Double-Entry Ledger**: Accurate financial tracking with built-in reconciliation
- **Real-Time Metrics**: Performance monitoring with risk-based assessment
- **Security & Compliance**: Role-based access control and privileged data views

## System Components

### 1. Event-Sourced Core

Every state change is captured as an immutable event. Events are never deleted or modified, only appended. Current state is derived by replaying the event stream.

**Event Types:**
- `project_created` - New project initialization
- `funding_committed` - Partner commits funds
- `disbursement_requested` - Request for fund release
- `disbursement_approved` - Approval granted
- `disbursement_executed` - Funds transferred
- `milestone_completed` - Project milestone achieved

### 2. Rules Engine

The rules engine validates every transaction against configurable business rules. Rules are defined declaratively and can be updated without code changes.

**Rule Categories:**
- **Validation**: Ensure data integrity (e.g., amounts must be positive)
- **Authorization**: Check permissions (e.g., requires two approvers)
- **Limits**: Enforce constraints (e.g., max 20% per disbursement)
- **Timing**: Time-based rules (e.g., milestone deadlines)

### 3. Double-Entry Ledger

Every financial transaction creates two entries (debit and credit), ensuring the books always balance and providing built-in error detection.

### 4. Multi-Partner Management

Manage multiple funding partners with:
- Different contribution levels
- Independent disbursement rules
- Separate reporting requirements
- Partner-specific validation rules

## Data Models

### Project
Projects are the top-level entity that contains:
- Budget and funding information
- Partner commitments and disbursements
- Milestones and timeline
- Status tracking

### Disbursement
Disbursements track fund releases with:
- Amount, currency, and category
- Approval workflow
- Supporting documentation
- Validation results

### Event
Events capture all state changes with:
- Event type and timestamp
- User and metadata
- Complete payload
- Sequence numbering

### Ledger Entry
Ledger entries provide financial tracking with:
- Debit/credit classification
- Balance snapshots
- Transaction references
- Account categorization

## Interactive Playground

The system includes an interactive disbursement validation playground where you can:
- Test different funding scenarios
- See rule evaluation in real-time
- Understand validation logic
- Experiment with edge cases

Access the playground through the web interface under the "Playground" tab.

## Architecture Highlights

### Event Sourcing Benefits
- **Complete Audit Trail**: Every change is permanently recorded
- **Point-in-Time Reconstruction**: Rebuild any state at any moment
- **Debugging**: Trace exactly what happened and when
- **Compliance**: Meet strict audit requirements

### Rules Engine Benefits
- **Flexibility**: Update rules without code changes
- **Transparency**: Rules are explicit and auditable
- **Consistency**: Same rules applied uniformly
- **Extensibility**: Add new rules easily

### Double-Entry Ledger Benefits
- **Accuracy**: Built-in error detection
- **Reconciliation**: Books always balance
- **Standard**: Industry-standard accounting practice
- **Trust**: Provides financial confidence

## Database Schema

The system uses PostgreSQL with the following main tables:

- **events**: Immutable event store
- **projects**: Project metadata and budgets
- **funding_partners**: Partner commitments and rules
- **disbursements**: Disbursement requests and approvals
- **ledger_entries**: Double-entry financial records
- **rules**: Configurable business rules

All tables use UUIDs for primary keys and include timestamp tracking.

## Security & Compliance

### Access Control
- Role-based permissions
- Privileged data views
- Audit logging for all actions
- Separation of concerns

### Financial Controls
- Multi-level approval workflows
- Budget enforcement
- Over-commitment prevention
- Real-time balance tracking

### Audit & Reporting
- Complete transaction history
- Point-in-time state reconstruction
- Partner-specific reporting
- Compliance documentation

## Use Cases

This system is ideal for:

1. **Government Programs**: Multi-agency funded initiatives with strict compliance requirements
2. **Nonprofit Projects**: Grant-funded projects with multiple funders and reporting needs
3. **Public-Private Partnerships**: Complex funding structures with different partner rules
4. **Research Initiatives**: Academic projects with diverse funding sources
5. **Infrastructure Projects**: Large capital projects with phased funding releases

## Getting Started

### View the Application

Simply open `index.html` in any modern web browser. No server or build process required—it's a fully self-contained static application.

### Explore the Documentation

The web interface includes six main sections:

1. **Overview**: System introduction and key features
2. **Architecture**: Technical design and patterns
3. **Data Schemas**: JSON schemas for all entities
4. **Rules Engine**: Rule definitions and examples
5. **Database**: PostgreSQL DDL and table structures
6. **Playground**: Interactive disbursement validator

### Publishing to GitHub Pages

See `PUBLISHING.md` for step-by-step instructions on creating a GitHub repository and publishing this system as a live website.

## Customization

### Adding New Rules

Rules are defined in JSON format. To add a new rule:

1. Define the rule structure with conditions and actions
2. Set priority (1-100, higher = evaluated first)
3. Specify which partners the rule applies to
4. Add clear validation messages

### Extending the Data Model

The schemas are designed to be extended. Common extensions include:

- Additional milestone types
- Custom disbursement categories
- Partner-specific metadata
- Regional compliance fields

### Database Setup

The PostgreSQL DDL provided in the Database tab can be used to:

1. Create the database schema
2. Set up indexes for performance
3. Add constraints for data integrity
4. Initialize with sample data

## Technical Stack

- **Frontend**: Pure HTML/CSS/JavaScript (no framework required)
- **Data Format**: JSON for all data structures
- **Database**: PostgreSQL with JSONB support
- **Architecture**: Event sourcing + CQRS patterns
- **Hosting**: Static site (GitHub Pages compatible)

## Best Practices

1. **Never modify events**: Events are immutable—always append new events
2. **Validate at the edge**: Run rules before accepting transactions
3. **Balance regularly**: Reconcile ledger entries frequently
4. **Audit everything**: Log all state changes with context
5. **Version rules**: Track rule changes over time

## Support & Documentation

All documentation is embedded in the web application. Additional resources:

- **JSON Schemas**: Complete data structure definitions
- **Rule Examples**: Pre-configured validation rules
- **SQL DDL**: Production-ready database schema
- **Interactive Playground**: Test scenarios in real-time

## License

This is a demonstration system designed to showcase best practices for multi-partner project tracking. Adapt and extend it for your specific needs.

## Contributing

This is a single-file application designed for easy forking and customization. Feel free to:

- Add new features
- Enhance the UI
- Extend the data model
- Share improvements

---

**Built with modern web standards • No build process required • Deploy anywhere**