# github-profile-techstack-sync

GitHub Action that scans your repositories, detects their tech stack, and updates your profile README with a generated “Tech Stack” section.

## How it works

- Lists repositories for a given user or organization using the GitHub API.
- Clones each repository (shallow clone) and runs a stack analyzer.
- Aggregates detected technologies (languages, frameworks, tools).
- Regenerates a dedicated section in your profile README between marker comments.
- Commits and pushes changes back to the profile repository.

## Use cases

- Keep your profile README always aligned with your actual code.
- Show top languages and frameworks across all repos.
- Highlight infra and tooling (CI (Continuous Integration), cloud, databases) in one place.

## Quick start

1. Create or use your profile repository:

   - It must be named `<your-github-username>/<your-github-username>`.
   - Ensure a `README.md` exists.

2. Add the Tech Stack marker to your `README.md`:

   ```md
   <!-- TECHSTACK:START -->
   <!-- The content below is auto-generated. Do not edit manually. -->
   <!-- TECHSTACK:END -->
