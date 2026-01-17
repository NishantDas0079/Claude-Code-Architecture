# Task D: Claude Engine - Multi-Language Code Review Workflow

## 🎯 **Scenario: "Audit our multi-language project for security and quality issues"**

### **Complete Execution Trace - 8 Steps**

---

## **Step 1: User Request & Intent Interpretation**

USER: "I have a multi-language project with Python data scripts,
C performance modules, and Java backend. Please audit it
for security vulnerabilities and code quality issues."

CLAUDE ENGINE:
• Detects keywords: "multi-language", "Python", "C", "Java",
"audit", "security", "quality"
• Classifies as: Multi-language code review + security audit
• Identifies required skills: python_analyzer, c_code_auditor, java_enterprise_review
• Estimated complexity: HIGH (requires coordination of 3 specialized skills)


---

## **Step 2: Rule Check & Constraint Validation**

ENGINE: Checks .claude.md for multi-language audit protocols:

RULES APPLIED:

"Always backup before security operations" → Creates project backup

"Log all audit activities" → Starts audit log

"Verify tool permissions" → Checks access to code scanners

"Respect file size limits" → Validates project size < 1GB

CONSTRAINTS IDENTIFIED:
• Time limit: 30 minutes total
• Memory limit: 2GB RAM
• Safety: Don't execute untrusted code
• Privacy: Mask sensitive data in outputs


---

## **Step 3: Task Decomposition & Skill Selection**

ENGINE: Breaks down into language-specific subtasks:
```
TASK DECOMPOSITION TREE:
└─ Multi-language Audit
├─ Python Analysis (skill/python_analyzer)
│ ├─ Syntax parsing
│ ├─ PEP 8 compliance
│ ├─ Security scanning
│ └─ Performance analysis
│
├─ C Code Audit (skill/c_code_auditor)
│ ├─ Memory safety
│ ├─ Buffer overflow detection
│ ├─ Performance bottlenecks
│ └─ Security vulnerabilities
│
└─ Java Review (skill/java_enterprise_review)
├─ Architecture review
├─ Thread safety analysis
├─ Spring framework audit
└─ Security compliance
```
SKILL SELECTION RATIONALE:
• python_analyzer: Best for data science scripts, ML code
• c_code_auditor: Essential for system-level C code with memory concerns
• java_enterprise_review: Required for Spring Boot enterprise applications


---

## **Step 4: Parallel Skill Execution with Tool Coordination**

TIMELINE TRACE:
T+0:00 → ENGINE: Starts parallel execution threads
T+0:02 → THREAD 1: python_analyzer calls tools:
• File system: Reads all .py files
• Pylint: Runs static analysis
• Bandit: Security scanning
• Black: Formatting check

T+0:02 → THREAD 2: c_code_auditor calls tools:
• Clang-tidy: Static analysis
• Cppcheck: Code checking
• Custom scanner: Buffer overflow detection
• Complexity analyzer: Performance metrics

T+0:02 → THREAD 3: java_enterprise_review calls tools:
• PMD: Code quality
• SpotBugs: Bug detection
• ArchUnit: Architecture validation
• Spring validator: Framework checks

TOOL COORDINATION LOGIC:
if language == "Python":
use_tools(["pylint", "bandit", "black"])
elif language == "C":
use_tools(["clang-tidy", "cppcheck", "valgrind"])
elif language == "Java":
use_tools(["PMD", "SpotBugs", "ArchUnit"])


---

## **Step 5: Cross-Language Dependency Analysis**

ENGINE: Identifies integration points between languages:

FOUND INTEGRATION POINTS:

Python → C via ctypes (C shared library called from Python)

Java → Python via Jython/JPype (Python scripts called from Java)

C → Java via JNI (Java Native Interface)


---

## **Step 6: Validation & Quality Gates**

VALIDATION CHECKLIST:

PYTHON OUTPUT VALIDATION:
✅ All .py files analyzed: 15/15
✅ PEP 8 compliance score: >80%
✅ No critical security issues: 0 found
✅ Test coverage: >70%
⚠️ Performance: 2 inefficient loops detected

C OUTPUT VALIDATION:
✅ Memory safety: No buffer overflows
✅ Security: No critical vulnerabilities
⚠️ Performance: 3 unoptimized loops
❌ Documentation: Missing for 5 functions

JAVA OUTPUT VALIDATION:
✅ Architecture: Layered pattern followed
✅ Thread safety: No race conditions
✅ Spring: Proper dependency injection
⚠️ Security: 2 medium-risk issues
✅ Performance: Connection pooling implemented

CROSS-LANGUAGE VALIDATION:
✅ Data flow between languages is type-safe
✅ Error handling consistent across languages
⚠️ Logging format inconsistent (3 different formats)
✅ API contracts well-defined


---

## **Step 7: Ambiguity Resolution & Decision Making**

ENGINE: Encountered ambiguous findings requiring decisions:

AMBIGUITY 1: Conflicting security ratings
• Python analyzer: "Use of eval() - LOW risk (sandboxed)"
• C auditor: "eval() usage - CRITICAL risk (memory unsafe)"
• RESOLUTION: Escalate to C rating (most conservative)
• ACTION: Mark as HIGH risk, recommend removal

AMBIGUITY 2: Performance trade-off
• Python: "Use list comprehension (faster)"
• C: "Pre-allocate array (memory efficient)"
• Java: "Use ArrayList (flexible)"
• RESOLUTION: Context-dependent
• ACTION: Provide all three options with context

AMBIGUITY 3: Thread safety
• Java: "Method is thread-safe (synchronized)"
• Python: "Global variable access not thread-safe"
• C: "No thread safety mechanisms detected"
• RESOLUTION: Inconsistent across languages
• ACTION: Flag for architectural review, recommend consistent approach

DECISION POLICY APPLIED:
• SAFETY: Always choose most secure option
• PERFORMANCE: Context-aware optimization
• MAINTAINABILITY: Prefer consistency across languages
• COMPLEXITY: Simpler solutions preferred


---

## **Step 8: Consolidated Reporting & Integration**

ENGINE: Merges outputs from all three skills into unified report:

REPORT GENERATION PROCESS:

EXECUTIVE SUMMARY (Combined from all languages)
• Overall risk: MEDIUM
• Languages analyzed: Python (15 files), C (8 files), Java (22 files)
• Critical issues: 1 (C buffer handling)
• Major issues: 5 (mixed across languages)

LANGUAGE-SPECIFIC FINDINGS (Structured by skill output)

PYTHON SECTION (from python_analyzer):
• Quality score: 85/100
• Critical issues: 0
• Recommendations:

Replace eval() with ast.literal_eval()

Vectorize data processing loops

Add type hints to 7 functions

C SECTION (from c_code_auditor):
• Memory safety: 92/100
• Critical issues: 1 (potential buffer overflow)
• Recommendations:

Replace strcpy() with strncpy()

Add bounds checking in 3 functions

Document memory ownership

JAVA SECTION (from java_enterprise_review):
• Architecture score: 88/100
• Thread safety: GOOD
• Recommendations:

Implement circuit breaker pattern

Add API rate limiting

Standardize error responses

CROSS-LANGUAGE INTEGRATION ISSUES
• Data serialization: 3 different formats (JSON, binary, XML)
• Error handling: Inconsistent across language boundaries
• Logging: Different formats and levels
• Security: Mixed authentication mechanisms

PRIORITIZED ACTION PLAN
🔴 IMMEDIATE (Week 1):

Fix C buffer overflow (CRITICAL security)

Remove eval() from Python (HIGH risk)

Standardize error handling

🟡 SHORT-TERM (Week 2-3):

Optimize Python data processing

Add C function documentation

Implement Java rate limiting

🟢 LONG-TERM (Month 1-2):

Unified logging framework

Cross-language testing suite

Performance benchmarking

# METRICS DASHBOARD
```
┌─────────────────┬─────────┬─────────┬─────────┐
│ Metric │ Python │ C │ Java │
├─────────────────┼─────────┼─────────┼─────────┤
│ Files │ 15 │ 8 │ 22 │
│ Quality Score │ 85/100 │ 92/100 │ 88/100 │
│ Security Issues │ 1 MED │ 1 CRIT │ 2 MED │
│ Performance │ 3 ISSUES│ 3 ISSUES│ GOOD │
│ Documentation │ GOOD │ POOR │ EXCELLENT│
└─────────────────┴─────────┴─────────┴─────────┘
```

# FINAL OUTPUT TO USER:
"Multi-language audit completed. Analyzed 45 files across 3 languages.
Found 1 critical issue (C buffer overflow), 8 major issues.
Priority recommendations and detailed reports attached.
Execution time: 4 minutes 32 seconds."


---

## 🔧 **ENGINE COORDINATION PATTERNS DEMONSTRATED**

### **Pattern 1: Parallel Execution with Result Merging**
```python
# Pseudo-code showing engine coordination
def execute_multi_language_audit(project):
    # Step 1: Parallel skill execution
    python_results = execute_skill_parallel(
        skill="python_analyzer",
        files=project.python_files,
        timeout=120
    )
    
    c_results = execute_skill_parallel(
        skill="c_code_auditor", 
        files=project.c_files,
        timeout=180
    )
    
    java_results = execute_skill_parallel(
        skill="java_enterprise_review",
        files=project.java_files,
        timeout=150
    )
    
    # Step 2: Wait for all results
    results = wait_for_all([python_results, c_results, java_results])
    
    # Step 3: Merge and validate
    merged = merge_results(
        results,
        strategy="priority_based",
        conflict_resolution="most_conservative"
    )
    
    # Step 4: Generate unified report
    report = generate_unified_report(merged)
    
    return report
```

Validation Flow:
1. Individual Skill Validation
   Python → Validate Python-specific rules
   C → Validate C-specific rules  
   Java → Validate Java-specific rules

2. Cross-Language Consistency Check
   Check: Data types match across language boundaries
   Check: Error handling is consistent
   Check: Security policies align

3. Integration Point Validation
   Check: Python→C interface (ctypes)
   Check: Java→Python interface (Jython)
   Check: C→Java interface (JNI)

4. Overall System Validation
   Check: Performance budget across languages
   Check: Security weakest link
   Check: Maintenance complexity

# Dynamic Tool Selection

def select_tools_for_language(language, project_type):
```
    tool_map = {
        "Python": {
            "data_science": ["pylint", "bandit", "black", "mypy"],
            "web": ["pylint", "bandit", "django-check"],
            "scripting": ["pylint", "bandit", "flake8"]
        },
        "C": {
            "embedded": ["cppcheck", "clang-tidy", "splint"],
            "system": ["valgrind", "clang-tidy", "coverity"],
            "library": ["cppcheck", "drmemory", "scan-build"]
        },
        "Java": {
            "enterprise": ["PMD", "SpotBugs", "ArchUnit", "checkstyle"],
            "android": ["lint", "findbugs", "pmd"],
            "library": ["SpotBugs", "checkstyle", "jacoco"]
        }
    }
    
    return tool_map.get(language, {}).get(project_type, ["default_tools"])
  ```


# SAFETY & ERROR HANDLING
Safety Mechanisms Applied:
Sandboxing: Each skill runs in isolated environment

Timeouts: Skills timeout after language-specific limits

Resource limits: Memory capped per skill

Fallback strategies: If one skill fails, others continue

Data sanitization: Outputs validated before merging


# WORKFLOW VISUALIZATION

┌─────────────────────────────────────────────────────┐
│                 USER REQUEST                         │
│ "Audit multi-language project"                       │
└──────────────────────────┬──────────────────────────┘
                           │
               ┌───────────▼───────────┐
               │   INTENT PARSING      │
               │ • Detect languages    │
               │ • Classify task type  │
               │ • Estimate complexity │
               └───────────┬───────────┘
                           │
               ┌───────────▼───────────┐
               │   TASK DECOMPOSITION  │
               │ • Python → skill 1    │
               │ • C → skill 2         │
               │ • Java → skill 3      │
               └───────────┬───────────┘
                           │
         ┌─────────────────┼─────────────────┐
         │                 │                 │
    ┌────▼─────┐     ┌────▼─────┐     ┌────▼─────┐
    │ Python   │     │   C      │     │  Java    │
    │ Analyzer │     │ Auditor  │     │ Reviewer │
    │ RUNNING  │     │ RUNNING  │     │ RUNNING  │
    └────┬─────┘     └────┬─────┘     └────┬─────┘
         │                │                │
         └────────────────┼────────────────┘
                          │
               ┌──────────▼───────────┐
               │   RESULT MERGING     │
               │ • Combine findings   │
               │ • Resolve conflicts  │
               │ • Validate consistency│
               └───────────┬───────────┘
                           │
               ┌───────────▼───────────┐
               │   UNIFIED REPORT      │
               │ • Executive summary   │
               │ • Language sections   │
               │ • Action plan         │
               │ • Metrics dashboard   │
               └───────────┬───────────┘
                           │
               ┌───────────▼───────────┐
               │   DELIVERY TO USER    │
               │ "Audit completed"     │
               │ + Detailed report     │
               └───────────────────────┘




# CHECKLIST: What This Workflow Demonstrates
# Task Requirements Met:
How it decomposes tasks: Broke into Python/C/Java parallel analysis

How it chooses skills/tools: Language-specific skill selection

How it validates outputs: Individual + cross-language validation

How it handles ambiguity: Decision policies for conflicts

How it manages multi-step workflows: State tracking, checkpoints

5-8 steps shown: 8 detailed steps documented

Integration with Task C skills: Uses python_analyzer, c_code_auditor, java_enterprise_review
