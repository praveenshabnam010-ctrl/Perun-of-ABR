# Contributing to Perun and ABR

Thank you for your interest in Perun and ABR. Contributions of all sizes are welcome, including hardware design, firmware, documentation, testing and constructive review.

## Project scope

Perun is the broader open-source software and hardware ecosystem. ABR is the weather station hardware project within Perun.

Keep ABR-specific files separate from broader Perun documentation. Do not present planned features as implemented or tested features.

## Before you start

- Read the README and the documentation in `ABR/documentation/`.
- Inspect the existing work before proposing changes.
- Open an issue before making major architectural, hardware or cost-affecting changes.
- Do not overwrite or rewrite existing working work without permission.
- Ask for clarification when the requirements are unclear.

## Ways to contribute

- Hardware design, component selection and verification.
- Firmware development and testing.
- Documentation, diagrams and reproducibility checks.
- Reporting issues, limitations and failed attempts.

## Reporting and proposing changes

- Small corrections can be submitted directly as a pull request.
- Major changes should be discussed in an issue first.
- Explain any trade-offs that affect cost, hardware compatibility or project architecture.
- Do not claim hardware compatibility without checking the relevant datasheets and technical requirements.
- Do not invent specifications, prices, measurements or test results.

## Coding standards

- Write readable, maintainable C/C++ suitable for Arduino-compatible hardware.
- Use meaningful variable and function names.
- Keep modules responsible for specific tasks.
- Prefer lightweight dependencies and avoid unnecessarily complicated libraries.
- Comment important or non-obvious logic.
- Handle sensor errors and missing readings gracefully.
- Avoid blocking operations that could interfere with measurement scheduling.
- Explain the purpose of any new dependency.

## Documentation standards

- Prefer clear, straightforward language and explain technical terms where useful.
- Use consistent naming throughout the repository.
- Clearly distinguish between **Planned**, **In development**, **Implemented** and **Tested**.
- Update relevant documentation when code or hardware changes.
- Do not document proposed functionality as completed functionality.

## Hardware contributions

- Verify component requirements against datasheets.
- Check logic levels, power requirements and pin conflicts.
- Consider price, local availability, reliability and reproducibility.
- Update the bill of materials and pin map when the design changes.
- Avoid adding expensive components without clear justification.
- Do not assume that a module variant is compatible because a similar module is.

## Commit and pull request guidance

- Keep changes focused and avoid unrelated modifications.
- Write clear commit messages that describe the change.
- Do not commit API keys, credentials, secrets or personal data.
- Describe new dependencies and why they are needed.
- Include documentation updates with functional changes.

## Licence

The project licence has not yet been finalised. A `LICENSE` file will be added once the licence is chosen. Until then, do not assume reuse rights beyond what is provided by GitHub's terms and the project maintainers' permission.

## AI assistance

This project uses AI tools (OpenCode, Nemotron 3 Ultra) for coding assistance. All design decisions, review and responsibility remain with the human maintainers. AI-generated content must be verified before committing.

## Questions

Open an issue if anything is unclear. Constructive questions and suggestions are welcome.
