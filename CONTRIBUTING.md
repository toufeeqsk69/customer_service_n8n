# Contributing to Max Pharma N8N Customer Service Automation

Thank you for your interest in contributing to the Max Pharma AI-powered customer service automation project! 🎉

This guide will help you understand how to contribute effectively to our N8N-based WhatsApp automation system.

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [Contribution Guidelines](#contribution-guidelines)
- [Workflow Development](#workflow-development)
- [AI Agent Improvements](#ai-agent-improvements)
- [Testing Guidelines](#testing-guidelines)
- [Submission Process](#submission-process)
- [Style Guide](#style-guide)
- [Issue Reporting](#issue-reporting)

## 🤝 Code of Conduct

We are committed to providing a welcoming and inclusive experience for everyone. Please be respectful and professional in all interactions.

### Our Standards
- ✅ Use welcoming and inclusive language
- ✅ Respect differing viewpoints and experiences
- ✅ Focus on what is best for the community
- ✅ Show empathy towards other contributors
- ❌ Use of sexualized language or imagery
- ❌ Personal attacks or insulting comments
- ❌ Harassment of any kind

## 🚀 Getting Started

### Prerequisites

Before contributing, ensure you have:

- [ ] **N8N Experience** - Familiarity with N8N workflow development
- [ ] **JavaScript Knowledge** - Understanding of Node.js and async programming
- [ ] **API Integration** - Experience with REST APIs and webhooks
- [ ] **Arabic Language** - Understanding of Egyptian Arabic (for AI improvements)
- [ ] **Google Workspace** - Knowledge of Google Sheets and Calendar APIs

### Areas for Contribution

We welcome contributions in these areas:

| Area | Description | Skill Level |
|------|-------------|-------------|
| 🔄 **Workflow Enhancement** | Improve existing N8N workflows | Intermediate |
| 🤖 **AI Agent Development** | Enhance Mahmoud's conversational abilities | Advanced |
| 🔧 **Tool Integration** | Add new business tools and APIs | Intermediate |
| 📊 **Analytics & Reporting** | Build monitoring and reporting features | Intermediate |
| 🌍 **Localization** | Add support for additional languages | Beginner |
| 📖 **Documentation** | Improve guides and documentation | Beginner |
| 🐛 **Bug Fixes** | Fix issues and improve stability | All Levels |

## ⚙️ Development Setup

### 1. Fork and Clone

```bash
# Fork the repository on GitHub, then clone your fork
git clone Ahmed-Esso/N8N-Customer-Service.git
cd max-pharma-n8n-automation

```

### 2. N8N Environment Setup

```bash
# Install N8N locally (if not using cloud)
npm install n8n -g

# Start N8N
n8n start

# Import workflow files
# Navigate to http://localhost:5678
# Import the JSON workflow files from the repository
```

### 3. Configure Test Environment

Create a test environment with:
- **Test Google Sheets** - Separate sheets for development
- **Test WhatsApp Number** - Use WhatsApp Business API sandbox
- **Development API Keys** - Separate API credentials
- **Test Calendar** - Dedicated Google Calendar for testing

### 4. Environment Variables

Create a `.env` file with your test credentials:
```bash
# Google APIs
GOOGLE_SHEETS_CLIENT_ID=your-test-client-id
GOOGLE_SHEETS_CLIENT_SECRET=your-test-client-secret
GOOGLE_CALENDAR_CLIENT_ID=your-test-calendar-id

# WhatsApp API
WHATSAPP_API_URL=your-test-webhook-url
WHATSAPP_API_TOKEN=your-test-token

# AI Model
GEMINI_API_KEY=your-test-gemini-key
```

## 📝 Contribution Guidelines

### Workflow Contributions

When modifying N8N workflows:

#### ✅ **DO:**
- **Test Thoroughly** - Test all branches and edge cases
- **Add Error Handling** - Include proper error nodes and fallbacks
- **Document Changes** - Add comments to complex nodes
- **Optimize Performance** - Minimize API calls and processing time
- **Follow Naming Conventions** - Use clear, descriptive node names

#### ❌ **DON'T:**
- **Break Existing Functionality** - Ensure backwards compatibility
- **Hardcode Values** - Use environment variables for configuration
- **Ignore Edge Cases** - Handle empty responses and errors
- **Skip Testing** - Always test with real data
- **Remove Error Handling** - Maintain robust error management

### Code Style for Custom Functions

```javascript
// ✅ Good - Clear, documented function
async function processCustomerMessage(message, customerPhone) {
  try {
    // Validate input
    if (!message || !customerPhone) {
      throw new Error('Missing required parameters');
    }
    
    // Process message
    const processedMessage = await aiAgent.process(message);
    
    return {
      success: true,
      response: processedMessage,
      timestamp: new Date().toISOString()
    };
  } catch (error) {
    console.error('Error processing message:', error);
    return {
      success: false,
      error: error.message
    };
  }
}

// ❌ Bad - No error handling, unclear logic
function process(msg) {
  return ai.process(msg).response;
}
```

## 🤖 AI Agent Improvements

### Enhancing Mahmoud's Capabilities

When improving the AI agent:

#### Conversation Flow
- **Context Awareness** - Ensure responses consider conversation history
- **Egyptian Dialect** - Maintain natural Arabic language patterns
- **Tone Matching** - Adapt responses to customer mood
- **Business Logic** - Follow Max Pharma's business rules

#### Response Quality
```javascript
// ✅ Good - Natural Egyptian Arabic response
const response = `أهلاً ${customerName}! إزيك يا فندم؟ 
أنا محمود من خدمة عملاء Max Pharma. 
المنتج ده متوفر بسعر ${price} جنيه. عاوز تطلبه؟`;

// ❌ Bad - Formal/unnatural Arabic
const response = `مرحباً سيد ${customerName}. 
هذا المنتج متوفر بسعر ${price} جنيه مصري. 
هل ترغب في طلبه؟`;
```

## 🧪 Testing Guidelines

### Testing Checklist

Before submitting your contribution:

#### Workflow Testing
- [ ] **Happy Path** - Test normal conversation flows
- [ ] **Edge Cases** - Test with invalid inputs and edge conditions
- [ ] **Error Scenarios** - Verify error handling works correctly
- [ ] **Performance** - Ensure responses are under 3 seconds
- [ ] **Memory Usage** - Test conversation memory retention

#### Integration Testing
- [ ] **WhatsApp Integration** - Test message sending/receiving
- [ ] **Google Sheets** - Verify data is written correctly
- [ ] **Calendar API** - Test appointment creation/updates
- [ ] **AI Responses** - Validate response quality and relevance

#### User Acceptance Testing
- [ ] **Customer Journey** - Complete end-to-end customer scenarios
- [ ] **Business Logic** - Verify all business rules are followed
- [ ] **Arabic Language** - Native speaker review of responses

### Test Data

Use these test scenarios:

```javascript
// Test Product Search
testMessages = [
  "عاوز أعرف سعر حمض ستيريك",
  "محتاج مواد تنظيف للمصنع",
  "ايه المنتجات المتوفرة للشعر؟"
];

// Test Order Creation
testOrders = [
  { product: "Stearic Acid", quantity: "10kg", phone: "+201234567890" },
  { product: "L-Tyrosine", quantity: "5kg", phone: "+201234567891" }
];

// Test Factory Visits
testVisits = [
  { name: "أحمد محمد", date: "2025-09-15", time: "10:00 AM" },
  { name: "فاطمة علي", date: "2025-09-20", time: "2:00 PM" }
];
```

## 📤 Submission Process

### Step-by-Step Guide

1. **Create Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make Your Changes**
   - Implement your feature or fix
   - Add appropriate tests
   - Update documentation if needed

3. **Test Thoroughly**
   - Run all test scenarios
   - Verify existing functionality still works
   - Test with real WhatsApp messages

4. **Commit Changes**
   ```bash
   git add .
   git commit -m "feat: add customer mood detection to AI agent"
   ```

5. **Push and Create PR**
   ```bash
   git push origin feature/your-feature-name
   ```
   Then create a Pull Request on GitHub.

### Commit Message Format

Use conventional commits:

```bash
# Features
feat: add voice message transcription support
feat: implement inventory checking tool

# Bug fixes  
fix: resolve order validation error
fix: correct Arabic text encoding issue

# Documentation
docs: update API integration guide
docs: add troubleshooting section

# Performance
perf: optimize product search response time
perf: reduce memory usage in conversation buffer

# Refactoring
refactor: simplify order creation workflow
refactor: improve error handling structure
```

## 🎨 Style Guide

### N8N Workflow Organization

#### Node Naming
- **Clear Names** - Use descriptive names like "Process Customer Message"
- **Consistent Prefixes** - Use prefixes like "Check:", "Send:", "Process:"
- **No Abbreviations** - Avoid shortened names that aren't clear

#### Workflow Structure
- **Left to Right Flow** - Arrange nodes in logical left-to-right order
- **Group Related Nodes** - Use visual grouping for related functionality
- **Color Coding** - Use consistent colors for node types
- **Clean Layout** - Avoid overlapping connections

### Documentation Standards

#### Code Comments
```javascript
// ✅ Good - Explains business logic
// Check if customer is asking about factory visit
// Egyptian phrase patterns: "عاوز أزور", "محتاج زيارة"
if (message.includes('زيارة') || message.includes('مصنع')) {
  return 'factory_visit_intent';
}

// ❌ Bad - Obvious comment
// Check if message contains visit
if (message.includes('زيارة')) {
```

#### README Updates
- Update feature lists when adding new capabilities
- Include new environment variables in setup instructions
- Add examples for new functionality
- Update architecture diagrams if needed

## 🐛 Issue Reporting

### Bug Report Template

When reporting bugs:

```markdown
## Bug Description
Brief description of the issue

## Steps to Reproduce
1. Send WhatsApp message: "عاوز أطلب منتج"
2. AI responds with...
3. Error occurs at...

## Expected Behavior
What should have happened

## Actual Behavior  
What actually happened

## Environment
- N8N Version: 
- Node.js Version:
- WhatsApp API: Evolution API
- Error Screenshots: (attach if applicable)

## Additional Context
Any other relevant information
```

### Feature Request Template

```markdown
## Feature Description
Clear description of the proposed feature

## Business Value
How this helps Max Pharma's customers or operations

## Proposed Implementation
Technical approach or suggestions

## Additional Context
Examples, mockups, or related features
```

## 🎯 Priority Areas

Current high-priority contribution areas:

| Priority | Area | Description |
|----------|------|-------------|
| 🔥 **High** | Voice Message Processing | Improve Arabic voice transcription accuracy |
| 🔥 **High** | Error Recovery | Better handling of API failures |
| 🔥 **High** | Performance Optimization | Reduce response times |
| ⚡ **Medium** | Payment Integration | Add payment processing capabilities |
| ⚡ **Medium** | Analytics Dashboard | Create usage and performance metrics |
| 💡 **Low** | Multi-language Support | Add English and French support |

## 🏆 Recognition

Contributors will be recognized in:
- **README.md** - Listed in acknowledgments
- **Release Notes** - Credited for features and fixes
- **Project Documentation** - Author attribution where appropriate

## ❓ Questions?

If you have questions about contributing:

1. **Check Documentation** - Review README and existing code
2. **Search Issues** - Look for similar questions or discussions
3. **Create Discussion** - Start a GitHub discussion for general questions
4. **Open Issue** - Create an issue for specific bugs or feature requests

---

Thank you for contributing to Max Pharma's customer service automation! Your efforts help improve customer experience for businesses across Egypt. 🇪🇬✨
