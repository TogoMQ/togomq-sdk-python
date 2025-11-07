# Security Policy

## Supported Versions

We release patches for security vulnerabilities for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| 0.1.x   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability within the TogoMQ SDK for Python, please send an email to security@togomq.io. All security vulnerabilities will be promptly addressed.

Please do **not** create public GitHub issues for security vulnerabilities.

### What to Include

When reporting a vulnerability, please include:

- Type of vulnerability
- Full paths of source file(s) related to the vulnerability
- Location of the affected source code (tag/branch/commit or direct URL)
- Step-by-step instructions to reproduce the issue
- Proof-of-concept or exploit code (if possible)
- Impact of the vulnerability
- How you discovered the vulnerability

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Depends on severity and complexity

### Disclosure Policy

- We will confirm the vulnerability and work on a fix
- We will release a security advisory on GitHub
- We will credit you for the discovery (unless you prefer to remain anonymous)

## Security Best Practices

When using the TogoMQ SDK:

1. **Protect Your Token**: Never commit authentication tokens to version control
2. **Use Environment Variables**: Store tokens in environment variables or secure vaults
3. **Enable TLS**: Always use TLS in production (default: enabled)
4. **Validate Input**: Validate message content before publishing
5. **Handle Errors**: Properly handle and log errors without exposing sensitive data
6. **Keep Updated**: Regularly update to the latest version

## Known Security Considerations

- **Authentication**: SDK uses token-based authentication over TLS
- **Network**: All communication with TogoMQ uses gRPC over TLS by default
- **Dependencies**: We regularly update dependencies to address security issues

## Contact

- **Security Issues**: security@togomq.io
- **General Support**: https://togomq.io/docs
- **GitHub Issues**: https://github.com/TogoMQ/togomq-sdk-python/issues (for non-security bugs)
