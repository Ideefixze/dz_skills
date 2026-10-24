---
name: dz-boilerplate
description: Scaffolding for new projects. Covers stack choice, folder layout, repository artifacts, CI, tests, tooling, docs, and finding libraries before writing code. Use when starting a project, adding standard files, or picking a technology.
---

# dz-boilerplate

Everything before the first feature, stack choice, repository files, tooling, and library search.

You write boilerplate once and live with it for a long time. Keep it small, boring, and complete enough that a fresh clone installs, tests, and runs without extra thought.

## When to use

Use when starting a project, or when an existing project is missing standard files and tooling.

- New project from an empty folder.
- Choosing a language, framework, storage, or deploy target.
- Adding README, .gitignore, CI, tests, linters, editor config, or docs.
- Looking for a library before writing one.

Do not use for feature work inside an established project. Use dz-new-feature.

## Instructions

Use following pattern:

1. Interview.
2. Scaffold.
3. Skill.
4. Verify

## Determine the goal

Try to ask user, using INTERVIEW flow, for what they want to achieve. Determine scope, needs and complexity. Determine what prefabrictes: libraries, packages, AI models, design patterns, opimizations, algorithms, data storage and frameworks user will need.

For each need try to find at least 2 - 5 suggestions on what to use, based on user need.
Try to propose modern, supported and well maintained and safe options, easy to use and effective.
**CRITICAL:** Usually, those projects are meant to be developed by one person, with slight AI assistant help, not for enterprise, large team usage.

Additional questions for the interview that **YOU ALWAYS ASK**:
1. What extra skills you want to create? (**Suggest at least 5 examples for user to go with**)
2. Do you want me to research deeply if there are already projects/frameworks/libraries that help you solve your problems?
3. Do you want me to add some simple classes to help you start your project, or just empty scaffolds?
4. Do you need me to give you tips how to make this project clean and maintainable?
5. What design system / UI style / interaction / visuals you need me to set up for you?

## Create Scaffolding

The most important step for you to follow.
Artifacts needed to kick-start a new personal project:

0. **CRITICAL:** .gitignore, separate virtual env (if python), git repository initialized
1. Folder structure: use proper naming for the used language/framework. Keep structure sensible. Think **big**!
2. Initial framework (if any) setup: `npx ... init` might be needed to run. Install needed requirements for python.
3. Short README.md: what, how, why and small guide to set up and run project. ALWAYS UP TO DATE.
4. CI/CD pipelines (if needed) and .env control
5. Docs generation (or Swagger if API is involved)
6. Link/Checks/Test setup and running
7. .vscode settings to run project from Visual Code
8. Changelog control
9. Docker images (if needed)


## Create skillsets

If project involves some specialistic knowledge or is complex enough, it is worth to implement AI assistant skills just for that project.
Focus on making specialistic skills that will simplify some workflows or repeating patterns. Those skills should be short, concise, effective and single-goal oriented.

Example:
User wants to make an application with an API access. 
A special skills that would be needed:

skills/test-endpoints -> `skill that describes how to setup a mock test environment endpoints and how to run a curl requests to check if new feature works fine on dev, each curl needs also analysis how long it takes to process one request etc.`

skills/before-release -> `skill that describes shortly what needs to happen before the release, what needs to be checked and what to do, all action is user confirmed`

skills/render-mockups -> `skill that generates a simple https://www.remotion.dev/ video mockups to create presentable gifs that visualize what my project does`

## Verify the scaffold

This last step is easy one.
Just **CAREFULLY** check you have everything created and following the guide you made, try to simply deploy the app and check if all components are working fine.