# Contributing to DeVault

Thank you for your interest in contributing to DeVault! We welcome contributions from the community to help build a secure, decentralized document storage and verification platform.

---

## Table of Contents
- [How to Contribute](#how-to-contribute)
- [Code Standards](#code-standards)
- [Pull Request Process](#pull-request-process)
- [Issue Reporting](#issue-reporting)
- [Security Best Practices](#security-best-practices)
- [Community Standards](#community-standards)

---

## How to Contribute

1. **Fork the repository** and clone your fork locally.
2. **Create a new branch** for your feature or bugfix:
   ```sh
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the code standards below.
4. **Test your changes** locally.
5. **Commit and push** your branch to your fork.
6. **Open a Pull Request** (PR) against the `main` branch of the upstream repository.

---

## Code Standards

- **Frontend (React):**
  - Use the Airbnb JavaScript Style Guide.
  - Use TSDoc for TypeScript and JSDoc for JavaScript documentation.
  - Write clear, descriptive comments using the Better Comments style.
  - Ensure all user input is validated and sanitized.

- **Backend (Motoko):**
  - Follow Motoko best practices for canister development.
  - Separate type definitions into dedicated files (e.g., `types.mo`).
  - Use stable data structures for persistent state.
  - Include error handling and input validation.

- **General:**
  - Write meaningful commit messages.
  - Keep pull requests focused and small.
  - Add or update tests as appropriate.

---

## Pull Request Process

1. Ensure your branch is up to date with `main`.
2. Open a PR with a clear description of your changes and reference any related issues.
3. The PR will be reviewed by maintainers. Please respond to feedback promptly.
4. All checks (CI, tests, linting) must pass before merging.
5. Once approved, your PR will be merged by a maintainer.

---

## Issue Reporting

- Search existing issues before opening a new one.
- Provide a clear, descriptive title and detailed information.
- Include steps to reproduce, expected behavior, and screenshots/logs if relevant.
- For security vulnerabilities, see the section below.

---

## Security Best Practices

- **Do not submit sensitive data** (e.g., private keys, passwords) in issues or PRs.
- Report security vulnerabilities **privately** by emailing the maintainers or using the repository's security disclosure process.
- Follow secure coding practices:
  - Validate and sanitize all user input.
  - Never log sensitive information.
  - Use environment variables for secrets and configuration.
- Review the [ARCHITECTURE.md](ARCHITECTURE.md) and [README.md](README.md) for more details on security and system design.

---

## Community Standards

- Be respectful and inclusive in all interactions.
- Provide constructive feedback and collaborate openly.
- Help us maintain a welcoming and safe environment for everyone.

---

Thank you for helping make DeVault better!
