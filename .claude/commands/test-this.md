---
description: Generate unit tests for a file or function
argument-hint: [file-path]
allowed-tools: Read, Write, Bash
---

Generate comprehensive unit tests for $ARGUMENTS:

1. Read the file and understand its functionality
2. Identify all functions/methods to test
3. Create tests covering:
   - Happy path (normal usage)
   - Edge cases (empty, null, boundaries)
   - Error conditions
4. Use the project's existing test framework
5. Follow existing test patterns in the codebase
