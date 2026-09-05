---
Topic: npm
Description: npm (Node Package Manager) is the default package manager for Node.js. It lets you install, update, and manage third-party libraries and tools for your project. npm also provides a registry at npmjs.com where developers publish and share their packages.
Resourse:
  - "[npx](https://docs.npmjs.com/cli/v12/commands/npx)"
  - "[Semantic Versioning](https://medium.com/codex/understanding-semantic-versioning-a-guide-for-developers-dad5f2b70583)"
  - "[Global Packages Installing](https://docs.npmjs.com/downloading-and-installing-packages-globally)"
  - "[Local Packages Installing](https://docs.npmjs.com/downloading-and-installing-packages-locally)"
  - "[How to update a package safely](https://chrispennington.dev/blog/how-to-update-npm-packages-safely-with-npm-check-updates/)"
  - "[Running Scripts](https://riptutorial.com/node-js/example/4592/running-scripts)"
  - "[Workspaces](https://docs.npmjs.com/cli/v12/using-npm/workspaces)"
Content:
  - "[[#npx]]"
  - "[[#Semantic Versioning]]"
  - "[[#Installing Packages]]"
  - "[[#Updating Packages]]"
  - "[[#Running Scripts]]"
  - "[[#npm workspaces]]"
Extra Resources:
  - "[NPM Documentation](https://docs.npmjs.com/)"
  - "[What is npm?](https://nodejs.org/en/learn/getting-started/an-introduction-to-the-npm-package-manager)"
  - "[An introduction to the npm package manager](https://nodejs.org/en/learn/getting-started/an-introduction-to-the-npm-package-manager)"
Authors:
  - "[Igor Venturelli](https://medium.com/@igventurelli)"
  - "[Chris Pennington](https://chrispennington.dev/)"
---
# npx
## 1. What is `npx`?

Runs a command from an npm package — **local** or **remote** — in a context similar to `npm run`.

---

## 2. Syntax Forms

| Form                                         | Example                                              |
| -------------------------------------------- | ---------------------------------------------------- |
| Run a package's binary                       | `npx <pkg>[@<version>] [args...]`                    |
| Run a specific package + custom command      | `npx --package=<pkg>[@<version>] -- <cmd> [args...]` |
| Run a shell command/script                   | `npx -c '<cmd> [args...]'`                           |
| Run a shell command with a package available | `npx --package=foo -c '<cmd> [args...]'`             |

> ⚠️ Args after the package name go to the **executed command**, not to npx itself. E.g. `npx create-react-app my-app --template typescript` → `my-app --template typescript` are passed to `create-react-app`.

---

## 3. The `--package` Option

- Puts the specified package(s) on the `PATH` of the executed command (alongside locally installed executables).
- Can be given **multiple times** → makes several packages available at once.
- Used when you want to run a binary that is **not** the same name as the package (bypasses name-inference).

---

## 4. Installation Behavior

| Scenario                                 | What Happens                                                            |
| ---------------------------------------- | ----------------------------------------------------------------------- |
| Package missing from local project deps  | Installed into the **npm cache**, added to `PATH` for that run          |
| Package name given **without** a version | Matches whatever version is already in the local project                |
| Package name given **with** a version    | Only matches if name **and** version match the local dependency exactly |
| Installing a missing package             | Prompts for confirmation (suppress with `--yes` or `--no`)              |

---

## 5. How npx Figures Out Which Binary to Run

Applies when **no `-c`/`--call`** and **no `--package`** is given — npx must infer the executable from the package name:

1. **Single `bin` entry** in `package.json` (or all entries alias the same command) → use it.
2. **Multiple `bin` entries**, one matches the **unscoped package name** → use that one.
3. **Neither condition met** (no bin entries, or none match) → `npm exec` **errors out**.

To skip this inference entirely and run a _different_ binary, pass `--package` explicitly.

---

## 6. `npx` vs `npm exec` — Argument Parsing

||`npx`|`npm exec`|
|---|---|---|
|Flag/option placement|Must come **before** positional args|Parses flags first regardless of position|
|Stopping option-parsing|Not needed the same way|Use `--` to stop npm from parsing further flags|

### Side-by-side example

```bash
# npx: --package is AFTER the positional arg → treated as arg to foo
npx foo@latest bar --package=@npmcli/foo
# → runs: foo bar --package=@npmcli/foo

# npm exec: --package is parsed by npm FIRST → resolves @npmcli/foo package
npm exec foo@latest bar --package=@npmcli/foo
# → runs: foo@latest bar   (in context of @npmcli/foo)
```

Use `--` with `npm exec` to make it behave like the `npx` version:

```bash
npm exec -- foo@latest bar --package=@npmcli/foo
```

---

## 7. Practical Examples

| Goal                                             | Command                                                                                 |
| ------------------------------------------------ | --------------------------------------------------------------------------------------- |
| Run local `tap` with args                        | `npx tap --bail test/foo.js` ≡ `npm exec -- tap --bail test/foo.js`                     |
| Run a binary different from package name         | `npx --package=foo bar --bar-argument` ≡ `npm exec --package=foo -- bar --bar-argument` |
| Run an arbitrary shell script in project context | `npx -c 'eslint && say "hooray, lint passed"'` ≡ `npm x -c '...'`                       |

---
# Semantic Versioning
## What is Semantic Versioning?

Semantic Versioning, often abbreviated as SemVer, is a versioning scheme designed to convey meaning about the underlying changes in a release. As defined on [semver.org](https://semver.org/), it uses a three-part version number: `MAJOR.MINOR.PATCH`. This format not only makes version numbers more informative but also sets clear expectations about the impact of each new version.

## Why Do We Need Semantic Versioning?

In software development, changes are inevitable. Whether it’s fixing bugs, adding new features, or making breaking changes, developers need a reliable way to communicate these updates. Semantic Versioning provides a standardized method to:

1. **Communicate Changes**: Users can immediately understand the nature of the updates by looking at the version number.
2. **Manage Dependencies**: Other software that relies on your code can handle updates more intelligently, reducing the risk of compatibility issues.
3. **Ensure Stability**: By following SemVer, developers can make intentional decisions about when and how to introduce breaking changes, ensuring a more stable and predictable development process.

## Breaking Down the Version Numbers

Semantic Versioning comprises three numbers separated by dots: `MAJOR.MINOR.PATCH`.

1. **MAJOR**: Incremented for incompatible API changes.
2. **MINOR**: Incremented for adding functionality in a backwards-compatible manner.
3. **PATCH**: Incremented for backwards-compatible bug fixes.

## Understanding Patches, Features, and Major Changes

- **Patch**: A patch version (e.g., 1.0.1 -> 1.0.2) includes minor bug fixes that do not affect the software’s functionality or API. For instance, if a small bug in the user interface is fixed without altering any external behavior, the patch number is incremented.
- **Feature**: A minor version (e.g., 1.1.0 -> 1.2.0) includes new features or improvements that are backwards-compatible. Adding a new method to an API, enhancing performance, or introducing optional configurations without breaking existing functionality would warrant a minor version bump.
- **Major Change**: A major version (e.g., 1.0.0 -> 2.0.0) includes changes that break backwards compatibility. This could be removing a deprecated feature, restructuring the codebase, or making significant changes to the API that require users to modify their code to upgrade.

## When to Change the Major Version

Changing the major version signals a significant shift. You should increment the major version when:

- **Breaking Changes**: Introduce changes that are not backwards-compatible.
- **Deprecation**: Remove or alter functionality that existing users depend on.
- **Overhaul**: Make comprehensive changes to the software’s architecture or design that require users to adapt their usage.

## Widespread Use and Adoption

Semantic Versioning is widely adopted across the software industry. From open-source libraries to enterprise-level applications, many developers and organizations rely on SemVer to maintain clarity and consistency in their versioning practices. Popular programming languages, frameworks, and package managers like Node.js (npm), Ruby (Gem), and Python (pip) all adhere to Semantic Versioning principles.

## Examples of Semantic Versioning

Let’s look at a few practical examples:

1. **Initial Release**: `1.0.0` : The first stable release of a software application;
2. **Minor Update**: `1.1.0` : Added a new feature that is backwards-compatible;
3. **Patch Update**: `1.1.1` : Fixed a minor bug that did not affect the overall functionality;
4. **Major Update**: `2.0.0` : Introduced breaking changes that require users to update their implementations;

---
# Installing Packages

## Downloading and installing packages globally

Installing a package globally allows you to use the code in the package as a set of tools on your local computer.

To download and install packages globally, on the command line, run the following command:

`npm install -g <package_name>`

---
## Downloading and installing packages locally

You can install a package locally if you want to depend on the package from your own module, using something like Node.js `require`. This is `npm install`'s default behavior.

### Installing an unscoped package

Unscoped packages are always public, which means they can be searched for, downloaded, and installed by anyone. To install a public package, on the command line, run

`npm install <package_name>`

This will create the `node_modules` directory in your current directory (if one doesn't exist yet) and will download the package to that directory.

**Note:** If there is no `package.json` file in the local directory, the latest version of the package is installed.

If there is a `package.json` file, npm installs the latest version that satisfies the semver ruledeclared in `package.json`.

### Installing a scoped public package

[Scoped public packages](https://docs.npmjs.com/about-scopes) can be downloaded and installed by anyone, as long as the scope name is referenced during installation:

`npm install @scope/package-name`

### Installing a private package

[Private packages](https://docs.npmjs.com/about-private-packages) can only be downloaded and installed by those who have been granted read access to the package. Since private packages are always scoped, you must reference the scope name during installation:

`npm install @scope/private-package-name`

### Testing package installation

To confirm that `npm install` worked correctly, in your module directory, check that a `node_modules` directory exists and that it contains a directory for the package(s) you installed:

`ls node_modules`

### Installed package version

If there is a `package.json` file in the directory in which `npm install` is run, npm installs the latest version of the package that satisfies the [semantic versioning rule](https://docs.npmjs.com/about-semantic-versioning) declared in `package.json`.

If there is no `package.json` file, the latest version of the package is installed.

### Installing a package with dist-tags

Like `npm publish`, `npm install <package_name>` will use the `latest` tag by default.

To override this behavior, use `npm install <package_name>@<tag>`. For example, to install the `example-package` at the version tagged with `beta`, you would run the following command:

`npm install example-package@beta`

---
# Updating Packages

When you come back to an old web dev project, it’s important to update your packages to get new features, bug fixes, and security patches. NPM Check Updates is a CLI that will help you safely make those updates.

## 1. Install NPM Check Updates.

It’s often best to just install NPM check updates globally. (Alternatively, you can run it with NPX.)

```bash
npm install -g npm-check-updates
```

**Note:** [Access the full docs](https://www.npmjs.com/package/npm-check-updates) for NPM Check Updates.

## 2. Run NPM Check Updates.

cd to a directory with your project and run the following command.

```bash
npx ncu
```

This will return a list of packages that need to be updated. Here’s what it looks like:

```bash
[==========================] 15/15 100%
 @notionhq/client   ^0.4.11  →  ^0.4.13 
 node-fetch          ^2.6.6  →   ^3.2.0 
 gulp-autoprefixer   ^7.0.1  →   ^8.0.0 
 gulp-imagemin       ^7.1.0  →   ^8.0.0 
 gulp-sass           ^5.0.0  →   ^5.1.0 
 gulp-terser         ^2.0.1  →   ^2.1.0 
 sass               ^1.35.2  →  ^1.49.7
```

The existing version is on the left and the latest version is on the right. NPU maintains semantic versioning policies, so you can quickly identify patches, minor updates, or major updates that need fixing.

**Note:** In semantic versioning, the number on the right stands for patches (bug fixes), the number in the middle stands for minor versions (new features added in a backwards compatible manner), and major versions (new features added in a breaking manner). So … MAJOR.MINOR.PATCH.

## 3. Update Patches.

First, update all patches. Assuming the package maintainers are following semantic versioning, this shouldn’t break anything.

```bash
npx ncu -u -t patch
```

Run `npm i`, ensure everything is still working, and commit the changes (so u can revert if necessary).

## 4. Update Minor Versions.

Next, update all minor updates. Again, assuming the package maintainers are following semantic versioning, this shouldn’t break anything.

```bash
npx ncu -u -t minor
```

Run `npm i`, ensure everything is still working, and commit the changes (so u can revert if necessary).

## 5. Update Major Versions.

Finally, update all major updates. Before you update these, you should read the release note docs to see how the new version will affect your project. Once you know how the updates will affect your code, update each major change in a separate commit.

With NCU, you can filter for a specific package by using the `--filter` or `-f` flag. So in this case, let’s say I’m starting with node-fetch. I’d type the following command:

```bash
npx ncu -u -f node-fetch
```

Run `npm i`, ensure everything is still working, and commit the changes (so u can revert if necessary).

Then proceed to the next package to the next major version.

---

# Running Scripts

You may define scripts in your `package.json`, for example:

```json
{
  "name": "your-package",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "author": "",
  "license": "ISC",
  "dependencies": {},
  "devDependencies": {},
  "scripts": {
    "echo": "echo hello!"
  }
}

```

To run the `echo` script, run `npm run echo` from the command line. Arbitrary scripts, such as `echo` above, have to be be run with `npm run <script name>`. npm also has a number of official scripts that it runs at certain stages of the package's life (like `preinstall`). 

npm scripts are used most often for things like starting a server, building the project, and running tests. Here's a more realistic example:

```json
  "scripts": {
    "test": "mocha tests",
    "start": "pm2 start index.js"
  }
```

In the `scripts` entries, command-line programs like `mocha` will work when installed either globally or locally. If the command-line entry does not exist in the system PATH, npm will also check your locally installed packages.

If your scripts become very long, they can be split into parts, like this:

```json
  "scripts": {
    "very-complex-command": "npm run chain-1 && npm run chain-2",
    "chain-1": "webpack",
    "chain-2": "node app.js"
  }
```

---
# npm workspaces

## 1. What Are Workspaces?

A set of npm CLI features for managing **multiple packages** from your local filesystem, all under a single **top-level root package**.

- Automates **linking** of local packages as part of `npm install`
- Removes the need to manually run `npm link`
- Each auto-symlinked nested package = **"a workspace"**

---

## 2. Defining a Workspace

Declared via the `"workspaces"` property in the **root** `package.json`:

```json
{
  "name": "my-workspaces-powered-project",
  "workspaces": ["packages/a"]
}
```

**Before `npm install`:**

```json
.
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
```

**After `npm install`:**

```json
.
+-- node_modules
|  `-- a -> ../packages/a      ← symlink created
+-- package-lock.json
+-- package.json
`-- packages
   +-- a
   |   `-- package.json
```

---

## 3. Creating a New Workspace (`npm init`)

```bash
npm init -w ./packages/a
```

This automatically:

1. Creates missing folders
2. Creates a `package.json` for the new workspace (if missing)
3. Updates the **root** `package.json`'s `"workspaces"` property

---

## 4. Adding Dependencies to a Workspace

|Goal|Command|
|---|---|
|Add a **registry** package to workspace `a`|`npm install abbrev -w a`|
|Add workspace `b` as a dependency of workspace `a`|`npm install b -w a`|

### Registry dependency vs. sibling-workspace dependency

||Registry package (e.g. `abbrev`)|Another workspace (e.g. `b`)|
|---|---|---|
|Source|Fetched from npm registry|**Auto-detected** as a workspace|
|Install method|Downloaded|**Symlinked**, not fetched|
|`package.json` entry|Normal version|Standard version range, e.g. `"b": "^1.0.0"`|

> ⚠️ Note: `uninstall`, `ci`, and other install-family commands also **respect** the `-w` workspace config.

---

## 5. Consuming a Workspace in Code

Because of how Node.js resolves `node_modules`, you can `require()` a workspace **by its package name** — same as any npm dependency:

```js
// ./packages/a/index.js
module.exports = 'a'

// ./lib/index.js
const moduleA = require('a')
console.log(moduleA) // -> a
```

Run with:

```bash
node lib/index.js
```

---

## 6. Running Commands in Workspace Context

|Flag|Scope|Example|
|---|---|---|
|`--workspace=<name>`|One specific workspace|`npm run test --workspace=a`|
|`--workspace=<name>` (repeated)|Multiple named workspaces|`npm run test --workspace=a --workspace=b`|
|`--workspace=<folder>`|All workspaces under a folder|`npm run test --workspace=packages`|
|`--workspaces` (plural)|**All** configured workspaces|`npm run test --workspaces`|

Equivalent manual alternative:

```bash
cd packages/a && npm run test
```

> 💡 If your **current directory is inside a workspace**, the workspace config is **implicit**, and `prefix` is set to the root.

### Run order matters

Commands run in the **order workspaces are listed** in the root `package.json`:

```json
{ "workspaces": [ "packages/a", "packages/b" ] }   // a runs before b
```

```json
{ "workspaces": [ "packages/b", "packages/a" ] }   // b runs before a
```

---

## 7. Ignoring Missing Scripts

Not every workspace needs to implement every script. Use `--if-present` to avoid errors:

```bash
npm run test --workspaces --if-present
```

---