# RAC Diagrams

This directory contains Mermaid diagrams that visualize various aspects of the RAC specifications.

## Available Diagrams

1. **Motion Status Flow** (`motion-status-flow.md`)
   - Shows the flow of motion status checking and permission handling
   - Based on `motion-status.test.rac.yaml`

2. **Security Context Flow** (`security-context-flow.md`)
   - Illustrates security context validation and its impact on motion detection
   - Based on `security-requirements.test.rac.yaml`

3. **Motion Detection Permission Flow** (`motion-detection-permission-flow.md`)
   - Shows the sequence of interactions between components for motion detection
   - Combines flows from multiple test files

4. **Error Handling Flow** (`error-handling-flow.md`)
   - Visualizes error handling flows and recovery paths
   - Based on `motion-status.test.rac.yaml`

## Viewing the Diagrams

These diagrams are written in Mermaid syntax and can be viewed in any Markdown viewer that supports Mermaid diagrams, such as:
- GitHub
- GitLab
- VS Code with Mermaid extension
- Mermaid Live Editor (https://mermaid.live)

## Source Files

The diagrams are generated from the following RAC test files:
- `rac/tests/motion-status.test.rac.yaml`
- `rac/tests/security-requirements.test.rac.yaml` 