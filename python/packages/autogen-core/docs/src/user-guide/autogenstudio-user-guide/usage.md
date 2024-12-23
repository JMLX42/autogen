---
myst:
  html_meta:
    "description lang=en": |
      Usage for AutoGen Studio - A low code tool for building and debugging multi-agent systems
---

# Usage

The expected usage behavior is that developers use the provided Team Builder interface to to define teams - create agents, attach tools and models to agents, and define termination conditions. Once the team is defined, users can run the team in the Playground to interact with the team to accomplish tasks.

![AutoGen Studio](https://media.githubusercontent.com/media/microsoft/autogen/refs/heads/main/python/packages/autogen-studio/docs/ags_screen.png)

## Building an Agent Team

AutoGen Studio is tied very closely with all of the component abstractions provided by AutoGen AgentChat. This includes - {py:class}`~autogen_agentchat.teams`, {py:class}`~autogen_agentchat.agents`, {py:class}`~autogen_core.models`, {py:class}`~autogen_core.tools`, {py:class}`~autogen_agentchat.conditions`.

Users can define these components in the Team Builder interface either via a declarative specification or by dragging and dropping components from a component library.

## Testing an Agent Team

AutoGen Studio Playground allows users to interactively test teams on tasks and review resulting artifacts (such as images, code, and documents).

Users can also review the “inner monologue” of team as they address tasks, and view profiling information such as costs associated with the run (such as number of turns, number of tokens etc.), and agent actions (such as whether tools were called and the outcomes of code execution).

## Importing and Reusing Team Configurations

AutoGen Studio provides a Gallery view where users can import components from 3rd party community sources. This allows users to reuse and share team configurations with others.

- Gallery -> New Gallery -> Import
- Set as default gallery
- Reuse components in Team Builder

### Using AutoGen Studio Teams in a Python Application

An exported team can be easily integrated into any Python application using the `TeamManager` class with just two lines of code. Underneath, the `TeamManager` rehydrates the workflow specification into AutoGen agents that are subsequently used to address tasks.

```python

from autogenstudio.teammanager import TeamManager

tm = TeamManager()
result_stream =  tm.run(task="What is the weather in New York?", team_config="team.json") # or wm.run_stream(..)

```

<!-- ### Deploying AutoGen Studio Teams as APIs

The team can be launched as an API endpoint from the command line using the autogenstudio commandline tool.

```bash
autogenstudio serve --workflow=workflow.json --port=5000
```

Similarly, the workflow launch command above can be wrapped into a Dockerfile that can be deployed on cloud services like Azure Container Apps or Azure Web Apps. -->
