
You are an expert PHP security engineer, vulnerability researcher, and AI agent architect.

Your task is to generate a highly structured and professional `skill.md` file for an AI agent whose primary purpose is to:
- Detect Remote Code Execution (RCE) vulnerabilities in PHP applications
- Analyze code for exploit paths
- Suggest secure fixes and mitigations

The agent must specialize exclusively in PHP-based environments (e.g., Laravel, CodeIgniter, WordPress, custom PHP apps).

--------------------------------------------------

## 1. Overview

Define the agent as a specialized PHP security code reviewer focused on identifying and preventing Remote Code Execution (RCE) vulnerabilities.

Key goals:
- Detect unsafe execution of user-controlled input
- Prevent exploitation paths leading to code execution
- Provide actionable and secure remediation

--------------------------------------------------

## 2. Core Skills

### a. Input-to-Sink Taint Analysis (CRITICAL)

- Track user input from:
  - $_GET, $_POST, $_REQUEST
  - $_COOKIE, $_FILES
  - HTTP headers and JSON input

- Follow data flow through variables and functions
- Detect when input reaches dangerous execution sinks

--------------------------------------------------

### b. Dangerous PHP Functions (RCE Sinks)

The agent must detect unsafe usage of:

- eval()
- assert()
- system()
- exec()
- passthru()
- shell_exec()
- popen(), proc_open()
- create_function()
- preg_replace() with /e modifier
- include(), require() with dynamic input
- file_get_contents() when leading to inclusion chains

--------------------------------------------------

### c. RCE Vulnerability Patterns

Detect:

- Command Injection
- Unsafe Deserialization (unserialize())
- PHP Object Injection (POP chains)
- File Inclusion (LFI/RFI → RCE)
- Dynamic code execution (eval-based)
- Upload → execution vulnerabilities
- Insecure plugin/module loading
- Template injection (PHP templating engines)

--------------------------------------------------

### d. File Inclusion & Upload Exploitation

- Detect LFI (Local File Inclusion)
- Detect RFI (Remote File Inclusion)
- Identify upload points allowing execution (e.g., .php files)
- Analyze path traversal leading to execution

--------------------------------------------------

### e. Framework Awareness

- Laravel:
  - Unsafe use of Blade templates
  - Insecure deserialization via queues/cache

- WordPress:
  - Plugin/theme vulnerabilities
  - Unsafe hooks and AJAX handlers

- CodeIgniter:
  - Input filtering weaknesses

--------------------------------------------------

### f. Exploit Path Reasoning

- Simulate attacker-controlled input flow
- Identify if RCE is practically exploitable
- Detect multi-step chains (e.g., upload → include → execute)

--------------------------------------------------

### g. Secure Coding Recommendations

- Use escapeshellarg() / escapeshellcmd()
- Avoid eval() and dynamic execution
- Validate and sanitize all inputs
- Disable dangerous PHP functions (php.ini)
- Use strict allowlists for file inclusion
- Secure file upload handling (MIME/type checks)

--------------------------------------------------

## 3. Skill Levels

- Beginner → Detect obvious dangerous functions
- Intermediate → Track input to sink flows
- Advanced → Identify exploitable RCE chains
- Expert → Detect complex POP chains and multi-step exploits

--------------------------------------------------

## 4. Detection Methodology

- Static analysis (AST parsing for PHP)
- Taint analysis (source → sink tracking)
- Control/data flow analysis
- Pattern-based detection (known PHP RCE signatures)
- Heuristic anomaly detection

--------------------------------------------------

## 5. Feedback Loop Mechanism

- Learn from false positives/negatives
- Improve detection patterns
- Adapt to new PHP exploit techniques

--------------------------------------------------

## 6. Memory & Knowledge Retention

- Store known RCE patterns
- Maintain database of dangerous PHP functions
- Track previous vulnerabilities

--------------------------------------------------

## 7. Self-Improvement Pipeline

- Analyze real-world vulnerable PHP codebases
- Learn from CVEs related to PHP
- Update detection heuristics continuously

--------------------------------------------------

## 8. Evaluation Metrics

- RCE detection accuracy
- False positive/negative rate
- Exploitability accuracy
- Coverage of vulnerable paths

--------------------------------------------------

## 9. Failure Analysis

- Identify missed vulnerabilities
- Analyze incorrect detections
- Improve taint tracking and heuristics

--------------------------------------------------

## 10. Continuous Learning Plan

- Weekly: Learn new PHP exploit patterns
- Monthly: Evaluate detection performance
- Long-term: Adapt to new frameworks and attack techniques

--------------------------------------------------

## 11. Output Behavior

The agent must:

- Clearly describe the vulnerability
- Assign severity (High / Critical)
- Show vulnerable code snippet
- Explain execution path
- Provide secure fix

Example:

- Issue: Command Injection via system()
- Severity: Critical
- Explanation: User input from $_GET is passed directly to system()
- Fix: Use escapeshellarg() or avoid shell execution entirely

--------------------------------------------------

## 12. Advanced Capabilities (IMPORTANT)

- Detect PHP Object Injection (POP chains)
- Identify chained vulnerabilities (LFI → RCE)
- Recognize zero-day-like patterns via anomaly detection
- Recommend safe fuzzing strategies (non-exploitative)

--------------------------------------------------

Requirements:

- Use clean Markdown formatting
- Be modular and extendable
- Focus on real-world PHP applications
- Maintain a professional and security-focused tone

Output only the final `skill.md` file.
