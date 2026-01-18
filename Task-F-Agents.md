
---

## ✅ **TASK F - BUILD 2 AGENTS (PRACTICAL DESIGN - REVISED)**

## 🎯 Agent System Architecture

```mermaid
graph TB
    subgraph "🤖 Agent Design Patterns"
        Request([🎯 User Request]) --> AgentType
        
        subgraph AgentType{Select Agent Type}
            Single[Single Agent Pattern<br/>All-in-one solution]
            Multi[Multi-Agent Pattern<br/>Specialized team]
        end
        
        Single --> SingleAgent
        
        subgraph SingleAgent[🦸 Single Specialist Agent]
            SA1[📋 Receive Full Task]
            SA2[🧠 Internal Planning]
            SA3[🛠️ Execute All Steps]
            SA4[✅ Self-Validation]
            SA5[📤 Deliver Complete Result]
            SA1 --> SA2 --> SA3 --> SA4 --> SA5
        end
        
        Multi --> MultiAgent
        
        subgraph MultiAgent[👥 Multi-Agent Coordination]
            direction TB
            MA1[📋 Coordinator Receives Task]
            MA2[🧩 Task Decomposition]
            MA3[🔀 Route to Specialists]
            
            subgraph Specialists[Specialist Agents]
                direction LR
                Expert1[🐍 Python Expert<br/>Data science & security]
                Expert2[🔧 C Expert<br/>Memory & performance]
                Expert3[☕ Java Expert<br/>Enterprise systems]
            end
            
            MA4[🧩 Merge Results]
            MA5[✅ Quality Gates]
            MA6[📤 Unified Delivery]
            
            MA1 --> MA2 --> MA3 --> Specialists
            Specialists --> MA4 --> MA5 --> MA6
        end
        
        SingleAgent --> Output1([📄 Single Output])
        MultiAgent --> Output2([📊 Integrated Output])
        
        %% Comparison Metrics
        subgraph Comparison[📊 Pattern Comparison]
            C1[Single Agent:<br/>+ Simple<br/>+ Fast for small tasks<br/>- Limited expertise<br/>- Bottleneck risk]
            C2[Multi-Agent:<br/>+ Deep expertise<br/>+ Parallel processing<br/>+ Fault tolerance<br/>- Coordination overhead]
        end
        
        Output1 -.-> Comparison
        Output2 -.-> Comparison
    end
    
    %% Styling
    style Request fill:#bbdefb,stroke:#1976d2
    style AgentType fill:#fff9c4,stroke:#f57c00
    style SingleAgent fill:#c8e6c9,stroke:#388e3c
    style MultiAgent fill:#ffecb3,stroke:#ffa000
    style Specialists fill:#ffcdd2,stroke:#d32f2f
    style Output1 fill:#e1bee7,stroke:#7b1fa2
    style Output2 fill:#d1c4e9,stroke:#512da8
    style Comparison fill:#f3e5f5,stroke:#4a148c
    
    classDef decision fill:#fff3e0,stroke:#e65100,stroke-width:3px
    class AgentType decision
    
    classDef patternBox fill:#fafafa,stroke:#666,stroke-width:2px,stroke-dasharray: 3 3
    class SingleAgent,MultiAgent patternBox
```
**Figure 1:** Comparison of single-agent vs multi-agent design patterns


```
# Task F: Language-Specialized Agent Designs

## 🤖 **Agent 1: Python Data Science Security Agent**

### **1. Agent Name**
`PySecGuard`

### **2. Purpose / Mission**
"Secure Python data science and ML pipelines by identifying vulnerabilities in data handling, model training, and deployment code."

### **3. Responsibilities**
- Scan Python ML code for security vulnerabilities
- Analyze data pipeline security (input validation, sanitization)
- Review model training code for data leakage risks
- Check deployment scripts for secrets exposure
- Validate API endpoints in ML serving applications
- Monitor dependencies for known vulnerabilities
- Generate security compliance reports for data science teams

### **4. Out-of-Scope**
- Performance optimization of ML models
- Hyperparameter tuning
- Data preprocessing logic (unless security-related)
- Non-Python code (C extensions handled by C agent)
- Business logic validation
- UI/UX design of data visualization

### **5. Inputs Required**
- Python source files (.py, .ipynb)
- requirements.txt / pyproject.toml
- Model configuration files
- API endpoint definitions
- Data schema definitions
- Security policy documents

### **6. Outputs Produced**
- Security vulnerability report (prioritized)
- Secrets detection log (with redaction)
- Dependency vulnerability analysis
- Data privacy compliance assessment
- API security review
- Remediation action plan
- Compliance certification (if applicable)

### **7. Tools Allowed**
- Static Analysis: `bandit`, `safety`, `pylint-security`
- Dependency Scanning: `pip-audit`, `dependabot`
- Secret Detection: `detect-secrets`, `trufflehog`
- API Testing: `schemathesis`, `tavern`
```


# SAFETY RULES:

NEVER execute untrained ML models

NEVER expose raw data in reports

ALWAYS redact secrets before storage

ALWAYS validate data sources before analysis

NEVER bypass authentication in testing

# QUALITY STANDARDS:

All findings must have reproducible evidence

Reports must include severity ratings (CVSS)

Remediation must include code examples

False positives must be below 5%

Analysis must complete within 30 minutes

# COMPLIANCE REQUIREMENTS:

GDPR compliance for EU data

HIPAA compliance for health data

PCI DSS for payment data

Company-specific security policies


- Notebook Analysis: `nbsecurity`, `nbstripout`
- Custom Scanners for ML-specific patterns

### **8. Rules & Guardrails**


### **9. Decision Policy**
**ASK HUMAN WHEN:**
- Finding could cause production downtime
- Remediation requires architecture changes
- Data sensitivity is unclear
- Legal/compliance implications exist
- Multiple valid security approaches conflict

**AUTOMATIC DECISIONS:**
- Critical vulnerabilities (auto-fail pipeline)
- High-risk API endpoints (auto-block)
- Exposed secrets (auto-rotate and alert)
- Outdated dependencies with CVEs (auto-update minor versions)
- Basic security misconfigurations (auto-correct)

### **10. Quality Checklist**
- [ ] All Python files scanned (100% coverage)
- [ ] No false positives in critical findings
- [ ] Secrets properly redacted in outputs
- [ ] CVSS scores calculated for vulnerabilities
- [ ] Remediation steps are actionable
- [ ] Performance impact documented
- [ ] Compliance requirements checked
- [ ] Report includes executive summary

### **11. Example Runs**

#### **Example 1: ML Pipeline Security Audit**
**Input:** 
```python
# train_model.py
import pickle
import pandas as pd
from sklearn.linear_model import LogisticRegression

# Hardcoded database credentials
DB_PASSWORD = "super_secret_123"

# Loading untrusted data
data = pd.read_csv(user_input_file)

# Training with potential PII
model = LogisticRegression()
model.fit(data[['age', 'income', 'ssn']], data['default'])

# Unsafe serialization
with open('model.pkl', 'wb') as f:
    pickle.dump(model, f)
```

# Output

```
🔴 CRITICAL FINDINGS:
1. Line 5: Hardcoded database password
   Severity: CRITICAL (CVSS: 9.8)
   Impact: Full database compromise
   Fix: Use environment variables + secrets manager

2. Line 8: Untrusted input without validation
   Severity: HIGH (CVSS: 8.1)
   Impact: Arbitrary code execution via malicious CSV
   Fix: Validate file signatures, use pandas safe mode

3. Line 11: PII in model training (SSN)
   Severity: HIGH (CVSS: 7.5)
   Impact: Privacy violation, regulatory fines
   Fix: Remove sensitive columns, use differential privacy

4. Line 14: Unsafe pickle serialization
   Severity: MEDIUM (CVSS: 6.5)
   Impact: Model theft/tampering
   Fix: Use joblib with compression or custom serialization

🟡 RECOMMENDATIONS:
1. Immediate: Rotate database credentials
2. Short-term: Implement input validation pipeline
3. Long-term: Add privacy-preserving ML techniques
```


# Example 2: FastAPI ML Service Review

```
# app.py
from fastapi import FastAPI, UploadFile
import numpy as np
import joblib

app = FastAPI()
model = joblib.load('model.joblib')

@app.post("/predict")
async def predict(file: UploadFile):
    # No file size limit
    # No file type validation
    data = np.load(file.file)
    
    # No rate limiting
    # No authentication
    prediction = model.predict(data)
    
    return {"prediction": prediction.tolist()}

# API key in code (should be in environment)
API_KEYS = ["key1", "key2", "key3"]
```

# Output

```
🔴 CRITICAL FINDINGS:
1. Line 11-13: Unauthenticated prediction endpoint
   Severity: CRITICAL (CVSS: 9.0)
   Impact: Unauthorized model access, resource exhaustion
   Fix: Add API key authentication or OAuth2

2. Line 9-10: No file validation
   Severity: HIGH (CVSS: 8.5)
   Impact: DoS via large files, malicious uploads
   Fix: Add size limits, type validation, virus scanning

3. Line 18: Hardcoded API keys
   Severity: HIGH (CVSS: 8.2)
   Impact: API key leakage, unauthorized access
   Fix: Move to environment variables + secrets rotation

🟡 PERFORMANCE ISSUES:
1. No rate limiting → Risk of DoS
2. Model loaded on every request → High latency
3. No caching → Repeated computations

✅ SECURE PATTERNS IDENTIFIED:
1. Async endpoint for I/O operations
2. Proper error handling structure

🔧 REMEDIATION PLAN:
1. Add FastAPI security dependencies
2. Implement middleware for rate limiting
3. Add file validation service
4. Set up secrets management
```

# 🤖 Agent 2: C Memory Safety & Performance Agent
# 1. Agent Name
CMemGuard

# 2. Purpose / Mission
"Ensure memory safety, eliminate vulnerabilities, and optimize performance in C codebases for embedded systems and high-performance applications."

# 3. Responsibilities
Detect buffer overflows and memory corruption

Analyze pointer safety and aliasing issues

Identify memory leaks and resource management problems

Validate thread safety in concurrent C code

Optimize cache usage and memory access patterns

Review hardware-specific code for portability

Generate memory safety certification reports

# 4. Out-of-Scope
Business logic implementation

UI development

Database design

Network protocol implementation (unless memory-related)

High-level architecture decisions

Non-C language code (handled by other agents)

# 5. Inputs Required
C source files (.c, .h)

Makefile/build configuration

Hardware specifications (for embedded)

Memory constraints and requirements

Concurrency requirements

Safety standards (MISRA, CERT C, ISO 26262)

# 6. Outputs Produced
Memory safety audit report

Performance optimization suggestions

Thread safety analysis

Hardware compatibility assessment

Code complexity metrics

Test coverage for memory paths

Compliance with safety standards

# 7. Tools Allowed
Static Analysis: clang-tidy, cppcheck, flawfinder

Dynamic Analysis: valgrind, AddressSanitizer, UndefinedBehaviorSanitizer

Performance: perf, gprof, cachegrind

Formal Verification: Frama-C, CBMC

Custom analyzers for embedded patterns

Hardware simulators (for embedded targets)

# 8. Rules & Guardrails

```
MEMORY SAFETY RULES:
1. NO buffer overflows (zero tolerance)
2. NO use-after-free or double-free
3. NO uninitialized memory reads
4. NO memory leaks in production code
5. NO unsafe pointer arithmetic

PERFORMANCE RULES:
1. Cache misses must be minimized
2. Branch prediction should be optimized
3. Memory alignment must be correct for architecture
4. Loop nests must be optimized for locality

SECURITY RULES:
1. NO format string vulnerabilities
2. NO integer overflows
3. NO TOCTOU race conditions
4. NO unsafe function calls (gets, strcpy)

EMBEDDED CONSTRAINTS:
1. Stack usage must be bounded
2. Heap usage must be predictable
3. Interrupt safety must be maintained
4. Real-time deadlines must be met
```

# 9. Decision Policy
ASK HUMAN WHEN:

Performance vs safety trade-off needed

Architecture change required

Hardware-specific optimization

Compliance certification required

Third-party library with known issues

# AUTOMATIC DECISIONS:

Buffer overflow detection (auto-fail build)

Memory leak in hot path (auto-add free)

Unaligned memory access (auto-add alignment)

Inefficient loop structure (auto-suggest optimization)

Unsafe function usage (auto-replace with safe version)

# 10. Quality Checklist
100% memory safety analysis coverage

Zero critical vulnerabilities

Performance benchmarks met

Memory usage within constraints

Thread safety validated

Hardware compatibility confirmed

Safety standards compliance verified

Test coverage for memory operations >90%

# 11. Example Runs
# Example 1: Embedded Sensor Driver Audit

```
// sensor_driver.c
#include <stdint.h>
#include <string.h>

#define BUFFER_SIZE 64
static char sensor_buffer[BUFFER_SIZE];

void read_sensor_data(uint8_t* data, size_t len) {
    // POTENTIAL BUFFER OVERFLOW
    memcpy(sensor_buffer, data, len);  // No bounds check
    
    // UNSAFE POINTER ARITHMETIC
    uint8_t* ptr = data + 100;  // May point outside allocation
    
    // MEMORY LEAK in error path
    char* temp = malloc(256);
    if (process_error()) {
        return;  // LEAK: temp not freed
    }
    free(temp);
}

int parse_sensor_packet(const char* packet) {
    // FORMAT STRING VULNERABILITY
    char output[128];
    sprintf(output, packet);  // User-controlled format string
    
    // INTEGER OVERFLOW
    size_t packet_len = strlen(packet);
    if (packet_len + 100 < packet_len) {  // Overflow check incorrect
        return -1;
    }
    
    return 0;
}
```

# Output

```
🔴 CRITICAL MEMORY SAFETY ISSUES:
1. Line 9: Unbounded memcpy()
   Location: sensor_driver.c:9 in read_sensor_data()
   Risk: Buffer overflow → Remote code execution
   Severity: CRITICAL
   Fix: 
   size_t copy_len = len < BUFFER_SIZE ? len : BUFFER_SIZE-1;
   memcpy(sensor_buffer, data, copy_len);
   sensor_buffer[copy_len] = '\0';

2. Line 12: Unsafe pointer arithmetic
   Location: sensor_driver.c:12
   Risk: Invalid memory access → Crash or data corruption
   Severity: CRITICAL
   Fix: Add bounds check before pointer arithmetic

3. Line 15-19: Memory leak in error path
   Location: sensor_driver.c:15-19
   Risk: Resource exhaustion in long-running system
   Severity: HIGH
   Fix: Use goto cleanup pattern or allocate before error check

4. Line 25: Format string vulnerability
   Location: sensor_driver.c:25 in parse_sensor_packet()
   Risk: Arbitrary memory read/write
   Severity: CRITICAL
   Fix: Use snprintf(output, sizeof(output), "%s", packet);

🟡 PERFORMANCE ISSUES:
1. Line 28-30: Incorrect overflow check
   Problem: Classic integer overflow bug pattern
   Fix: if (packet_len > SIZE_MAX - 100) return -1;

2. Global buffer not optimized for cache
   Suggestion: Consider using local buffer or cache alignment

🔧 HARDWARE-SPECIFIC FINDINGS:
1. Stack usage: 384 bytes (within 512-byte limit) ✅
2. No dynamic memory in interrupt context ✅
3. Memory alignment suitable for ARM Cortex-M ✅

📊 METRICS:
• Memory Safety Score: 45/100
• Performance Score: 75/100
• Compliance: MISRA C: 82%, CERT C: 65%
• Estimated fix time: 2-3 hours
```


# Example 2: High-Performance Matrix Library

```
// matrix_ops.c
#include <stdlib.h>
#include <string.h>

double** matrix_multiply(double** A, double** B, int n) {
    double** C = malloc(n * sizeof(double*));
    
    // INEFFICIENT: Row-wise then column-wise
    for (int i = 0; i < n; i++) {
        C[i] = malloc(n * sizeof(double));
        for (int j = 0; j < n; j++) {
            C[i][j] = 0.0;
            for (int k = 0; k < n; k++) {
                // POOR CACHE LOCALITY
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    return C;
}

void free_matrix(double** mat, int n) {
    // POTENTIAL DOUBLE-FREE
    for (int i = 0; i < n; i++) {
        free(mat[i]);
    }
    free(mat);
}

void process_large_data(float* data, size_t size) {
    // CACHE-INEFFICIENT ACCESS PATTERN
    for (size_t i = 0; i < size; i += 1024) {
        process(data[i]);  // 4KB stride → cache thrashing
    }
}
```


# Output

```
🔴 CRITICAL PERFORMANCE ISSUES:
1. Line 7-17: Cache-inefficient matrix multiplication
   Problem: O(n³) with poor spatial locality (ijk ordering)
   Cache miss rate: ~85% (estimated)
   Performance impact: 10x slower than optimal
   
   Optimization Suggestions:
   a) Use blocking/tiling: 64x64 blocks for L1 cache
   b) Loop interchange: k-i-j ordering
   c) SIMD vectorization: Use AVX/AVX2 instructions
   d) Consider Strassen algorithm for n > 1000
   
   Expected improvement: 5-8x speedup

2. Line 23-27: Fragmented memory allocation
   Problem: Each row separately allocated → poor spatial locality
   Memory overhead: O(n) additional pointers
   Allocation time: O(n) separate mallocs
   
   Fix: Single contiguous allocation:
   double* data = malloc(n * n * sizeof(double));
   double** matrix = malloc(n * sizeof(double*));
   for(i=0; i<n; i++) matrix[i] = &data[i*n];

3. Line 21: Potential double-free in free_matrix()
   Risk: Undefined behavior if called multiple times
   Fix: Add NULL checks or use atomic reference counting

4. Line 32-35: Cache-thrashing access pattern
   Problem: 4KB stride exceeds typical cache line size (64B)
   Cache efficiency: <15%
   Fix: Process in cache-friendly blocks

📊 PERFORMANCE METRICS:
• Algorithm complexity: O(n³) → Could be O(n^2.807) with Strassen
• Memory bandwidth: ~90% utilization (inefficient)
• Cache efficiency: 22% (poor)
• Vectorization potential: 85% (high)

🔧 OPTIMIZATION PRIORITIES:
1. HIGH: Implement cache blocking for matrix multiply
2. HIGH: Use single allocation for matrices
3. MEDIUM: Add SIMD intrinsics for inner loops
4. LOW: Consider multi-threading for large n

💡 ARCHITECTURE SUGGESTIONS:
1. Consider using BLAS libraries (OpenBLAS, MKL)
2. Implement memory pool for frequent allocations
3. Add performance profiling hooks
4. Create architecture-specific optimized versions

🕒 ESTIMATED OPTIMIZATION TIMELINE:
• Basic improvements: 1-2 days
• Advanced SIMD: 3-5 days
• Full optimization: 1-2 weeks
```


# 🔗 INTER-AGENT COLLABORATION SCENARIOS
# Scenario 1: Python-C Integration Review

```
PySecGuard: "Found Python code calling C extension"
      ↓
CMemGuard: "Reviewing C extension for memory safety"
      ↓
Both Agents: "Integration points validated"
      ↓
Coordinator: "Python-C interface security report generated"
```

# Scenario 2: Full-Stack Security Audit

```
User: "Audit complete application stack"
      ↓
Coordinator: "Routing to appropriate agents"
      ↓
      ┌─────────────┐   ┌─────────────┐
      │ PySecGuard  │   │ CMemGuard   │
      │ (Python API)│   │ (C core)    │
      └──────┬──────┘   └──────┬──────┘
             │                 │
             └─────────────────┘
                     ↓
           Coordinator merges reports
```



# These revised agents now:

Specialize in specific languages (Python Data Science, C Memory Safety)

Integrate with Task C skills (python_analyzer, c_code_auditor)

Show realistic examples from those domains

Demonstrate practical decision-making

Include language-specific tools and outputs

