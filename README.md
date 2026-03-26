<div align="center">

![BioLIMS Logo](https://raw.githubusercontent.com/biolims/BioLIMS-SKILL/main/assets/logo.png)

# BioLIMS-SKILL

**Biopharmaceutical Intelligent Laboratory Information Management System - AI Skills**

[![Skills](https://img.shields.io/badge/Skills-15+-blue.svg)](#skills-catalog)
[![API Coverage](https://img.shields.io/badge/APIs-83-green.svg)](#api-coverage)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

*Empowering laboratory workflows with conversational AI for order management, sample tracking, and experiment orchestration*

[Quick Start](#-quick-start) • [Skills Catalog](#-skills-catalog) • [Documentation](#-documentation) • [API Reference](#-api-reference)

</div>

---

## 🎯 At a Glance

BioLIMS-SKILL provides AI-powered conversational interfaces for Bio-LIMS laboratory management system, enabling natural language interactions with complex laboratory workflows.

| Module | Skills | Focus Areas |
|--------|--------|-------------|
| 🧪 **Order Management** | 8 | Order creation, query, update, sample tracking, fee management |
| 📦 **Sample Receiving** | 12 | Barcode scanning, batch receiving, plate management, quality control |
| 🔬 **Experiment Center** | 15 | Experiment templates, workflow execution, sample pool, result management |
| 📊 **Quality Control** | 6 | QC references, result submission, quality records |

**Total**: 41 integrated skills across 4 core laboratory modules

---

## ⚡ Quick Start

### Installation

```bash
# Clone the repository
git clone https://github.com/biolims/BioLIMS-SKILL.git
cd BioLIMS-SKILL

# Configure authentication
cp .biolims-auth.json.example .biolims-auth.json
# Edit .biolims-auth.json with your credentials
```

### 3-Second Usage

```bash
# Query order details
node scripts/biolims.mjs order ORDER202401180001

# Create sample receive order
node scripts/biolims.mjs create-receive @templates/receive-template.json

# Query experiment templates
node scripts/biolims.mjs et-list
```

---

## 📁 Repository Layout

```
BioLIMS-SKILL/
├── scripts/              # Core API client scripts
│   ├── biolims.mjs      # Main CLI interface (auto token management)
│   ├── biolims-server.mjs    # MCP server for Claude integration
│   └── biolims-client.mjs    # API client library
├── references/          # API documentation & field mappings (16 docs)
│   ├── api.md          # Order management API reference
│   ├── receive-api.md  # Sample receiving API reference
│   ├── experiment-api.md    # Experiment center API reference
│   └── field-mapping-*.md   # Field mapping quick references
├── templates/          # JSON templates for common operations
└── SKILL.md           # Skill definition for AI assistants
```

---

## 🔧 Skills Catalog

<details open>
<summary><b>🧪 Order Management (8 skills)</b></summary>

| Skill | Description |
|-------|-------------|
| [order](SKILL.md#order) | Query order details by order ID |
| [order-list](SKILL.md#order-list) | Paginated query of order list |
| [order-samples](SKILL.md#order-samples) | Query order sample list |
| [order-fees](SKILL.md#order-fees) | Query order fee information |
| [create-order](SKILL.md#create-order) | Create new order with samples and fees |
| [update-order](SKILL.md#update-order) | Update existing order information |
| [complete-order](SKILL.md#complete-order) | Complete order and lock for editing |
| [cancel-order](SKILL.md#cancel-order) | Cancel order |

</details>

<details>
<summary><b>📦 Sample Receiving (12 skills)</b></summary>

| Skill | Description |
|-------|-------------|
| [receive-list](SKILL.md#receive-list) | Query receive order list |
| [receive](SKILL.md#receive) | Query single receive order details |
| [receive-samples](SKILL.md#receive-samples) | Query receive order sample details |
| [scan-barcode](SKILL.md#scan-barcode) | Scan barcode to get sample info |
| [scan-order](SKILL.md#scan-order) | Scan order number for batch receiving |
| [create-receive](SKILL.md#create-receive) | Create new receive order |
| [update-receive](SKILL.md#update-receive) | Update receive order |
| [complete-receive](SKILL.md#complete-receive) | Complete receive order |
| [delete-receive-item](SKILL.md#delete-receive-item) | Delete sample receive items |
| [get-orders-for-receive](SKILL.md#get-orders-for-receive) | Get available orders for receiving |
| [get-next-flows](SKILL.md#get-next-flows) | Query next step flow options |
| [sample-types](SKILL.md#sample-types) | Query all sample types |

</details>

<details>
<summary><b>🔬 Experiment Center (15 skills)</b></summary>

### Experiment Templates
| Skill | Description |
|-------|-------------|
| [et-list](SKILL.md#et-list) | Query experiment template list |
| [et-detail](SKILL.md#et-detail) | Query template details (3-layer structure) |
| [et-create](SKILL.md#et-create) | Create new experiment template |
| [et-copy](SKILL.md#et-copy) | Deep copy template with attachments |
| [et-cancel](SKILL.md#et-cancel) | Cancel experiment template |
| [et-complete](SKILL.md#et-complete) | Complete template workflow |
| [et-all-completed](SKILL.md#et-all-completed) | Query all completed templates |

### Experiment Execution
| Skill | Description |
|-------|-------------|
| [experiment-types](SKILL.md#experiment-types) | Query experiment types (NAE/LP/E/Se) |
| [experiment-protocols](SKILL.md#experiment-protocols) | Query experiment protocols by type |
| [create-experiment](SKILL.md#create-experiment) | Create experiment order |
| [experiment-list](SKILL.md#experiment-list) | Query experiment order list |
| [experiment-detail](SKILL.md#experiment-detail) | Query experiment order details |
| [update-experiment](SKILL.md#update-experiment) | Save experiment data |
| [complete-experiment-step](SKILL.md#complete-experiment-step) | Complete experiment step |
| [experiment-sample-pool](SKILL.md#experiment-sample-pool) | Manage experiment sample pool |

</details>

<details>
<summary><b>📊 Quality Control (6 skills)</b></summary>

| Skill | Description |
|-------|-------------|
| [qc-references](SKILL.md#qc-references) | Query QC reference list |
| [add-qc-reference](SKILL.md#add-qc-reference) | Add QC reference |
| [submit-qc-result](SKILL.md#submit-qc-result) | Submit QC result |
| [qc-result](SKILL.md#qc-result) | Query QC result (single) |
| [qc-results](SKILL.md#qc-results) | Query QC results (multiple) |
| [qc-check-items](SKILL.md#qc-check-items) | Query/save QC check items |

</details>

---

## 🚀 Representative Workflows

| Use Case | Example Skills | Description |
|----------|---------------|-------------|
| **Patient Order Creation** | `create-order` → `order-samples` | Create patient order with samples and fees, query confirmation |
| **Sample Batch Receiving** | `scan-order` → `create-receive` → `complete-receive` | Scan order barcode, batch receive samples, complete registration |
| **Experiment Template Setup** | `et-exp-types` → `et-create` → `et-copy` | Query experiment types, create template, copy for variations |
| **Experiment Execution** | `create-experiment` → `experiment-sample-pool` → `complete-experiment-step` | Create experiment order, manage sample pool, complete workflow steps |
| **Quality Control** | `add-qc-reference` → `submit-qc-result` → `qc-results` | Add QC reference samples, submit results, query QC records |

---

## 📊 API Coverage

### Integrated APIs (15/83)

**Order Management**: 8 APIs
- Query: order details, order list, samples, fees
- Mutation: create, update, complete, cancel

**Sample Receiving**: 12 APIs  
- Query: receive list, details, samples, next flows
- Mutation: create, update, complete, delete items
- Scanning: barcode scan, order scan

**Experiment Center**: 15 APIs
- Templates: list, detail, create, copy, cancel, complete
- Execution: types, protocols, create, list, detail, update, complete step
- Sample Pool: query, add, remove

### Pending Integration (68/83)

See [API_INTERFACE_LIST.md](API_INTERFACE_LIST.md) for complete integration roadmap.

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [SKILL.md](SKILL.md) | Complete skill definition and usage guide |
| [API_INTERFACE_LIST.md](API_INTERFACE_LIST.md) | API integration status and roadmap |
| [EXPERIMENT_CENTER_README.md](EXPERIMENT_CENTER_README.md) | Experiment center module guide |
| [SEQUENCING_QC_README.md](SEQUENCING_QC_README.md) | Sequencing QC workflow guide |

### API References

| Module | Reference | Field Mapping |
|--------|-----------|---------------|
| Order Management | [api.md](references/api.md) | [field-mapping-quick-reference.md](references/field-mapping-quick-reference.md) |
| Sample Receiving | [receive-api.md](references/receive-api.md) | [field-mapping-sample-receive-quick-reference.md](references/field-mapping-sample-receive-quick-reference.md) |
| Experiment Templates | [experiment-template-api.md](references/experiment-template-api.md) | [template-components.md](references/template-components.md) |
| Experiment Center | [experiment-api.md](references/experiment-api.md) | - |

---

## ✨ Key Features

### 🤖 Automatic Token Management
- Auto-login with encrypted credentials
- Token refresh on expiry (401 errors)
- No manual authentication required

### 🔄 Flexible Input Methods
- Direct JSON string input
- File-based input with `@filepath` syntax
- Avoids command-line escaping issues

### 📋 Field Mapping
- Automatic conversion between API field names and display names
- Support for custom fields with dynamic mapping
- Enum value translation (gender, status, etc.)

### 🎯 Conversational AI Ready
- Designed for Claude Code and AI assistants
- Natural language command descriptions
- Structured error messages with resolution hints

---

## 🛠️ Technical Stack

- **Runtime**: Node.js (ES Modules)
- **API Client**: Fetch API with automatic retry
- **Authentication**: JWT with auto-refresh
- **Integration**: Model Context Protocol (MCP) server support

---

## 📖 Usage Examples

### Query Order with Custom Fields

```bash
# Query order details
node scripts/biolims.mjs order DD2602030022

# Output includes:
# - Patient information (name, gender, age, contact)
# - Product & test information
# - Order status & progress
# - Custom fields (automatically mapped)
```

### Batch Sample Receiving

```bash
# Scan order to get unreceived samples
node scripts/biolims.mjs scan-order ORD202401180001

# Create receive order with samples
node scripts/biolims.mjs create-receive @templates/receive-template.json

# Complete receive order
node scripts/biolims.mjs complete-receive SR202401180001
```

### Experiment Template Management

```bash
# List all templates
node scripts/biolims.mjs et-list 1 20

# View template details (3-layer structure)
node scripts/biolims.mjs et-detail ET2024000001

# Copy template for modification
node scripts/biolims.mjs et-copy ET2024000001
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details

---

## 🔗 Related Projects

- [LabClaw](https://github.com/wu-yc/LabClaw) - Comprehensive laboratory AI skill library
- [Bio-LIMS](https://www.biolims.cn) - Biopharmaceutical Laboratory Information Management System

---

<div align="center">

**Built with ❤️ for the biopharmaceutical research community**

[Report Bug](https://github.com/biolims/BioLIMS-SKILL/issues) • [Request Feature](https://github.com/biolims/BioLIMS-SKILL/issues)

</div>
