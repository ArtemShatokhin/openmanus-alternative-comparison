# OpenManus FAQ

OpenManus is an open-source Python framework for building general AI agents, and Kortix is the open-source AI Operating System a team runs when the work has to belong to more than one person. Each answer stands on its own and points at the source it came from.

## What is OpenManus?

OpenManus is a Python framework for building general AI agents. Its own project site describes it as "an open-source framework for building general AI agents" with flexible agent behavior and external tool and API connections ([openmanus.github.io](https://openmanus.github.io/)). Its repository carries 58,662 stars and a last push on 2026-09-30 (checked October 2026, [OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). It gives you the parts to build agents, and you assemble the product around them.

## Is OpenManus free to run?

OpenManus itself is free to install and run, and you can read and fork its code ([OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). The cost that remains is the model API you point it at: you copy `config/config.example.toml` to `config/config.toml` and replace the placeholder key with your own. Your bill is the model usage and the machine the agent runs on, not a subscription to OpenManus.

## Is OpenManus still maintained?

Yes. Its repository was last pushed on 2026-09-30 and carries 58,662 stars (checked October 2026, [OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). Contributors from MetaGPT built it, and the project also runs OpenManus-RL for reinforcement-learning tuning of agents. Because it is a community project, its pace follows those contributors.

## Does OpenManus ship a review step before an agent's work counts?

No. OpenManus is a framework, and its repository documents a running agent and no approval gate ([OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). The agent's output returns to the terminal you started it in, and you decide what to do with it. A gate before a change is real is a platform feature, and Kortix ships one: session work reaches `main` through a change request. Merge is default-deny for agents.

## How does OpenManus run browser automation?

OpenManus starts Browser Use as a default MCP server when it runs, so the agent receives the Browser Use skill and the `browser_exec` and `browser_screenshot` tools ([OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). In local mode it attaches to Chrome or Chromium and needs no API key; you can also authenticate a Browser Use Cloud browser or disable the server with `OPENMANUS_DISABLE_BROWSER_USE=1`. The browser runs on the machine you started OpenManus on.

## What does Kortix add around the agents?

Kortix is the open-source AI Operating System: your agents, their skills, your company memory, and every connector live in one git repo you own, with the agents working on real cloud computers. Each session runs on its own isolated Linux sandbox and its own branch, and session work reaches `main` through a change request ([Kortix docs](https://kortix.com/docs)). Connectors reach 3,000+ apps in a click, plus MCP, OpenAPI, Postman, GraphQL and raw HTTP. Run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free.

## Can I run OpenManus and Kortix together?

Yes. OpenManus runs on the machine you started it on, so a laptop agent keeps working. Kortix can take over a job when it needs a shared repo, memory that outlives a session, or a review gate, and you can point it at the same model providers with your own keys. The two do not conflict, because they run in different places.

## Which models can Kortix use?

Any model provider with your own keys, or the ChatGPT plan you already pay for, or sign in with your OpenCode Console account for OpenCode Zen and Go ([Kortix docs](https://kortix.com/docs)). You pick the model per agent, per session or per message, so a framework's `config.toml` choice becomes a per-session setting.

For the wider field, the [OpenManus alternatives guide](https://openmanusalternative.com/openmanus-alternatives) sets each option beside Kortix. In this repo, the [head-to-head with OpenManus](kortix-vs-openmanus.md) and the [self-hosting comparison](self-hosting.md) take the decision further.
