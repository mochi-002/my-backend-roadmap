---
Content: Node.js
Resources:
- "[What is Node.js?](https://www.youtube.com/watch?v=uVwtVBpw7RQ)"
- "[Why Choose Node.js?](https://medium.com/selleo/why-choose-node-js-b0091ad6c3fc)"
- "[Differences between Node.js and the Browser](https://nodejs.org/learn/getting-started/differences-between-nodejs-and-the-browser)"
- "[Run Node.js scripts from the command line](https://nodejs.org/learn/command-line/run-nodejs-scripts-from-the-command-line#run-nodejs-scripts-from-the-command-line)"
Topics:
- "[[#1. Core Definition]]"
- "[[#2. What Do Back-End Services Do?]]"
- "[[#3. Developer Advantages of Node.js]]"
- "[[#4. Case Study PayPal's Node.js Migration]]"
- "[[#5. Why Choose Node.js? (4 Key Use Cases)]]"
- "[[#6. General Benefits of Node.js]]"
- "[[#7. Node.js vs. The Browser]]"
- "[[#8. Running Node.js Code]]"
- "[[#9. Running Tasks via `package.json` (Built-in Task Runner)]]"
- "[[#Quick-Recall Summary Table]]"
---
## 1. Core Definition

|Aspect|Detail|
|---|---|
|**What it is**|Open-source, cross-platform **runtime environment**|
|**Core function**|Executes JavaScript **outside** the browser|
|**Primary use**|Building back-end services & APIs|
|**Engine**|Built on Chrome's **V8** engine|

> 🧠 **Mnemonic — "RAJ"**: Node.js is a **R**untime that runs JS **A**nywhere, for **J**S-only stacks (front + back).

---

## 2. What Do Back-End Services Do?

Back-end services are the **engine behind client apps** (web/mobile). They run on a server/cloud and handle:

- **S**toring & retrieving data
- **E**mailing (sending emails)
- **N**otifications (push)
- **D**riving workflows (kicking them off)

> 🧠 **Mnemonic — "SEND"**: Store, Email, Notify, Drive workflows.

Node.js is specifically strong for services that are **scalable, data-intensive, and real-time**.

---

## 3. Developer Advantages of Node.js

|Advantage|Why It Matters|
|---|---|
|**Unified stack**|One language (JS) for front-end + back-end — no context switching|
|**Code consistency**|Same naming conventions, tools, best practices across the stack|
|**Huge ecosystem (npm)**|Largest library ecosystem — reuse instead of rebuild|
|**Agility**|Great for rapid prototyping / agile dev|

---

## 4. Case Study: PayPal's Node.js Migration

PayPal rewrote a Java/Spring app in Node.js. Results:

|Metric|Improvement|
|---|---|
|Development speed|2× faster, smaller team|
|Lines of code|33% fewer|
|File count|40% fewer|
|Throughput|2× requests/sec|
|Latency|35% lower avg. response time|

**Other adopters:** Uber, Netflix, Walmart, PayPal.

> ⚠️ Exam angle: This case study is commonly cited as _proof of scalability + productivity gains_, not just performance.

---

## 5. Why Choose Node.js? (4 Key Use Cases)

|#|Use Case|Enabling Feature|
|---|---|---|
|1|**API services**|REST APIs exposing JSON|
|2|**Streaming apps**|Built-in `streams` module → sends data in chunks (music/video without full download)|
|3|**Real-time apps**|Event loop + WebSockets → chat, video calls, collaborative docs (e.g., Google Docs)|
|4|**Microservices**|Small, independently working services|

> 🧠 **Mnemonic — "ASRM"**: **A**PI, **S**treaming, **R**eal-time, **M**icroservices.

---

## 6. General Benefits of Node.js

- Open-source
- Scales **vertically** (add resources to a node) and **horizontally** (add more nodes)
- Enables modular components → cheaper dev, faster time-to-market
- Reusable code between front-end and back-end
- Better performance via V8 engine
- One language (JS) end-to-end
- Rich framework ecosystem: **Express.js, Koa, Nest.js**

---

## 7. Node.js vs. The Browser

Both use JavaScript, but the **ecosystem** differs completely.

|Feature|Browser|Node.js|
|---|---|---|
|DOM / `window`, `document`|✅ Available|❌ Not available|
|Filesystem access|❌ Not available|✅ Available (via modules)|
|Environment control|❌ You don't choose the user's browser|✅ You choose the Node version|
|Modern JS (ES2015+)|⚠️ May need Babel for compatibility|✅ Use directly, no transpiling needed|
|Module systems|Mostly ES Modules (`import`)|Both **CommonJS** (`require()`) and **ES Modules** (`import`, since v12)|

> 🧠 **Mnemonic — "DEEM"**: **D**OM (browser only), **E**nvironment control (Node only), **E**S/CommonJS (Node has both), **M**odern JS without Babel (Node only).

> 💡 **Key exam line**: "What changes is the ecosystem" — same language, different APIs/context.

---

## 8. Running Node.js Code

### 8.1 Basic execution

```bash
node app.js
```

### 8.2 Shebang (make file self-executing)

```js
#!/usr/bin/env node
// your javascript code
```

Then grant execute permission:

```bash
chmod u+x app.js
```

> Why `env` instead of a direct path? Not all systems have `node` at a fixed bin path, but nearly all have `env`.

### 8.3 Run a JS string directly

```bash
node -e "console.log(123)"
```

⚠️ **OS quoting note**: On Windows `cmd.exe`, only `"` works. In PowerShell/Git Bash, both `'` and `"` work.

### 8.4 Auto-restart on file change (`--watch`, Node v16+)

```bash
node --watch app.js
```

---

## 9. Running Tasks via `package.json` (Built-in Task Runner)

### 9.1 The `--run` flag

Given:

```json
{
  "type": "module",
  "scripts": {
    "start": "node app.js",
    "test": "node --test"
  }
}
```

Run it:

```bash
node --run test
```

### 9.2 Passing arguments to the script

```bash
node --run start -- --port 8080
```

Equivalent to: `node app.js --port 8080`

> ⚠️ **Gotcha**: Args after `--` are passed literally to the script — they are **not** parsed as Node CLI flags. E.g., `--watch` here won't behave like `node --watch app.js`.

### 9.3 Environment variables set by `--run`

|Variable|Meaning|
|---|---|
|`NODE_RUN_SCRIPT_NAME`|Name of the script being run|
|`NODE_RUN_PACKAGE_JSON_PATH`|Path to the `package.json` used|

### 9.4 Limitations of Node's built-in runner (vs `npm run` / `yarn run`)

- No `pre`/`post` script hooks
- Simpler & faster, but less feature-rich
- Best for straightforward tasks only

---

## Quick-Recall Summary Table

|Topic|One-Line Takeaway|
|---|---|
|Definition|JS runtime outside the browser, for back-end|
|Strength|Scalable, data-intensive, real-time services|
|Advantage|One language, huge ecosystem (npm)|
|PayPal case|Faster dev, less code, 2× throughput, -35% latency|
|Use cases|API · Streaming · Real-time · Microservices|
|vs Browser|Same language, different ecosystem (no DOM, has FS access, dev controls Node version)|
|Run a file|`node app.js` or shebang + `chmod u+x`|
|Run a script|`node --run <script>` (limited vs npm/yarn)|