# Contributing to StacksBridge

Thank you for your interest in contributing to StacksBridge! This document provides guidelines for contributing to the project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Code Style Guidelines](#code-style-guidelines)
- [Testing Requirements](#testing-requirements)
- [Pull Request Process](#pull-request-process)
- [Security Considerations](#security-considerations)

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct:

- Be respectful and inclusive
- Focus on constructive feedback
- Help maintain a welcoming environment
- Report any unacceptable behavior

## Getting Started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) v2.0+
- [Node.js](https://nodejs.org/) v18+
- [Git](https://git-scm.com/)
- Basic understanding of Clarity and Bitcoin concepts

### Initial Setup

1. Fork the repository on GitHub
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/stacks-bridge.git
   cd stacks-bridge
   ```
3. Add the original repository as upstream:
   ```bash
   git remote add upstream https://github.com/barlogun/stacks-bridge.git
   ```
4. Install dependencies:
   ```bash
   npm install
   ```
5. Verify everything works:
   ```bash
   clarinet check
   npm test
   ```

## Development Workflow

### Branching Strategy

- `main`: Production-ready code
- `develop`: Integration branch for new features
- `feature/description`: Feature development branches
- `hotfix/description`: Critical bug fixes

### Creating a Feature Branch

```bash
git checkout develop
git pull upstream develop
git checkout -b feature/your-feature-name
```

### Making Changes

1. Make your changes in logical, focused commits
2. Write or update tests for your changes
3. Ensure all tests pass: `npm test`
4. Verify contract syntax: `clarinet check`
5. Update documentation if needed

### Commit Message Format

Use conventional commit format:

```
type(scope): description

[optional body]

[optional footer]
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code refactoring
- `test`: Test changes
- `chore`: Build/tooling changes

Examples:
```
feat(channels): add multi-party channel support
fix(validation): correct balance verification logic
docs(readme): update API documentation
```

## Code Style Guidelines

### Clarity Code Style

- Use descriptive variable and function names
- Include comprehensive comments for complex logic
- Follow consistent indentation (2 spaces)
- Group related functions together
- Use constants for magic numbers

Example:
```clarity
;; Good: Descriptive name and clear purpose
(define-private (validate-channel-parameters
    (channel-id (buff 32))
    (funding-amount uint)
  )
  (and
    (validate-channel-id channel-id)
    (validate-deposit-amount funding-amount)
  )
)

;; Bad: Unclear naming and no comments
(define-private (check (id (buff 32)) (amt uint))
  (and (= (len id) u32) (>= amt u1000))
)
```

### TypeScript Code Style

- Use TypeScript strict mode
- Prefer explicit types over `any`
- Use descriptive variable names
- Include JSDoc comments for public functions

### General Guidelines

- Keep functions focused and single-purpose
- Avoid deeply nested code structures
- Use meaningful error messages
- Include input validation for all public functions

## Testing Requirements

### Test Categories

1. **Unit Tests**: Test individual functions
2. **Integration Tests**: Test function interactions
3. **Edge Case Tests**: Test boundary conditions
4. **Security Tests**: Test attack vectors

### Writing Tests

- Write tests before or alongside code changes
- Use descriptive test names
- Test both success and failure cases
- Include edge cases and boundary conditions

Example test structure:
```typescript
describe("establish-channel", () => {
  it("should create channel with valid parameters", () => {
    // Test successful channel creation
  });

  it("should reject channel with invalid ID", () => {
    // Test validation failure
  });

  it("should reject insufficient funding", () => {
    // Test minimum funding requirement
  });
});
```

### Running Tests

```bash
# Run all tests
npm test

# Run tests with coverage
npm run test:report

# Run tests in watch mode
npm run test:watch
```

## Pull Request Process

### Before Submitting

1. Ensure all tests pass
2. Verify contract compiles without errors
3. Update documentation if needed
4. Rebase your branch on latest develop
5. Write clear commit messages

### PR Description Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests pass
- [ ] Manual testing completed

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Documentation updated
- [ ] Tests added/updated
```

### Review Process

1. Automated checks must pass
2. At least one code review required
3. All discussions must be resolved
4. Maintainer approval needed for merge

## Security Considerations

### Security-First Development

- Always validate inputs
- Use safe math operations
- Implement proper access controls
- Consider reentrancy attacks
- Test edge cases thoroughly

### Reporting Security Issues

**DO NOT** create public issues for security vulnerabilities.

Instead:
1. Email security concerns to [security@stacksbridge.com]
2. Include detailed reproduction steps
3. Wait for acknowledgment before disclosure

### Security Review Checklist

- [ ] Input validation implemented
- [ ] Access controls verified
- [ ] Integer overflow/underflow prevented
- [ ] Reentrancy protection added
- [ ] Gas optimization considered
- [ ] Error handling comprehensive

## Documentation Standards

### Code Documentation

- Document all public functions
- Explain complex algorithms
- Include usage examples
- Document error conditions

### README Updates

Update documentation when:
- Adding new features
- Changing APIs
- Modifying deployment process
- Adding dependencies

## Questions and Support

### Getting Help

- **GitHub Discussions**: General questions and ideas
- **GitHub Issues**: Bug reports and feature requests
- **Discord**: Real-time community support
- **Email**: Direct contact for sensitive issues

### Before Asking

1. Search existing issues and discussions
2. Read the documentation thoroughly
3. Try reproducing the issue locally
4. Prepare a minimal reproduction case

## Recognition

Contributors will be recognized in:
- GitHub contributors list
- Release notes for significant contributions
- Project documentation credits
- Community highlights

Thank you for helping make StacksBridge better! 🚀
