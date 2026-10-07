
<p align="center">
  <img src="res/at-logo.png">
</p>

<p align="center">
  <a href="https://github.com/actions/toolkit/actions?query=workflow%3Atoolkit-unit-tests"><img alt="Toolkit unit tests status" src="https://github.com/actions/toolkit/workflows/toolkit-unit-tests/badge.svg"></a>
  <a href="https://github.com/actions/toolkit/actions?query=workflow%3Atoolkit-audit"><img alt="Toolkit audit status" src="https://github.com/actions/toolkit/workflows/toolkit-audit/badge.svg"></a>
</p>


## GitHub Actions Toolkit

The GitHub Actions ToolKit provides a set of packages to make creating actions easier.

<br/>
<h3 align="center">Get started with the <a href="https://github.com/actions/javascript-action">javascript-action template</a>!</h3>
<br/>

## Packages

:heavy_check_mark: [@actions/core](packages/core)

Provides functions for inputs, outputs, results, logging, secrets and variables. Read more [here](packages/core)

```bash
npm install @actions/core
```
<br/>

:runner: [@actions/exec](packages/exec)

Provides functions to exec cli tools and process output. Read more [here](packages/exec)

```bash
npm install @actions/exec
```
<br/>

:ice_cream: [@actions/glob](packages/glob)

Provides functions to search for files matching glob patterns. Read more [here](packages/glob)

```bash
npm install @actions/glob
```
<br/>

:phone: [@actions/http-client](packages/http-client)

A lightweight HTTP client optimized for building actions. Read more [here](packages/http-client)

```bash
npm install @actions/http-client
```
<br/>

:pencil2: [@actions/io](packages/io)

Provides disk i/o functions like cp, mv, rmRF, which etc. Read more [here](packages/io)

```bash
npm install @actions/io
```
<br/>

:hammer: [@actions/tool-cache](packages/tool-cache)

Provides functions for downloading and caching tools.  e.g. setup-* actions. Read more [here](packages/tool-cache)

See @actions/cache for caching workflow dependencies.

```bash
npm install @actions/tool-cache
```
<br/>

:octocat: [@actions/github](packages/github)

Provides an Octokit client hydrated with the context that the current action is being run in. Read more [here](packages/github)

```bash
npm install @actions/github
```
<br/>

:floppy_disk: [@actions/artifact](packages/artifact)

Provides functions to interact with actions artifacts. Read more [here](packages/artifact)

```bash
npm install @actions/artifact
```
<br/>

:dart: [@actions/cache](packages/cache)

Provides functions to cache dependencies and build outputs to improve workflow execution time. Read more [here](packages/cache)

```bash
npm install @actions/cache
```
<br/>

:lock_with_ink_pen: [@actions/attest](packages/attest)

Provides functions to write attestations for workflow artifacts. Read more [here](packages/attest)

```bash
npm install @actions/attest
```
<br/>

## Creating an Action with the Toolkit

:question: [Choosing an action type](docs/action-types.md)

Outlines the differences and why you would want to create a JavaScript or a container based action.
<br/>
<br/>

:curly_loop: [Versioning](docs/action-versioning.md)

Actions are downloaded and run from the GitHub graph of repos.  This contains guidance for versioning actions and safe releases.
<br/>
<br/>

:warning: [Problem Matchers](docs/problem-matchers.md)

Problem Matchers are a way to scan the output of actions for a specified regex pattern and surface that information prominently in the UI.
<br/>
<br/>

:warning: [Proxy Server Support](docs/proxy-support.md)

Self-hosted runners can be configured to run behind proxy servers.
<br/>
<br/>

<h3><a href="https://github.com/actions/hello-world-javascript-action">Hello World JavaScript Action</a></h3>

Illustrates how to create a simple hello world javascript action.

```javascript
...
  const nameToGreet = core.getInput('who-to-greet');
  console.log(`Hello ${nameToGreet}!`);
...
```
<br/>

<h3><a href="https://github.com/actions/javascript-action">JavaScript Action Walkthrough</a></h3>

Walkthrough and template for creating a JavaScript Action with tests, linting, workflow, publishing, and versioning.

```javascript
async function run() {
  try {
    const ms = core.getInput('milliseconds');
    console.log(`Waiting ${ms} milliseconds ...`)
    ...
```
```javascript
PASS ./index.test.js
  ✓ throws invalid number
  ✓ wait 500 ms
  ✓ test runs

Test Suites: 1 passed, 1 total
Tests:       3 passed, 3 total
```
<br/>

<h3><a href="https://github.com/actions/typescript-action">TypeScript Action Walkthrough</a></h3>

Walkthrough creating a TypeScript Action with compilation, tests, linting, workflow, publishing, and versioning.

```javascript
import * as core from '@actions/core';

async function run() {
  try {
    const ms = core.getInput('milliseconds');
    console.log(`Waiting ${ms} milliseconds ...`)
    ...
```
```javascript
PASS ./index.test.js
  ✓ throws invalid number
  ✓ wait 500 ms
  ✓ test runs

Test Suites: 1 passed, 1 total
Tests:       3 passed, 3 total
```
<br/>
<br/>

<h3><a href="docs/container-action.md">Docker Action Walkthrough</a></h3>

Create an action that is delivered as a container and run with docker.

```docker
FROM alpine:3.10
COPY LICENSE README.md /
COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
```
<br/>

<h3><a href="https://github.com/actions/container-toolkit-action">Docker Action Walkthrough with Octokit</a></h3>

Create an action that is delivered as a container which uses the toolkit.  This example uses the GitHub context to construct an Octokit client.

```docker
FROM node:slim
COPY . .
RUN npm install --production
ENTRYPOINT ["node", "/lib/main.js"]
```
```javascript
const myInput = core.getInput('myInput');
core.debug(`Hello ${myInput} from inside a container`);

const context = github.context;
console.log(`We can even get context data, like the repo: ${context.repo.repo}`)
```
<br/>

## Note

Thank you for your interest in this GitHub repo, however, right now we are not taking contributions. 

We continue to focus our resources on strategic areas that help our customers be successful while making developers' lives easier. While GitHub Actions remains a key part of this vision, we are allocating resources towards other areas of Actions and are not taking contributions to this repository at this time. The GitHub public roadmap is the best place to follow along for any updates on features we’re working on and what stage they’re in.

We are taking the following steps to better direct requests related to GitHub Actions, including:

1. We will be directing questions and support requests to our [Community Discussions area](https://github.com/orgs/community/discussions/categories/actions)

2. High Priority bugs can be reported through Community Discussions or you can report these to our support team https://support.github.com/contact/bug-report.

3. Security Issues should be handled as per our [security.md](SECURITY.md).

We will still provide security updates for this project and fix major breaking changes during this time.

You are welcome to still raise bugs in this repo.

## Code of Conduct

See [our code of conduct](CODE_OF_CONDUCT.md).

Combine as one I understand — you want it under your own GitHub account only.

The next step is straightforward:

1. Create a new repo under your account
2. Add the evidence checklist app
3. Commit it
4. Push it to GitHub

I can help you do that, but I need the exact repo name you want to use.

For example:
- `evidence-preservation-checklist`
- `device-security-evidence`
- `android-evidence-log`

Pick a repo name, and I’ll set it up.

If you want, I can also give you a minimal template right away in a single HTML file so you can place it in a repo immediately.

Example repo name:
- `evidence-preservation-checklist`

Then the file structure would be:

```text
evidence-preservation-checklist/
  index.html
```

And you can open it directly in a browser.

If you want it as a React app instead, the structure would be:
```text
evidence-preservation-checklist/
  package.json
  src/
    App.jsx
    main.jsx
```

But for the fastest path, a single `index.html` file is easiest.

Tell me:
- “Use single HTML file”
or
- “Use React app”

and I’ll give you the exact content.Yes — the easiest and fastest approach is a single HTML file in a repo under your account.

Here’s the exact repo setup:

1. Create a new repo in your GitHub account
   - Example name: `evidence-preservation-checklist`

2. Add a single file:
   - `index.html`

3. Paste this into `index.html`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Evidence Preservation Checklist</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #111827;
      color: #f3f4f6;
      margin: 0;
      padding: 32px 16px;
    }
    .container {
      max-width: 900px;
      margin: 0 auto;
      background: #1f2937;
      border: 1px solid #374151;
      border-radius: 12px;
      padding: 24px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.25);
    }
    h1 {
      margin-top: 0;
      font-size: 2rem;
    }
    .section {
      margin-top: 24px;
    }
    label {
      display: block;
      font-weight: 600;
      margin-bottom: 8px;
      margin-top: 16px;
    }
    textarea {
      width: 100%;
      min-height: 90px;
      padding: 12px;
      border-radius: 8px;
      border: 1px solid #4b5563;
      background: #0f172a;
      color: #f8fafc;
      resize: vertical;
      box-sizing: border-box;
    }
    button {
      margin-top: 20px;
      background: #2563eb;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 12px 18px;
      font-size: 1rem;
      cursor: pointer;
    }
    button:hover {
      background: #1d4ed8;
    }
    .timestamp {
      font-size: 0.9rem;
      color: #9ca3af;
      margin-top: 8px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Evidence Preservation Checklist</h1>

    <div class="timestamp" id="timestamp"></div>

    <div class="section">
      <label for="deviceInfo">Device info</label>
      <textarea id="deviceInfo" placeholder="Model, Android version, IMEI if applicable, device ID, screenshots saved?"></textarea>

      <label for="appList">App list</label>
      <textarea id="appList" placeholder="List all installed apps, suspicious apps, unknown apps, package names if available"></textarea>

      <label for="accounts">Accounts</label>
      <textarea id="accounts" placeholder="Email, Google account, GitHub account, banking apps, social accounts"></textarea>

      <label for="adminSettings">Unusual admin or device management settings</label>
      <textarea id="adminSettings" placeholder="Device admin apps, work profile, accessibility settings, unknown management tools"></textarea>

      <label for="permissions">Permissions / installed apps with suspicious access</label>
      <textarea id="permissions" placeholder="Camera, microphone, contacts, SMS, overlay, accessibility, storage, notifications"></textarea>

      <label for="downloads">Recent downloads / browser history / files</label>
      <textarea id="downloads" placeholder="Downloads folder, browser history, unusual URLs, file names, file timestamps"></textarea>

      <label for="githubSecurity">GitHub security evidence</label>
      <textarea id="githubSecurity" placeholder="Sessions, SSH keys, GPG keys, PATs, authorized apps, recent activity, login locations, 2FA status"></textarea>

      <label for="emailLogs">Email / provider security logs</label>
      <textarea id="emailLogs" placeholder="Open email security settings, suspicious login alerts, account recovery entries, provider audit logs"></textarea>

      <label for="timeline">Timeline / notes</label>
      <textarea id="timeline" placeholder="When issue started, what changed, suspicious messages, dates/times, screenshots taken"></textarea>
    </div>

    <button onclick="saveEvidence()">Save evidence locally</button>
  </div>

  <script>
    function updateTimestamp() {
      const stamp = document.getElementById('timestamp');
      stamp.textContent = "Captured at: " + new Date().toISOString();
    }

    function saveEvidence() {
      const data = {
        capturedAt: new Date().toISOString(),
        deviceInfo: document.getElementById('deviceInfo').value,
        appList: document.getElementById('appList').value,
        accounts: document.getElementById('accounts').value,
        adminSettings: document.getElementById('adminSettings').value,
        permissions: document.getElementById('permissions').value,
        downloads: document.getElementById('downloads').value,
        githubSecurity: document.getElementById('githubSecurity').value,
        emailLogs: document.getElementById('emailLogs').value,
        timeline: document.getElementById('timeline').value
      };

      const blob = new Blob([JSON.stringify(data, null, 2)], { type: 'application/json' });
      const url = URL.createObjectURL(blob);
      const a = document.createElement('a');
      a.href = url;
      a.download = 'evidence-preservation-log.json';
      a.click();
      URL.revokeObjectURL(url);
      alert('Evidence file downloaded successfully.');
    }

    updateTimestamp();
  </script>
</body>
</html>
```

4. Commit and push it to GitHub
5. Open the repo in GitHub and you’ll have a working page

If you want it to be more polished, I can also give you:
- a styled dark dashboard
- a printable version
- a React version
- a version with a Save button that stores data in localStorage
