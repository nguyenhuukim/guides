---
trigger: always_on
---

# Agent Rules: Git-Safe & Formatting Policy

To maintain a clean Git history and avoid unnecessary diffs, the Agent must adhere to the following rules regarding code formatting and structure:

## 1. Respect Existing Code Structure

- **Strict No-Autoformat:** Do NOT automatically reformat, beautify, or reorder content (such as imports or methods) in existing source code files.
- **Explicit Request Only:** Reformatting or structural reorganization should only be performed if the user provides a specific and explicit instruction to do so.
- **Local Consistency:** When adding new code, match the existing file's indentation and style, but do not touch the rest of the file.

## 2. Proposal-First Policy

- **Identify Improvements:** If you notice that a file requires reformatting, better organization, or violates project standards, you must **propose** these changes first.
- **Wait for Consent:** Present your recommendation to the user (e.g., "I recommend reordering these methods for better readability, which will affect Git history. Should I proceed?").
- **Action:** Only apply structural changes or reformatting AFTER receiving explicit confirmation from the user.

## 3. Objective

- The primary goal is to **minimize unnecessary Git changes**.
- Ensure that every line changed in a Pull Request is relevant to the functional task at hand, not just a stylistic preference.
