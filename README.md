# 🎵 Motion Music Player — RaC Example

A motion-controlled music app prototype created during the Bolt.new hackathon and included as a reference implementation in the RaC white‑papers.

## 🧠 What is RaC?

Requirements as Code (RaC) is a methodology for defining full-stack application behavior using declarative YAML schemas—covering state, events, logic, ui, data, tests, and bindings. The system supports incremental, test-first development and ensures transparency, modularity, and validation-ready architecture.

**🔧 Technology Agnostic**: RaC schemas are completely independent of implementation technology. The same requirements can be bound to React, Vue, Angular, or any other framework. Your business logic and UI definitions remain portable across different tech stacks.

## ⚙️ Project Structure

```
/
├── rac/           # RaC methodology implementation
│   ├── state/         # Application data schema
│   ├── events/        # User/system event definitions
│   ├── logic/         # Behavioural and validation rules
│   ├── ui/            # Abstract UI component definitions
│   ├── schemas/       # RaC schema definitions
│   ├── tests/         # Simulations & validations
│   ├── bindings/      # Technology adapters (Bolt.new, React, etc.)
│   ├── docs/          # Supplementary RaC docs (e.g. security-model)
│   ├── diagrams/      # Flow diagrams and visual documentation
│   ├── get-started.md # Core RaC tooling guide
│   ├── steps.md       # Implementation steps
│   └── reqs.md        # Requirements documentation
└── README.md      # ← You are here
```

## 🚀 Get Started

Follow this sequence to scaffold and build your app with RaC and Bolt.new:

• Start an empty Bolt.new project
  Use the browser-based Bolt.new to create a new project.
  Add the rac/ folder from this repo into it.

• Define app scope via LLM dialogue
  Introduce your app idea to the LLM in Bolt.new.
  Iteratively refine your vision through conversation.

• Generate requirements (reqs.md)
  Ask the LLM to produce a file with functional (e.g., "shake to play") and non-functional (e.g., "UI latency <200 ms") requirements.

• Create implementation plan (steps.md)
  Reference rac/get-started.md and ask the LLM to generate a step-by-step plan. Save output to plan.md.

• Implement RaC structure
  In dialogue, walk through the plan to build YAML files under state/, events/, logic/, ui/, and tests/, wiring bindings accordingly.

• Regular schema verification
  Periodically prompt the LLM to verify your YAML for schema correctness and consistency with requirements.

## 🛠️ Why This Workflow?

• Enables collaborative app definition through LLM interaction

• Structured via RaC: declarative, testable, and technology-agnostic

• Bolt.new acts as a live sandbox, letting you experience the music app in action—without manual boilerplate

## 📌 Example Workflow Summary

| Step | Action | Output |
|------|--------|--------|
| 1 | Import rac/ into Bolt.new | App scaffold in place |
| 2 | Scope refinement via chat | Clear app vision |
| 3 | Generate reqs.md | Requirements documented |
| 4 | Generate plan.md | Implementation roadmap |
| 5 | Build RaC structure | YAML modules + tests |
| 6 | Validate schema periodically via LLM | Consistency & correctness |

This loop of dialogue → generate → implement → verify ensures each feature is well-specified, testable, and connected to requirements.

## 📚 Further Exploration

• Try adding gestures: e.g., double-shake to toggle shuffle.

• Swap bindings: integrate React UI in bindings/ui/.

• Enrich tests: simulate more edge behaviors in tests/.

• Extend bindings: connect to real music APIs via bindings/express/ or similar.

## 🔗 Related Links

• [Bolt.new](https://bolt.new/) – browser-based AI dev platform

• [RaC white‑papers](https://github.com/dimitar-trifonov/rac-white-papers) – theory & reference implementations (includes this repo)

By following this workflow, you'll build a motion-controlled music app that's scoped, specified, and validated—one RaC-defined step at a time.