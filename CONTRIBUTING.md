# Contributing to TogoMQ SDK for Python

Thank you for your interest in contributing to the TogoMQ SDK for Python! This document provides guidelines and instructions for contributing.

## Development Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/TogoMQ/togomq-sdk-python.git
   cd togomq-sdk-python
   ```

2. **Create a virtual environment**:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -e ".[dev]"
   ```

## Code Style

We follow Python best practices and use automated tools to maintain code quality:

- **Black** for code formatting (line length: 100)
- **Ruff** for linting
- **mypy** for type checking

Run these before committing:

```bash
# Format code
black togomq tests examples

# Lint
ruff check togomq tests examples

# Type check
mypy togomq
```

## Testing

We use pytest for testing. All new features should include tests.

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=togomq --cov-report=html

# Run specific test file
pytest tests/test_client.py

# Run specific test
pytest tests/test_client.py::TestClient::test_client_creation
```

### Test Guidelines

- Write tests for all new functionality
- Aim for >80% code coverage
- Test both success and error paths
- Use mocks for gRPC calls
- Follow existing test patterns

## Pull Request Process

1. **Fork** the repository
2. **Create a branch** for your feature: `git checkout -b feature/my-feature`
3. **Make your changes** and commit with clear messages
4. **Add tests** for your changes
5. **Run the test suite** and ensure all tests pass
6. **Run code quality tools** (black, ruff, mypy)
7. **Push** your branch: `git push origin feature/my-feature`
8. **Open a Pull Request** with a clear description

### Pull Request Guidelines

- Provide a clear description of the changes
- Reference any related issues
- Ensure CI checks pass
- Update documentation if needed
- Add examples if introducing new features

## Commit Messages

Follow conventional commit format:

- `feat: Add new feature`
- `fix: Fix bug in client`
- `docs: Update README`
- `test: Add tests for config`
- `refactor: Improve error handling`
- `chore: Update dependencies`

## Project Structure

```
togomq-sdk-python/
├── togomq/              # Main package
│   ├── __init__.py
│   ├── client.py        # Client implementation
│   ├── config.py        # Configuration
│   ├── message.py       # Message model
│   ├── errors.py        # Error handling
│   └── ...
├── tests/               # Test suite
│   ├── test_client.py
│   ├── test_config.py
│   └── ...
├── examples/            # Usage examples
│   ├── publish.py
│   ├── subscribe.py
│   └── ...
├── .github/             # GitHub workflows
│   └── workflows/
│       ├── ci.yml
│       └── release.yml
└── pyproject.toml       # Package configuration
```

## Adding New Features

When adding a new feature:

1. **Design** the API to match existing patterns
2. **Implement** the feature with type hints
3. **Document** with docstrings and examples
4. **Test** thoroughly with unit tests
5. **Update** README.md and examples
6. **Update** AGENTS.md if relevant for AI agents

## Reporting Issues

When reporting issues, please include:

- Python version
- SDK version
- Operating system
- Steps to reproduce
- Expected vs actual behavior
- Any error messages or stack traces

## Questions?

- Check existing [Issues](https://github.com/TogoMQ/togomq-sdk-python/issues)
- Review the [Documentation](https://togomq.io/docs)
- Ask in a new issue with the "question" label

## Code of Conduct

- Be respectful and inclusive
- Welcome newcomers
- Focus on constructive feedback
- Follow Python community standards

## License

By contributing, you agree that your contributions will be licensed under the MIT License.
