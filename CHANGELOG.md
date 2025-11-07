# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial release of TogoMQ SDK for Python
- Client class for connection and message operations
- Configuration management with sensible defaults
- Message model with builder pattern
- Subscribe options with wildcards support
- Comprehensive error handling with error codes
- Configurable logging system
- Full type hints support
- Batch and streaming publish methods
- Streaming subscription with generators
- Context manager support for automatic cleanup
- Complete test suite with >80% coverage
- Comprehensive documentation and examples
- CI/CD pipeline with GitHub Actions
- Automatic PyPI publishing on release
- Support for Python 3.9+

## [0.1.0] - Initial Release

### Features
- 🚀 High-performance gRPC-based communication
- 📡 Streaming support for pub/sub operations
- 🔒 TLS encryption and token authentication
- 🎯 Simple, intuitive API
- 📝 Configurable logging
- ⚡ Thread-safe operations
- ✅ Well-tested codebase
- 🐍 Full type hints

### API Methods
- `Client.pub_batch()` - Publish batch of messages
- `Client.pub()` - Publish messages via generator (streaming)
- `Client.sub()` - Subscribe to messages with options
- `Client.close()` - Close connection
- Context manager support with `with` statement

### Configuration Options
- `host` - TogoMQ server hostname (default: q.togomq.io)
- `port` - TogoMQ server port (default: 5123)
- `token` - Authentication token (required)
- `log_level` - Logging level (default: info)
- `use_tls` - TLS encryption (default: True)

### Documentation
- Comprehensive README with examples
- API documentation in docstrings
- Multiple example scripts
- AGENTS.md for AI agent development
- CONTRIBUTING.md for contributors
- SECURITY.md for security policies

### Development
- GitHub Actions CI/CD
- Automated testing across Python versions
- Code quality checks (Black, Ruff, mypy)
- Automatic PyPI publishing
- Version management via git tags

[Unreleased]: https://github.com/TogoMQ/togomq-sdk-python/compare/v0.1.0...HEAD
[0.1.0]: https://github.com/TogoMQ/togomq-sdk-python/releases/tag/v0.1.0
