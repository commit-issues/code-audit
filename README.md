# Code & Security Audit

[![License: CC BY-NC-SA 4.0](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc-sa/4.0/)
![Language: Python](https://img.shields.io/badge/language-Python-3776AB?logo=python&logoColor=white)
![Topic: Security](https://img.shields.io/badge/topic-security-red)
![Topic: Clean Code](https://img.shields.io/badge/topic-clean--code-green)

> *Your code runs. That doesn't mean it's clean, secure, or yours to defend.*

Stop shipping AI slop. A 9-step code quality & security audit pipeline for every file, every time — before it touches main. Star it. You'll want it later.

⭐ **Star it now. Your 2am self will thank you.**

---

**SudoCode by SudoChef** · [@sudochef](https://instagram.com/sudochef) · [github.com/commit-issues](https://github.com/commit-issues)

---

## Before You Start

> If your GitHub repository isn't locked down properly, none of this matters. Start with the [**SudoChef Security Posture Guide →**](https://github.com/commit-issues/secure-your-repo) then come back here.

> Already know why clean code matters? [Skip straight to the pipeline →](#the-full-tool-stack). But if you want to understand what you're actually protecting against, keep reading. It's worth it.

> Not using Python? [Jump to audit tools for your language →](#audit-tools-by-language)

---

## Table of Contents

- [Why This Exists](#why-this-exists)
- [The Language Doesn't Matter. The Discipline Does.](#the-language-doesnt-matter-the-discipline-does)
- [What Is Clean Code](#what-is-clean-code-and-why-does-it-matter)
- [AI Slop](#ai-slop--what-it-is-and-why-its-a-problem)
- [Vibe Coding: When It Works and When It Doesn't](#vibe-coding-when-it-works-and-when-it-doesnt)
- [Cybersecurity and Privacy](#cybersecurity-and-privacy-the-part-vibe-coders-skip)
- [The Rule](#the-rule)
- [The Full Tool Stack](#the-full-tool-stack)
- [Quick Reference](#quick-reference)
- [The Commit Gate](#the-commit-gate)
- [Audit Tools by Language](#audit-tools-by-language)
- [License](#license)

---

## Why This Exists

Most people don't audit their code. They write it, run it, and if it doesn't crash, they push it. That works — until it doesn't. Until someone reads your codebase and immediately knows it was AI-generated. Until a vulnerability ships quietly inside a utility function nobody reviewed. Until the whole thing collapses under its own complexity six months later and nobody — including you — can debug it.

This document is the standard applied to every file before it gets committed. Not most files. Not important files. Every file.

---

## The Language Doesn't Matter. The Discipline Does.

The tools in this guide are Python-based. That's not arbitrary. It's taught at universities, required at major companies, and serves as the entry point for most people learning to code today — data science, security tooling, automation, backend services, AI pipelines. It's everywhere. And yes, the purists will tell you it's bloated, slow, and imprecise. They're not entirely wrong. But that argument misses the point entirely.

**The point is this: no matter what language you write in, you must audit your code.**

Clean code, security scanning, type safety, and complexity management are not Python problems — they're every language's problem. The specific tools change, per language. The discipline doesn't. Whether you're writing Python, JavaScript, Go, or Rust — audit your code before every push. That is the difference between code that holds up and code that becomes a liability.

Search online or use AI to find the best auditing tools for your specific language and apply the same pipeline.

---

## What Is "Clean Code" and Why Does It Matter?

Clean code is not just code that works. Clean code is code that:

- Does one thing per function and does it clearly
- Uses descriptive names that don't require a comment to explain
- Has consistent formatting that doesn't change based on who wrote it or when
- Contains no dead weight — no unused imports, no commented-out blocks, no variables that do nothing
- Can be read by someone else (or by you, six months later) without a map

**Less is more.** Fewer lines that do more is better than more lines that do less. A 40-line function that handles eight different cases is not clever — it's a maintenance problem waiting to happen. Break it up.

**Spaghetti code** is what you get when structure is an afterthought. Logic that jumps between functions with no clear flow. Side effects buried in methods that look like they do something else. State that changes in three different places for reasons nobody remembers. Spaghetti code works until it doesn't — and when it breaks, it breaks in ways that are almost impossible to trace.

---

## AI Slop — What It Is and Why It's a Problem

AI can generate functional code fast. That's real and useful. But there's a category of output that developers have started calling **AI slop** — and if you're using AI to write code without understanding what it's producing, you're probably shipping it.

AI slop looks like this:

- Functions that are technically correct but do far more than they need to
- Variable names like `result`, `data`, `temp`, `x` that carry no meaning
- Repeated logic across files instead of shared utilities
- Missing error handling because the happy path was all that was demonstrated
- Security patterns that look fine on the surface but have known vulnerabilities underneath
- Excessive nesting and complexity because the model didn't refactor, it just solved
- No tests, because tests weren't asked for

The problem isn't that AI wrote it. The problem is that **nobody read it**. AI is a tool and a learning accelerator — not a replacement for understanding your own codebase. When something breaks in production at 2am, the AI is not on call. You are.

Anyone experienced enough to review your code will recognize AI slop immediately. It has a texture. It reads like no one was home when it was written. And in professional settings, in acquisitions, in security audits, in contract work — that matters.

---

## Vibe Coding: When It Works and When It Doesn't

Vibe coding — using AI to build fast, iteratively, without a formal spec — is a legitimate approach for the right kinds of projects. The key word is *right*.

**Where vibe coding works well:**

- Simple SaaS tools with straightforward CRUD operations
- Internal dashboards and admin panels
- Proof-of-concept web apps you're using to learn
- Landing pages and marketing sites
- Personal automation scripts
- Prototypes you're showing to stakeholders, not deploying to users

**Where vibe coding will hurt you:**

- Anything handling real user data — especially authentication, payments, or personal information
- APIs that other services depend on
- Security tooling
- Healthcare, legal, or financial applications
- Anything that will scale — complexity compounds fast
- Open source tools other people will run on their machines

The line is **consequence**. Low consequence, low stakes, fast iteration — vibe coding is fine. High consequence, real users, real data, real liability — you need to understand every line.

Build while you learn. Use AI to understand patterns, not just produce output. The developers who will thrive are the ones who use AI to go faster *and* understand what they're building. Not one or the other.

---

## Cybersecurity and Privacy: The Part Vibe Coders Skip

If your project touches users — any users — you have legal and ethical obligations that don't care how fast you shipped it.

**Privacy law is not optional.** A few things every developer building anything web-facing needs to know:

**CCPA (California Consumer Privacy Act)** — If your app or site has users in California, this applies to you. It governs how you collect, store, and share personal data. California has over 39 million people. If your app is public, you almost certainly have California users.

**GDPR (General Data Protection Regulation)** — The European Union's privacy framework. If your product is accessible globally — and most web apps are — GDPR applies. Data minimization, right to deletion, explicit consent, breach notification requirements. GDPR fines are not small. Businesses have been fined hundreds of millions of euros for violations. "I didn't know" is not a defense.

**The rule of thumb:** If you're collecting an email address, you're in scope. If you're storing any user behavior, you're in scope. If you have accounts, you're in scope. Build privacy in from the start — it is significantly harder to retrofit after the fact than to do right initially.

**Vibe hackers are real.** AI has lowered the bar for writing attack scripts the same way it's lowered the bar for building apps. People who couldn't write a working exploit in 2020 can generate one now in thirty seconds. Automated scanners, credential stuffers, API abuse scripts, SQL injection payloads — these are running against public-facing apps constantly, at scale, looking for exactly the gaps that unaudited AI-generated code tends to leave open.

You have to use AI to fight the misuse of AI. That means scanning your own code (Step 4 of this guide), auditing your dependencies, locking down your repository, and understanding what your app does and doesn't expose. Security is not a feature you add at the end. It is the foundation everything else is built on.

---

## The Rule

Every file goes through this cycle in this exact order. If you skip a step because the change seemed small, that's exactly when something slips through. No committing without a clean run. One bad habit breaks the whole pipeline.

---

## The Full Tool Stack

### Step 1 — Backup

```bash
cp src/file.py src/file.py.bak
```

Before you touch anything, back it up. If something breaks mid-audit, you restore instantly — one command, no lost work, no debugging a half-edited file at 2am.

---

### Step 2 — ruff

```bash
ruff check src/file.py
```

**What it does:** ruff is a fast Python linter written in Rust. It catches style violations, unused imports, shadowed variables, bad formatting patterns, and a range of logic issues — in milliseconds. It covers most of what flake8 does and more, with significantly better performance.

**Why it goes first:** ruff identifies the fastest, cleanest wins. Get these out of the way before the heavier tools run. A file full of unused imports and style noise makes every other tool's output harder to read.

---

### Step 3 — black

```bash
black --check src/file.py   # Preview what will change
black --diff src/file.py    # See the exact line-by-line diff
black src/file.py           # Apply formatting
```

**What it does:** black is an opinionated, zero-config Python formatter. It enforces one consistent style across the entire codebase — line length, spacing, string quotes, trailing commas. You don't argue with black. It just formats.

**Always check before applying** so you know exactly what's changing. The `--diff` flag is especially useful in code review contexts.

**⚠️ Important:** black and pylint sometimes conflict. black wraps long lines in ways pylint flags as style violations. Always re-run pylint after black to catch anything that slipped through.

---

### Step 4 — bandit

```bash
bandit src/file.py -f txt
```

**What it does:** bandit is a static security analysis tool for Python. It scans your code for known vulnerability patterns and reports findings by severity (High / Medium / Low) and confidence level.

**How to act on results:**
- **High severity** — Fix before pushing. No exceptions.
- **Medium severity** — Review every finding. Understand it before dismissing it.
- **Low severity** — Candidates for `# nosec` annotation *only* if the finding is genuinely intentional and understood.

Never silence a warning you don't understand. That's how vulnerabilities ship.

---

### Step 5 — mypy

```bash
mypy src/file.py --ignore-missing-imports
```

**What it does:** mypy is a static type checker for Python. It enforces type annotations and catches type mismatches before they become runtime bugs — things like passing a string where an integer is expected, or calling a method that doesn't exist on a given type.

**`--ignore-missing-imports`** prevents false positives on third-party libraries that don't ship type stubs. Without this flag, mypy will throw errors on perfectly valid imports from libraries that simply haven't annotated their code yet.

Type safety is documentation that the interpreter enforces. Write it.

---

### Step 6 — pylint

```bash
pylint src/file.py --output-format=text
```

**What it does:** pylint performs deep static analysis of your Python code. It scores your file out of 10.00 and catches everything from missing docstrings and naming violations to architectural complexity issues and shadowed variables.

**Target: 9.5 or above.**

A fake 10.00 with silenced warnings is worse than an honest 9.3. The score exists to surface real problems, not to be gamed. If you're suppressing warnings, document why.

Remember: if you ran black in Step 3, run pylint *after* black, not before. Black's line-wrapping can introduce pylint warnings that weren't there before.

---

### Step 7 — pytest

```bash
python3 -m pytest tests/ -v
```

**The rule:** All tests must pass before every commit. No exceptions.

If tests fail, you do not commit. You fix the failure, re-run the full audit from the top, and then commit. A green test suite is the minimum bar for production code — not the ceiling.

If you're adding new functionality, write the tests for it before you consider the work done.

---

### Step 8 — vulture

```bash
vulture src/file.py
```

**What it does:** vulture detects dead code — unused functions, variables, imports, and class attributes. It uses a 60% confidence threshold by default, which means it surfaces probable dead code rather than only certainties.

**How to interpret results:** Treat vulture findings as investigative leads, not verdicts. Public API functions in utility modules will always show as "unused" because vulture only analyzes the file you give it — it cannot see cross-file calls. Use judgment. If something is genuinely unused, remove it. If it's a public interface, note it and move on.

Dead code is technical debt with a heartbeat. Remove it before it causes confusion.

---

### Step 9 — radon

```bash
radon cc src/file.py -s
```

**What it does:** radon measures cyclomatic complexity — the number of independent code paths through a function. It grades each function from A (simple) through F (extremely complex).

**How to act on results:**

| Grade | Complexity | Action |
|-------|------------|--------|
| A | 1–5 | Good. Leave it. |
| B | 6–10 | Acceptable. Monitor. |
| C | 11–15 | Worth examining. Schedule a refactor. |
| D | 16–20 | Needs refactoring. |
| F | 21+ | Refactor before it spreads. |

High complexity is a maintenance liability. A function with 25 code paths is a function that's nearly impossible to test completely and nearly impossible to debug confidently. Break it up.

---

## Quick Reference

| Step | Tool | Purpose |
|------|------|---------|
| 1 | `cp` | Backup before anything |
| 2 | `ruff` | Fast lint — style, imports, logic |
| 3 | `black` | Consistent formatting |
| 4 | `bandit` | Security vulnerability scan |
| 5 | `mypy` | Static type checking |
| 6 | `pylint` | Deep code analysis, score out of 10 |
| 7 | `pytest` | All tests must pass |
| 8 | `vulture` | Dead code detection |
| 9 | `radon` | Cyclomatic complexity grading |

---

## The Commit Gate

Before any commit, the following must all be true:

- [ ] ruff — zero warnings
- [ ] black — formatting applied and clean
- [ ] bandit — zero High severity findings
- [ ] mypy — no type errors
- [ ] pylint — 9.5 or above
- [ ] pytest — all tests passing
- [ ] vulture — dead code reviewed and addressed
- [ ] radon — no F grades (D grades documented for refactor)

If any item on this list is not met, the commit does not happen.

---

## Audit Tools by Language

Python is the focus of this guide — but the discipline applies everywhere. Below are the top languages used in development and in security, with the tools you should be running and what to watch for in each.

---

**Python**

Python is the #1 most widely used programming language in the world and the foundation of this guide. It's used for malware scripts, exploit frameworks (Metasploit modules), automation attacks, and more. The full audit pipeline is documented above.

---

**1. JavaScript / Node.js**

The language of the web — and the language of most web vulnerabilities. XSS, prototype pollution, insecure deserialization, and supply chain attacks through npm packages are all JavaScript problems. Audit tools: `eslint`, `semgrep`, `npm audit`. Watch for: unvalidated input, dangerous use of `eval()`, and dependency bloat.

---

**2. C**

The language systems are built on — and the language exploits are written in. Memory corruption, buffer overflows, and shellcode all live here. There is no runtime safety net. Audit tools: `cppcheck`, `valgrind`, `clang-tidy`. Watch for: unsafe memory functions like `strcpy`, `gets`, and `sprintf`, and anything touching raw pointers.

---

**3. C++**

Everything C can do, with more complexity and more surface area. Rootkits, ransomware, and reverse engineering targets are frequently C++. Audit tools: `cppcheck`, `clang-tidy`, `AddressSanitizer`. Watch for: use-after-free, uninitialized variables, and unsafe casting.

---

**4. Java**

The enterprise backend language. Deserialization vulnerabilities are Java's most dangerous attack surface — Log4Shell lived here and took down half the internet. Audit tools: `SpotBugs`, `SonarQube`, `OWASP Dependency-Check`. Watch for: unsafe deserialization, outdated dependencies, and overly permissive class loading.

---

**5. Go**

Fast, modern, and increasingly the language of choice for cloud tooling — and for next-generation malware. Cobalt Strike alternatives and C2 frameworks are being written in Go specifically because it compiles to a single binary and antivirus struggles with it. Audit tools: `golangci-lint`, `gosec`. Watch for: improper error handling (Go makes it easy to silently ignore errors) and hardcoded credentials.

---

**6. Rust**

Built for memory safety — and increasingly showing up in both security tooling and malware for the same reason. AV struggles to analyze Rust binaries. Audit tools: `clippy`, `cargo audit`. Watch for: unsafe blocks, which opt out of Rust's safety guarantees entirely, and dependency vulnerabilities in `Cargo.lock`.

---

**7. C#**

The Windows ecosystem language. Heavily used in enterprise software and increasingly in offensive security tooling — SharpHound, Covenant C2, and a long list of red team utilities are written in C#. Audit tools: `Roslyn analyzers`, `SonarQube`, `OWASP Dependency-Check`. Watch for: insecure deserialization, SQL injection in Entity Framework queries, and unsafe reflection.

---

**8. Ruby**

The language Rails is built on — and the language Metasploit is written in. If you're doing web app security or writing Metasploit modules, you're reading Ruby. Audit tools: `RuboCop`, `Brakeman`, `bundler-audit`. Watch for: mass assignment vulnerabilities, SQL injection in ActiveRecord, and outdated gems.

---

**9. PHP**

Legacy web but still powering a massive chunk of the internet. Webshells are almost always PHP. If you're doing web pentesting, you will encounter PHP. Audit tools: `PHPStan`, `Psalm`, `RIPS`. Watch for: `eval()` usage, unsanitized `$_GET`/`$_POST` input, and file inclusion vulnerabilities.

---

**10. Assembly (x86/x64)**

Not a language most people build in — but since I'm into cybersecurity, this one had to be on the list. Assembly is the language of shellcode, reverse engineering, and malware analysis. When you're analyzing a binary, reading a CVE exploit, or writing your own shellcode, you're reading Assembly. You don't audit Assembly the way you audit Python — but you need to be able to read it. Tools: `Ghidra`, `IDA Free`, `Binary Ninja`. Know what you're looking at when the debugger opens.

---

## Found This Useful?

If this guide saves you time, catches a bug, or makes your codebase something you're proud of — **star this repo** ⭐. It keeps it at the top of your GitHub for quick access and helps other developers find it.

---

## License

This work is licensed under [Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)](https://creativecommons.org/licenses/by-nc-sa/4.0/).

You are free to share and adapt this material for non-commercial purposes as long as you give appropriate credit and distribute any adaptations under the same license.

---

*SudoCode by SudoChef (commit-issues)*
