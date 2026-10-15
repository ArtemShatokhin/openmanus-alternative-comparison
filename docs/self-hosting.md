# Self-hosting a framework versus self-hosting the platform

Self-hosting OpenManus and self-hosting Kortix are two different jobs with the same name. OpenManus is an open-source Python framework you run on one machine; Kortix is the open-source AI Operating System you run as one stack a whole team shares. Each one asks something different of you and gives something different back.

## What self-hosting OpenManus asks of you

OpenManus runs on a Python environment you prepare yourself. Its repository documents the steps: create a Python 3.12 environment, clone the repo, install the requirements, copy `config/config.example.toml` to `config/config.toml`, add a model API key, then run `python main.py` ([OpenManus on GitHub](https://github.com/FoundationAgents/OpenManus)). The framework then lives on one box, under one key, in one terminal loop.

That is real freedom and very little system. The framework ships no team governance, no shared memory, no review gate, and no hosted path. Whoever runs it holds the box and the key, and the work ends in the terminal it ran in.

## What self-hosting Kortix gives back

Kortix self-hosts as the whole platform, not a trimmed build. The `kortix self-host` commands install and run the full stack on your own infrastructure ([Kortix docs](https://kortix.com/docs)). A project is a git repo with `kortix.yaml` at its root, and your agents, skills, memory, tools, triggers and connectors are files in it.

The parts a framework leaves to you come already built:

- Per-resource permissions for people and agents. Roles, groups, and an audit trail.
- Approval gates you set. Off until you set them.
- Secrets are encrypted at rest with a key per project, and connector credentials are brokered server-side and never enter the machine.
- Session work reaches `main` through a change request. Merge is default-deny for agents.

You run it on Kortix Cloud, in your VPC, or on your own on-prem network. Self-host is free.

## Where the sessions actually run

One detail changes how you plan the hardware. The control plane runs on your server, and the sessions do not. Each session runs on a cloud sandbox provider, with an isolated Linux sandbox and its own branch, and the sandbox calls back to your instance's public API over the network. The instance has to be reachable for that callback, so plan a domain or a tunnel and a machine with a public address.

On the framework side there is no such split. OpenManus runs where you started it, and the machine that runs the agent is also the machine you maintain.

## Which one to run

Self-host the framework while one person is prototyping and the box and the key can live on one desk. The setup is short, and you control every part of it.

Self-host the platform when several people share the agents, when review has to leave a trail, and when the configuration has to outlast the person who set it up. That is the point where self-hosting the platform makes sense, and it is the path we recommend for a team.

You can run both. Keep OpenManus for the experiments, and run Kortix for the work that has to belong to more than one person. In this repo, the [head-to-head with OpenManus](kortix-vs-openmanus.md) and the [FAQ](faq.md) cover the next questions, and the site's [self-hosting guide](https://openmanusalternative.com/self-hosting-openmanus-alternatives) has the install in full.
