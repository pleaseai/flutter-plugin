---
name: Flutter and Dart Development
description: Build Flutter applications with expert Dart coding, widget composition, and MCP tools for formatting, linting, and package management. Use when working with Flutter projects, Dart code, mobile apps, or when user mentions Flutter, Dart, widgets, StatefulWidget, StatelessWidget, pub.dev, cross-platform development, or UI components.
allowed-tools: mcp__dart__dart_format, mcp__dart__dart_fix, mcp__dart__analyze_files, mcp__dart__pub, mcp__dart__pub_dev_search
---

# Flutter & Dart Development

Expert Flutter and Dart development with MCP tools for code quality and package management.

## Key Principles

**SOLID & Composition**
- Apply SOLID principles throughout
- Favor composition over inheritance for complex widgets
- Build UI from smaller, reusable widgets

**Immutability & State**
- Prefer immutable data structures
- StatelessWidget should be immutable
- Separate ephemeral state from app state

**Code Quality**
- Functions < 20 lines, single purpose
- PascalCase (classes), camelCase (members), snake_case (files)
- Line length ≤ 80 characters
- Handle errors explicitly

## MCP Tool Workflow

1. **Format**: Use `dart_format` for consistent formatting
2. **Fix**: Use `dart_fix` to auto-fix common errors
3. **Analyze**: Use `analyze_files` to run linter

**Package Management**:
- Search: `pub_dev_search` to find packages
- Manage: `pub` to add/remove dependencies

## Flutter Patterns

**State Management**
- Separate UI from business logic
- Use modern state management solutions

**Navigation**
- Use go_router or auto_route
- See [navigation.md](./navigation.md) for examples

**Testing**
- Write testable code with dependency injection
- Use file, process, platform packages for fakes

## Dart-Specific

- Follow [Effective Dart](https://dart.dev/effective-dart)
- Explain null safety, futures, streams to users
- Use logging package instead of print
- Document all public APIs

For complete guidelines, see [flutter.md](./flutter.md)