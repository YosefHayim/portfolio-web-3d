# Project Overview

This repository contains a GitHub Action that automatically scans your public and private repositories, detects their technology stack, and updates your GitHub profile README with a dynamically generated "Tech Stack" section. It helps keep your profile's proclaimed skills aligned with the actual technologies you use in your projects.

The action is designed to run on a schedule (weekly by default) or can be triggered manually. It uses the `@specfy/stack-analyser` tool to inspect repository contents and identify languages, frameworks, and tools.

# Building and Running

This is a GitHub Action and is not meant to be run locally in the same way as a typical application. It is executed by the GitHub Actions runner.

To use this action:

1.  **Set up your profile repository:** This is a repository named after your GitHub username (e.g., `your-username/your-username`).
2.  **Add markers to your `README.md`:** Insert the following markers where you want the tech stack to appear:

    ```markdown
    <!-- TECHSTACK:START -->
    <!-- The content below is auto-generated. Do not edit manually. -->
    <!-- TECHSTACK:END -->
    ```
3.  **Configure the workflow:** Copy the `.github/workflows/tech-stack-sync.yml` file into your profile repository. The action will then run automatically.

# Development Conventions

*   **Core Logic:** The main logic is contained within the `.github/workflows/tech-stack-sync.yml` file, primarily in the `Collect stacks and update README` step.
*   **Technology Analysis:** The `@specfy/stack-analyser` npm package is the core dependency for technology detection.
*   **Data Manipulation:** The workflow heavily relies on shell scripting, using tools like `jq` for JSON processing and `awk` for text manipulation to generate the final Markdown output.
*   **Output:** The action generates two artifacts:
    *   `stacks.json`: A JSON file containing the raw data of the analyzed stacks.
    *   An updated `README.md` with the generated tech stack summary.
*   **Committing:** The action will commit the updated `README.md` and `stacks.json` to the repository.
