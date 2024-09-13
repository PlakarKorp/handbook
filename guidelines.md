# Plakar Development Guidelines

## Code Simplicity and Clarity

Write code that is simple, clear, and easy to maintain. Prioritize readability over cleverness.
Avoid unnecessary abstractions, and aim for straightforward implementations.
Ensure that every line of code serves a clear purpose and avoids ambiguity.


## Security First

Integrate security principles from the start. Follow a secure-by-default approach.
Use safe coding practices (e.g., bounds-checking, avoiding unsafe functions).
Implement privilege separation, least privilege, and compartmentalization where applicable.
Perform regular code audits to detect vulnerabilities early.


## Code Auditing and Peer Review

All code changes must be reviewed by peers before merging. Peer review is essential to maintaining high-quality, secure, and efficient code.
Encourage contributors to explain the rationale behind significant changes or design choices during reviews.


## Minimal and Carefully Managed Dependencies

Keep external dependencies to a minimum. Only use dependencies that are well-maintained and absolutely necessary for the project.
Carefully evaluate the licenses of third-party dependencies to avoid reliance on viral licensing (e.g., GPL) that could impose unwanted restrictions on the project.
Favor permissively licensed, widely supported libraries and tools.


## Incremental and Reversible Changes

Make small, incremental changes instead of large, sweeping modifications.
Ensure that changes are easy to reverse or mitigate in case they introduce issues.


## Consistent Code Style

Adhere to a strict coding style across the project for consistency. Use uniform naming conventions, indentation, and structuring.
Run code formatters and linters as part of the CI pipeline to enforce these rules.


## Focus on Correctness

Code correctness is paramount. Before optimizing for performance, ensure that the code behaves as expected in all situations.
Write test cases for all code, covering both common and edge cases.


## Comprehensive Documentation

Missing documentation is considered a bug. Every function, module, and design decision must be documented comprehensively.
Write man pages or equivalent documentation for all user-facing features.
Ensure comments explain the “why” behind complex code, not just the “how.”


## Code Cleanup Is Work

Treat code cleanup as a priority. Removing unused or unnecessary code is an essential part of keeping the codebase clean, maintainable, and efficient.
Do not allow unused, redundant, or cluttering code to accumulate in the project.


## Technical Superiority First

The only factor that matters in decision-making is technical superiority. The quality and merit of the code take precedence over who authored the contribution.
Encourage contributions from all, but maintain rigorous technical standards.


## Open Collaboration

Encourage contributions from the community and foster an environment where external contributors feel welcome.
Make the contribution process clear and accessible, including well-defined workflows for submitting patches or issues.


## Strict Version Control Practices

Use version control (e.g., Git) rigorously. All commits should have clear, concise messages that explain the changes.
Use branches for development and testing, and only merge into the main branch after passing review and automated tests.


## Automated Testing and CI/CD

Implement a continuous integration (CI) pipeline to automatically run tests, linting, and security checks on all contributions.
Ensure that every change is tested across multiple platforms and environments.


## Regular Code Audits

Periodically perform in-depth security audits of the codebase. Use external auditors when necessary to ensure unbiased reviews.
Follow a proactive approach to identifying and fixing potential security issues.
By following these guidelines, Plakar will maintain a clean, secure, and technically superior codebase, promoting transparency, collaboration, and excellence across all development efforts.
