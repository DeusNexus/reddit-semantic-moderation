# Contributing to ModBotAI

Thank you for your interest in contributing! Please follow these guidelines to help keep the project maintainable and high-quality.

## Getting Started

1. **Fork the repository** and clone your fork locally.
2. **Create a new branch** for your feature or fix:
   ```bash
   git checkout -b my-feature
   ```
3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

## Development Guidelines

- Use **Python 3.10+**.
- Follow [PEP 8](https://peps.python.org/pep-0008/) style and use type hints everywhere.
- Write unit and integration tests for new features (`tests/`).
- Run `black .` and `mypy .` before pushing code.
- Document new functions, modules, and any public APIs.

## Pull Requests

- Ensure your branch is up to date with `main`.
- Reference related issues (if any) in your PR description.
- Pass all CI checks: tests, linting, and type checks.
- One feature/fix per pull request.
- PRs should include a clear description of changes.

## Reporting Issues

- Use the GitHub Issues tracker to report bugs or suggest features.
- Include as much detail as possible—error logs, OS/Python version, steps to reproduce.

## Code of Conduct

- Please be respectful, constructive, and welcoming in all project interactions.

## License

By contributing, you agree that your code will be licensed under the MIT License.