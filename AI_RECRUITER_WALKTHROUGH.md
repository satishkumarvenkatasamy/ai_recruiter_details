# AI Recruiter 2.0: Complete Visual Walkthrough

## Introduction

**AI Recruiter 2.0** is a revolutionary technical hiring platform that transforms how organizations evaluate software engineering candidates. Unlike traditional resume screening tools, AI Recruiter 2.0 performs deep, multi-dimensional analysis that combines:

- **Multi-LLM Code Evaluation**: Analyzes candidate's GitHub repositories using 5 different AI models (OpenAI GPT-4o, Anthropic Claude Sonnet 4.x, Google Gemini, Mistral, xAI Grok) running in parallel
- **Knowledge Graph Construction**: Builds comprehensive code relationship graphs using AST analysis, revealing architectural patterns and code quality
- **Mathematical Scoring**: Provides rigorous, explainable scores based on graph theory, linear algebra, and statistical ensemble methods
- **Security & Quality Analysis**: Performs static analysis for vulnerabilities, design patterns, and maintainability metrics
- **Automated Interview Preparation**: Generates personalized technical questions based on candidate's actual code

This walkthrough demonstrates the complete candidate evaluation workflow, from uploading a resume to generating a comprehensive assessment report with actionable insights.

---

## Step 1: Starting a Candidate Evaluation Workflow

![Workflow Start](./airecruiterimages/Step001_CandidateEvalWorkflowStart.png)

The journey begins at the **Candidate Evaluation** page where recruiters can initiate a new analysis workflow. The interface provides:

- **Resume Upload**: Support for PDF and DOCX formats up to 20 pages
- **Job Description Upload**: Upload the role requirements for matching analysis
- **Workflow Dashboard**: View all active and completed candidate evaluations

The system uses intelligent text extraction with `pdfplumber` and `python-docx` to parse documents, preserving tables and formatting for accurate NER (Named Entity Recognition) analysis.

---

## Step 2: Workflow Initialization & Progress Tracking

### Step 2a: File Upload Confirmation

![Upload Confirmation](./airecruiterimages/Step002a_CandidateEvalWorkflowStart-01.png)

After uploading the resume and job description, the system confirms successful file reception and displays:
- File names and sizes
- Upload timestamps
- Workflow ID for tracking

### Step 2b: Real-Time Workflow Progress

![Workflow Progress](./airecruiterimages/Step002b_CandidateAnalysis-02.png)

The **Workflow Progress** panel provides real-time status updates for all 20+ analysis steps:

**Completed Steps** (shown in green):
- Extract Resume Text (executed in 84s)
- Extract JD Text (executed in 85s)

**Pending Steps** include:
- Resume NER Analysis
- JD NER Analysis
- GitHub Repository Analysis
- Multi-LLM Code Evaluation (OpenAI, Mistral, Claude, Gemini, Grok)
- Knowledge Graph Construction
- Security Analysis
- Quality Metrics Calculation
- Technical Question Generation

The overall progress bar shows 10% completion, with estimated total time of 8-12 minutes for typical candidates with 2-3 GitHub repositories.

### Step 2c: Active Analysis in Progress

![Analysis Running](./airecruiterimages/Step002c_CandidateAnalysis.png)

The "Analyzing..." button indicates the backend workflow orchestrator (DAG-based) is actively processing the candidate's data through multiple stages in parallel where possible.

---

## Step 3: Executive Summary - Consolidated Candidate Score

![Executive Summary](./airecruiterimages/Step003_CandidateAnalysisExecutiveSummary.png)

Upon completion, the **Executive Summary** tab presents a comprehensive at-a-glance assessment:

### Key Metrics Displayed:

**Final Score: 55.4/100**
- Grade: C (Pass with Reservations)
- Confidence Level: 75% (High Confidence)
- Recommendation: "Consider for Interview with Reservations"

### Six-Dimensional Scoring Breakdown:

1. **Resume-Job Fit**: 54.0/100
   - Measures alignment between candidate skills and job requirements
   - Based on NER extraction and semantic matching

2. **Coding Proficiency**: 56.7/100
   - Aggregated score from 5 LLM evaluations
   - Includes bug detection, code quality, optimization potential

3. **Security Awareness**: 64.7/100
   - Static analysis + LLM security audits
   - Vulnerability detection and severity classification

4. **Architecture Quality**: 70.0/100
   - Design patterns, coupling metrics, inheritance analysis
   - Calculated from knowledge graph structure

5. **Maintainability**: 56.6/100
   - Modularity, complexity, documentation quality
   - Graph Laplacian spectral analysis

6. **Communication**: 30.3/100
   - Code comments, naming conventions, README quality
   - Documentation coverage and completeness

### Decision Matrix:
- **Proceed to Interview**: YES (with reservations)
- **Request Code Sample**: NO (already analyzed GitHub repos)
- **Schedule Tech Screen**: YES
- **Archive Application**: NO

### Strengths:
- Decent architecture and design patterns
- Acceptable security practices
- Moderate coding proficiency

### Areas for Improvement:
- Documentation and code comments (30.3%)
- Resume-JD alignment needs verification
- Some maintainability concerns

---

## Step 4: Understanding the Scoring Methodology

### Step 4a: How the Candidate Was Scored

![Scoring Breakdown](./airecruiterimages/Step004a_HowCandidateWasScored.png)

This tab reveals the complete scoring methodology with mathematical transparency:

**Dimension Weights:**
- Resume-Job Fit: 25% (w = 0.25)
- Coding Proficiency: 20% (w = 0.20)
- Security Awareness: 20% (w = 0.20)
- Architecture Quality: 15% (w = 0.15)
- Maintainability: 12% (w = 0.12)
- Communication: 8% (w = 0.08)

**Score Calculation Formula:**

$$S_{final} = \sum_{d \in D} w_d \cdot s_d \cdot c_d$$

Where:
- $w_d$ = dimension weight
- $s_d$ = dimension score (0-100)
- $c_d$ = confidence factor (0-1)

**Confidence Interval:**
- CI = [50.4, 60.4]
- Margin of Error: ±5.0
- Based on variance propagation: $\sigma^2_{total} = \sum w_d^2 \cdot \sigma_d^2$

**Quality Level**: MODERATE
- Data Completeness: 100% (all dimensions available)
- Overall Confidence: 75%
- Manual Review Required: NO

### Step 4b: Detailed Score Calculation

![Score Calculation](./airecruiterimages/Step004b_ScoringCalculation.png)

This view shows the actual computation for each dimension:

**Resume-Job Fit (54.0)**:
- Weight: 0.25 → Contribution: 13.50
- Confidence: 0.80 → Adjusted: 10.80

**Coding Proficiency (56.7)**:
- Weight: 0.20 → Contribution: 11.34
- Confidence: 0.85 → Adjusted: 9.64

**Security Awareness (64.7)**:
- Weight: 0.20 → Contribution: 12.94
- Confidence: 0.90 → Adjusted: 11.65

**Architecture Quality (70.0)**:
- Weight: 0.15 → Contribution: 10.50
- Confidence: 0.85 → Adjusted: 8.93

**Maintainability (56.6)**:
- Weight: 0.12 → Contribution: 6.79
- Confidence: 0.75 → Adjusted: 5.09

**Communication (30.3)**:
- Weight: 0.08 → Contribution: 2.42
- Confidence: 0.60 → Adjusted: 1.45

**Total: 55.43** (rounded to 55.4)

### Step 4c: What-If Analysis - Score Sensitivity

![What-If Analysis](./airecruiterimages/Step004c_ScoringWhatIfAnalysis.png)

The interactive **What-If Analysis** tool allows recruiters to explore scoring scenarios:

**Example Scenario:**
- "What if we increase Security weight from 20% to 30%?"
- "What if Communication was weighted equally to Coding?"

**Use Cases:**
- **Role-Specific Weighting**: Security-critical roles (fintech, healthcare) can emphasize Security Awareness
- **Junior vs Senior Roles**: Adjust Architecture and Maintainability weights based on seniority
- **Sensitivity Analysis**: Understand which dimensions have the most impact on final score

---

## Step 5: Detailed Scoring Explanation with Mathematical Formulas

![Detailed Explanation](./airecruiterimages/Step005_ScoringDetailedExplanation.png)

This section provides an academic-level breakdown of each scoring dimension:

### Security Awareness Score: 64.7/100

**Formula:**
$$S_{security} = w_{static} \cdot S_{static} + w_{llm} \cdot S_{llm}$$

Where:
- $w_{static} = 0.4$ (static analysis weight)
- $w_{llm} = 0.6$ (LLM ensemble weight)

**Static Analysis Component:**
$$S_{static} = \max(0, \min(100, S_{base} - \sum_{i} n_i \cdot w_i))$$

- $S_{base}$ = 85 (base score from knowledge graph)
- Penalties: $n_{high} \times 5.0 + n_{medium} \times 2.0 + n_{low} \times 0.5$

**LLM Ensemble Component:**
$$S_{llm} = \frac{\sum_{k=1}^{5} S_k \cdot r_k}{\sum_{k=1}^{5} r_k}$$

Where $r_k$ are reliability weights:
- OpenAI: 1.0
- Claude: 1.0
- Gemini: 0.95
- Mistral: 0.90
- Grok: 0.85

**Confidence Interval:**
$$\text{CI} = [S_{security} - 1.96\sqrt{\sigma^2}, S_{security} + 1.96\sqrt{\sigma^2}]$$

**Result:**
- Security Score: 64.7
- CI: [60.2, 69.2]
- Confidence: 90%
- Issues Found: 2 medium, 1 low severity

### Architecture Quality Score: 70.0/100

**Formula:**
$$S_{arch} = 0.30 \cdot S_{patterns} + 0.30 \cdot S_{structure} + 0.25 \cdot S_{coupling} + 0.15 \cdot S_{lifecycle}$$

**Design Pattern Score:**
- Factory Pattern: Detected (conformance: 85%)
- Observer Pattern: Partial (conformance: 60%)
- Singleton: Well-implemented (conformance: 95%)
- Anti-patterns: None detected

**Coupling Score (from Knowledge Graph):**
$$S_{coupling} = 100 - (0.35 \cdot C_{direct} + 0.25 \cdot C_{temporal})$$

Where:
- $C_{direct} = \frac{\|A\|_0}{n(n-1)} \times 100$ (direct coupling from adjacency matrix)
- $C_{temporal} = \frac{\|A^2\|_0}{n(n-1)} \times 100$ (2-hop coupling from $A^2$)

**Result:**
- Direct Coupling: 18% (good)
- Indirect Coupling: 35% (moderate)
- Overall Architecture: 70.0/100

---

## Step 6: Candidate-Job Description Match Analysis

![JD Match](./airecruiterimages/Step006_CandidateMatchForJobDescriptionAnalysis.png)

This critical tab shows how well the candidate aligns with job requirements:

### Match Score: 54.0/100

**Skills Alignment:**
- Required Skills Met: 11/15 (73%)
- Critical Skills Missing: 4
  - "Kubernetes orchestration"
  - "CI/CD pipeline automation"
  - "Microservices architecture"
  - "AWS cloud services"

**Experience Match:**
- Required: 5+ years → Candidate: 3 years
- Level: Mid-Senior → Candidate appears Mid-level

**Technology Stack Overlap:**
- Languages: Python, JavaScript (Match: 100%)
- Frameworks: React (Match: 100%), FastAPI (Match: 0% - not in JD)
- Databases: PostgreSQL (Match: 100%), DuckDB (Match: 0%)

**Explanation:**
"Candidate demonstrates strong foundational skills in core technologies (Python, React, PostgreSQL) but lacks experience in cloud infrastructure (Kubernetes, AWS) and DevOps practices (CI/CD) emphasized in the job description. Recommend assessing whether these gaps can be closed with on-the-job training or if they are deal-breakers."

**Recommendation:**
- **Fit Level**: MODERATE
- **Decision**: Consider for interview with focus on cloud/DevOps gap assessment
- **Training Estimate**: 3-6 months to reach full proficiency in missing areas

---

## Step 7: Comprehensive Candidate Profile

![Candidate Details](./airecruiterimages/Step007_CandidateDetails.png)

The **Candidate Details** section aggregates all extracted information:

### Personal Information
- **Name**: Prakalya (extracted from resume)
- **Experience**: 3 years
- **Location**: Not specified
- **Contact**: [Redacted for privacy]

### Technical Skills Identified
**Programming Languages:**
- Python (Expert)
- JavaScript/TypeScript (Intermediate)
- Java (Basic)

**Frameworks & Libraries:**
- React, Next.js
- FastAPI, Flask
- NumPy, Pandas, SciPy

**Tools & Technologies:**
- Git, GitHub
- Docker (basic)
- Neo4j, DuckDB
- Tree-sitter (AST parsing)

### GitHub Profile Analysis
- **Public Repositories**: 3 analyzed
- **Total Commits**: 450+
- **Languages**: Python (70%), JavaScript (25%), Other (5%)
- **Activity Level**: Moderate (2-3 commits/week)

### Education
- Bachelor's in Computer Science (detected from resume)
- Relevant coursework: Data Structures, Algorithms, Database Systems

### Certifications
- None detected in resume

### Projects Highlighted
1. **Code Evaluator**: Multi-LLM code analysis tool
2. **Knowledge Graph Builder**: AST-based relationship extraction
3. **Recruiter Dashboard**: React-based UI for candidate assessment

---

## Step 8: Job Description Requirements Breakdown

![JD Details](./airecruiterimages/Step008_JobDescriptionDetails.png)

This tab shows the parsed job description with extracted requirements:

### Role: Oracle Software Developer 2

### Key Responsibilities
1. Design and develop cloud-based IAM services
2. Build scalable microservices architecture
3. Implement CI/CD pipelines for automated deployment
4. Collaborate with cross-functional teams
5. Ensure security best practices in code

### Required Technical Skills
**Must Have:**
- 5+ years of software development experience
- Strong proficiency in Python and JavaScript
- Experience with Kubernetes and container orchestration
- Cloud platform expertise (AWS, Azure, or GCP)
- RESTful API design and implementation
- SQL and NoSQL database experience

**Nice to Have:**
- Identity and Access Management (IAM) experience
- Microservices architecture patterns
- GraphQL experience
- Frontend development (React)

### Soft Skills
- Strong problem-solving abilities
- Excellent communication skills
- Team collaboration experience
- Agile/Scrum methodology familiarity

### Education Requirements
- Bachelor's degree in Computer Science or equivalent

### Extracted Entities (NER)
- **Skills**: Python, JavaScript, Kubernetes, AWS, Docker, React, PostgreSQL, CI/CD
- **Experience Level**: Senior (5+ years)
- **Domain**: Cloud Infrastructure, IAM, Security
- **Team Size**: Cross-functional (5-10 people)

---

## Step 9: Multi-LLM Code Evaluation Overview

![Multi-LLM Overview](./airecruiterimages/Step009_CandidateGitHubCodeEvaluationByLLMs.png)

The **Code Quality** tab showcases the unique multi-LLM consensus approach:

### Evaluation Models:
1. **OpenAI GPT-4o**: 50.0/100
2. **Mistral Large**: 73.8/100
3. **Gemini 2.0 Flash**: 74.0/100
4. **Claude Sonnet 4.x**: (pending in this workflow)
5. **xAI Grok**: (pending in this workflow)

### Consensus Score: 65.9/100
- **Calculation**: Weighted average using reliability weights
- **Model Agreement**: 77% (Moderate)
- **Variance**: σ = 11.27 (Moderate disagreement)

### Why Multiple LLMs?

**Benefits:**
1. **Reduces Bias**: Each model has different training data and evaluation criteria
2. **Higher Confidence**: Agreement among models indicates reliable assessment
3. **Catches More Issues**: Different models detect different bug patterns
4. **Validation**: Cross-reference findings across models

**Interpretation:**
- **High Agreement (>85%)**: Very confident in assessment
- **Moderate Agreement (70-85%)**: Generally reliable, some uncertainty
- **Low Agreement (<70%)**: Manual review recommended

In this case, 77% agreement suggests the candidate's code quality is reasonably well-assessed, though the variance indicates some models found issues others didn't.

---

## Step 10: OpenAI Code Evaluation Details

![OpenAI Evaluation](./airecruiterimages/Step010_CandidateGithubCodeEvaluationByOpenAI.png)

### OpenAI GPT-4o Analysis: 50.0/100

**Bug Detection (Rating: 4/10)**

*Identified Issues:*
1. **Severe - Line 99-118 (sudoku.c)**: Unsafe pointer casting from 2D array to `int**`. This is undefined behavior in C and non-portable.
   ```c
   int **sample_sudoku_problem = (int **)sample_problem_1;  // WRONG
   ```
   **Severity**: 7/10

2. **Moderate - Line 605-643 (sudoku.c)**: `print_sudoku()` modifies `possible_values` array during printing, causing unintended side effects.
   **Severity**: 5/10

3. **Minor - Line 189-211 (sudoku.c)**: Excessive `scanf` calls block execution, making program unusable without manual input.
   **Severity**: 2/10

**Security Evaluation (Rating: 8/10)**

*Vulnerabilities Found:*
1. **User Input Validation**: `scanf` without bounds checking
   **Severity**: 5/10

2. **Type Safety**: Unsafe array-to-pointer casts
   **Severity**: 3/10

*Overall*: Code has moderate security posture. No critical vulnerabilities, but unsafe practices present.

**Optimization Opportunities (Rating: 5/10)**

1. Remove unnecessary casts and commented code
2. Use `const` for fixed sudoku puzzles
3. Modularize repeated logic in `solve_row_col_2nd_level`
4. Reduce global variable usage for better testability

**Final Assessment:**
"The code is functional for Sudoku solving but exhibits poor C practices including dangerous pointer manipulation, excessive global state, and debugging scaffolding left in production code. Test suite is disconnected from actual implementation."

---

## Step 11: Claude Code Evaluation Details

![Claude Evaluation](./airecruiterimages/Step011_CandidateGithubCodeEvaluationByClaude.png)

### Anthropic Claude Sonnet 4.x Analysis: (Score not shown in image)

**Bug Detection:**

Claude identified similar issues but with more detailed analysis:

1. **Type System Violation (Critical)**:
   - Location: `main()` function
   - Issue: "Treating a pointer to array as pointer to pointer is fundamentally incorrect in C memory model"
   - Impact: Undefined behavior, potential crashes on different architectures
   - Recommendation: Use proper 2D array passing: `void func(int arr[][9])`

2. **State Mutation in Display Logic (Medium)**:
   - Location: `print_sudoku()`
   - Issue: "Display functions should be pure - they modify solver state"
   - Impact: Debugging becomes difficult, unexpected behavior
   - Recommendation: Separate data access from modification

**Security Analysis:**

Claude's security assessment is more nuanced:

"While the code doesn't handle network input or file operations, the fundamental memory safety issues (unsafe casts, unbounded input) represent a security risk if this code is ever adapted for production use. The `scanf` without validation is a classic buffer overflow vector."

**Code Quality Assessment:**

- **Modularity**: 3/10 (heavy use of globals)
- **Testability**: 2/10 (test suite doesn't test actual code)
- **Readability**: 5/10 (decent naming but excessive comments)
- **Maintainability**: 4/10 (difficult to extend or modify)

**Unique Insights from Claude:**

Claude excels at architectural reasoning:
- "The algorithm structure (3-level solving) is sound, but implementation is tightly coupled"
- "Consider visitor pattern for sudoku cell operations"
- "Separate puzzle representation from solution algorithm"

---

## Step 12: Knowledge Graph Construction

![Knowledge Graph Overview](./airecruiterimages/Step012_KnowledgeGraphOfGitHubSourceCode.png)

The **Knowledge Graph** tab is where AI Recruiter 2.0 truly differentiates itself:

### Graph Statistics:
- **Total Nodes**: 135 entities
- **Total Edges**: 352 relationships
- **Languages Detected**: 1 (C)
- **Files Analyzed**: 2 (sudoku.c, test_sudoku.c)
- **Classes**: 0 (C doesn't have classes)
- **Functions**: 18
- **Imports**: 5 standard library headers

### Entity Types:
- **Files**: 2 nodes
- **Functions**: 18 nodes (solve_sudoku, print_sudoku, get_missing_numbers, etc.)
- **Global Variables**: 4 nodes (sample_problem_1, sample_problem_2, possible_values, array)
- **Includes**: 5 nodes (stdio.h, stdlib.h, string.h, CUnit/CUnit.h)

### Relationship Types:
- **CONTAINS**: File contains Function (18 edges)
- **CALLS**: Function calls Function (45 edges)
- **USES**: Function uses Global Variable (28 edges)
- **INCLUDES**: File includes Header (10 edges)

### Graph Metrics (from NetworkX):
- **Density**: 0.038 (sparse, good modularity)
- **Average Degree**: 5.2 (moderate connectivity)
- **Clustering Coefficient**: 0.12 (low clustering, indicates procedural style)
- **Diameter**: 6 (longest path between any two functions)

### Matrix Representations:

**Adjacency Matrix $A$**: 135×135
- Captures direct relationships (function calls)
- Used for coupling analysis

**Adjacency Matrix Squared $A^2$**: 135×135
- Reveals 2-hop indirect dependencies
- Used for temporal coupling detection

**Incidence Matrix $B$**: 135×352
- Maps entities to relationships
- Used for hypergraph analysis

**Graph Laplacian $L = D - A$**:
- Eigenvalue analysis for connectivity
- $\lambda_2 = 0.023$ (algebraic connectivity, indicates good modular structure)

---

## Step 13: Interactive Knowledge Graph Visualization (Zoomed)

![KG Visualization Zoomed](./airecruiterimages/Step013_KnowledgeGraphVisualizationInteractiveZoomedIn.png)

This view shows a **zoomed-in section** of the interactive D3.js visualization:

### Visible Components:

**Central Node: `solve_sudoku` (main function)**
Connected to:
- `print_sudoku` (CALLS)
- `solve_sudoku_1st_level` (CALLS)
- `solve_sudoku_2nd_level` (CALLS)
- `solve_sudoku_3rd_level` (CALLS)
- `possible_values` (USES)
- `array` (USES)

### Node Styling:
- **Blue circles**: Functions
- **Orange squares**: Global variables
- **Green diamonds**: Files
- **Red triangles**: External libraries

### Edge Styling:
- **Solid lines**: CALLS relationships
- **Dashed lines**: USES relationships
- **Dotted lines**: INCLUDES relationships

### Interactive Features:
1. **Pan & Zoom**: Explore large graphs
2. **Node Hover**: Shows full entity details
3. **Click to Expand**: Reveal connected subgraph
4. **Filter by Type**: Show only functions, or only relationships
5. **Search**: Find specific entities by name
6. **Highlight Path**: Show shortest path between two nodes

### Use Cases:
- **Code Navigation**: Understand call flow without reading source
- **Impact Analysis**: "If I modify function X, what's affected?"
- **Onboarding**: New developers visualize codebase structure
- **Architecture Review**: Identify tightly coupled modules

---

## Step 14: Interactive Knowledge Graph - Full View

![KG Visualization Full](./airecruiterimages/Step014_KnowledgeGraphVisualizationInteractive.png)

The **full graph view** shows the entire codebase structure:

### Layout Algorithm: Force-Directed (D3.js)
- **Force Simulation**: Nodes repel each other, edges pull them together
- **Convergence**: Graph stabilizes into natural clustering
- **Central nodes**: Highly connected (main functions)
- **Peripheral nodes**: Utility functions, less connected

### Clusters Identified:
1. **Core Solving Logic** (center): solve_sudoku, solve_1st_level, solve_2nd_level, solve_3rd_level
2. **Helper Functions** (top): get_missing_numbers, clear_missing_possible_arrays
3. **I/O Functions** (bottom): print_sudoku, read_input
4. **Test Suite** (isolated): test_sudoku.c functions (not connected to main code - bug!)

### Architectural Insights:
- **Hub Functions**: `solve_sudoku` has highest degree (8 connections)
- **Isolated Components**: Test functions have no edges to implementation → **Critical Issue**
- **Linear Flow**: Main solving pipeline shows clear progression 1st → 2nd → 3rd level

### Performance Optimization:
- For graphs >1000 nodes: Render only high-degree nodes at low zoom
- Use WebGL renderer for >10,000 nodes
- Implement graph sampling for initial view

---

## Step 15: Static Knowledge Graph Visualization (PlantUML)

![KG Static](./airecruiterimages/Step015_KnowledgeGraphVisualizationStatic.png)

For documentation and presentations, AI Recruiter 2.0 generates **static diagrams** using PlantUML:

### PlantUML Benefits:
- **Version Control Friendly**: Text-based diagram definition
- **Reproducible**: Same input always produces same output
- **Export Formats**: PNG, SVG, PDF for reports
- **Standardized**: Widely used in software documentation

### Diagram Shows:
```plantuml
@startuml
package "sudoku.c" {
  [solve_sudoku]
  [solve_sudoku_1st_level]
  [solve_sudoku_2nd_level]
  [solve_sudoku_3rd_level]
  [print_sudoku]
  [get_missing_numbers]
}

package "test_sudoku.c" {
  [test_suite_main]
  [test_solve_basic]
}

[solve_sudoku] --> [solve_sudoku_1st_level]
[solve_sudoku] --> [solve_sudoku_2nd_level]
[solve_sudoku] --> [solve_sudoku_3rd_level]
[solve_sudoku] --> [print_sudoku]
[solve_sudoku_1st_level] --> [get_missing_numbers]

@enduml
```

### Use Cases:
- **Documentation**: Include in README or design docs
- **Code Review**: Print and annotate during reviews
- **Presentations**: Export high-quality images for slides
- **Compliance**: Regulatory audits require static diagrams

---

## Step 16: Architecture Diagrams from Knowledge Graph

### Step 16a: Component Architecture

![Architecture Diagram 1](./airecruiterimages/Step016a_ArchitectureDiagramFromKnowledgeGraph.png)

AI Recruiter 2.0 automatically generates **architecture diagrams** showing:

**Component Breakdown:**
1. **Input Layer**: File reading, puzzle initialization
2. **Core Solver**: Three-level solving algorithm
3. **Helper Utilities**: Missing number detection, array operations
4. **Output Layer**: Printing, validation

**Dependencies:**
- Standard Library: stdio.h, stdlib.h, string.h
- Testing Framework: CUnit (optional)

### Step 16b: Module Dependency Graph

![Architecture Diagram 2](./airecruiterimages/Step016b_ArchitectureDiagramFromKnowledgeGraph.png)

This diagram focuses on **module-level dependencies**:

**Layers:**
1. **Presentation**: `print_sudoku`, `display_results`
2. **Business Logic**: `solve_*` functions
3. **Data Access**: `possible_values` array, puzzle data structures
4. **External**: Standard library functions

**Coupling Analysis:**
- **Tight Coupling**: Solver functions heavily use global `possible_values` array
- **Loose Coupling**: Test suite (incorrectly) isolated from implementation
- **Cyclic Dependencies**: None detected (good!)

**Recommendations:**
1. Reduce coupling by passing `possible_values` as parameter
2. Create header file to link test suite
3. Separate data structures from algorithms

---

## Step 17: Call Graph Visualization

![Call Graph](./airecruiterimages/Step017_CallGraphVisualizationFromKG.png)

The **Call Graph** shows function invocation hierarchy:

### Entry Point: `main()`
```
main()
 ├─ solve_sudoku()
 │   ├─ print_sudoku()
 │   ├─ solve_sudoku_1st_level()
 │   │   ├─ get_missing_numbers()
 │   │   ├─ clear_missing_possible_arrays()
 │   │   └─ print_sudoku()
 │   ├─ solve_sudoku_2nd_level()
 │   │   ├─ get_missing_numbers()
 │   │   └─ solve_row_col_2nd_level()
 │   └─ solve_sudoku_3rd_level()
 │       └─ solve_row_col_3rd_level()
 └─ print_sudoku()
```

### Call Depth Analysis:
- **Maximum Depth**: 4 (main → solve_sudoku → solve_1st → get_missing)
- **Most Called Function**: `print_sudoku` (called 3 times)
- **Recursive Calls**: None detected

### Performance Implications:
- Shallow call stack = efficient execution
- Multiple calls to `print_sudoku` = potential performance bottleneck for large puzzles
- No recursion = no stack overflow risk

### Call Tree Export Formats:
- **ASCII Text**: Copy-paste into documentation
- **JSON**: Programmatic analysis
- **Graphviz DOT**: Custom rendering
- **Interactive D3**: Explore call flow visually

---

## Step 18: Semantic Analysis - Understanding Code Intent

### Step 18a: Function Purpose Detection

![Function Purposes](./airecruiterimages/Step018a_SourceCodeSemanticAnalysisFunctionPurposes.png)

Using LLM-powered semantic analysis, AI Recruiter 2.0 **automatically infers** function purposes:

**Detected Functions:**

1. **`solve_sudoku`**
   - **Purpose**: "Main orchestrator that coordinates the three-level solving strategy"
   - **Intent**: Control flow, puzzle solving coordination
   - **Pattern**: Orchestrator/Facade pattern

2. **`get_missing_numbers`**
   - **Purpose**: "Identifies which digits (1-9) are missing in a given row, column, or box"
   - **Intent**: Data analysis, constraint checking
   - **Pattern**: Helper/Utility function

3. **`print_sudoku`**
   - **Purpose**: "Displays current puzzle state with formatting for readability"
   - **Intent**: User interface, debugging
   - **Pattern**: Display/Presenter function

4. **`solve_sudoku_1st_level`**
   - **Purpose**: "First solving pass - fills cells where only one number is possible"
   - **Intent**: Constraint satisfaction, easy cases
   - **Pattern**: Strategy pattern (level 1 strategy)

5. **`clear_missing_possible_arrays`**
   - **Purpose**: "Resets tracking arrays when a cell is solved to maintain consistency"
   - **Intent**: State management, data synchronization
   - **Pattern**: Utility/Cleanup function

**Semantic Relationships:**
- **Collaborators**: Functions that work together (solve_sudoku + solve_1st_level)
- **Dependents**: Functions that rely on others (solve_1st_level depends on get_missing_numbers)
- **Alternatives**: Functions that could replace each other (different solving strategies)

### Step 18b: Design Pattern Detection

![Code Patterns](./airecruiterimages/Step018b_SourceCodeSemanticAnalysisCodePattern.png)

AI Recruiter 2.0 identifies **design patterns** and **anti-patterns**:

**Detected Patterns:**

1. **Strategy Pattern (Partial)**
   - Where: `solve_sudoku_1st_level`, `solve_sudoku_2nd_level`, `solve_sudoku_3rd_level`
   - Quality: 60% conformance
   - Issue: "Strategies are hardcoded in sequence, not truly interchangeable"
   - Recommendation: "Extract strategies into separate structs with function pointers"

2. **Template Method (Implicit)**
   - Where: All `solve_*` functions follow similar structure
   - Quality: 75% conformance
   - Observation: "Common pattern of get_missing → check_constraints → fill_cell, but not formalized"

**Detected Anti-Patterns:**

1. **God Object**
   - Where: `possible_values` global array
   - Severity: Medium (6/10)
   - Issue: "Single array used by all functions, creates tight coupling"
   - Impact: "Difficult to test, hard to parallelize, risk of race conditions"

2. **Spaghetti Code (Mild)**
   - Where: `solve_row_col_2nd_level`
   - Severity: Low (3/10)
   - Issue: "Complex nested loops with minimal abstraction"
   - Impact: "Hard to understand, difficult to modify"

**Code Smells:**

1. **Long Method**: `solve_row_col_3rd_level` (100+ lines)
2. **Duplicated Code**: Constraint checking repeated across levels
3. **Feature Envy**: Functions heavily access global state
4. **Dead Code**: Commented-out debug statements

**Quality Score Impact:**
- Design patterns add +15 points to Architecture score
- Anti-patterns subtract -8 points
- Net impact: +7 (moderate positive)

---

## Step 19: Security Analysis Using Knowledge Graph

![Security Analysis](./airecruiterimages/Step019_SecurityAnalysisOfSourceCodeUsingKG.png)

The **Security Analysis** tab combines static analysis with LLM evaluations:

### Security Score: 64.7/100

**Vulnerability Breakdown:**

1. **Buffer Overflow Risk (Medium)**
   - **Location**: sudoku.c:142
   - **Issue**: `scanf("%c", &dummyChar)` without input validation
   - **CVSS Score**: 5.5 (Medium)
   - **Exploitability**: Low (requires local access)
   - **Impact**: Program crash or unexpected behavior
   - **Recommendation**: Use `fgets()` with buffer size or validate input length

2. **Memory Safety (Medium)**
   - **Location**: sudoku.c:148-151
   - **Issue**: Unsafe pointer casting from array to `int**`
   - **CVSS Score**: 6.0 (Medium)
   - **Exploitability**: Medium (undefined behavior on some architectures)
   - **Impact**: Potential segmentation fault or data corruption
   - **Recommendation**: Use proper array syntax: `void func(int arr[][9])`

3. **Information Disclosure (Low)**
   - **Location**: sudoku.c:605-643
   - **Issue**: Uninitialized variables printed in debug mode
   - **CVSS Score**: 2.0 (Low)
   - **Exploitability**: Very Low
   - **Impact**: Leaks stack memory contents
   - **Recommendation**: Initialize all variables before use

### Security Metrics from Knowledge Graph:

**Input Validation Coverage:**
- Functions accepting input: 3
- Functions with validation: 0
- Coverage: 0% (**Critical gap**)

**Memory Safety:**
- Unsafe pointer operations: 2
- Proper bounds checking: 60%
- Dynamic memory allocation: 0 (good - no malloc/free issues)

**Code Injection Risk:**
- User input used in execution: No
- System calls: None
- External commands: None
- Risk: **Very Low**

### LLM Security Assessments:

**OpenAI**: 80/100
- "Moderate security posture. No network-facing vulnerabilities."

**Claude**: 85/100
- "Memory safety concerns exist but are not immediately exploitable."

**Gemini**: 70/100
- "Input validation is insufficient. Recommend defense-in-depth approach."

**Mistral**: 75/100
- "Typical C pitfalls present. Not suitable for production without hardening."

**Ensemble Score**: 64.7/100 (weighted average with confidence factors)

### Recommendations:
1. **High Priority**: Add input validation for all `scanf` calls
2. **Medium Priority**: Fix unsafe pointer casts
3. **Low Priority**: Initialize all variables
4. **Best Practice**: Run static analysis tools (Valgrind, AddressSanitizer)

---

## Step 20: Overall Code Quality Assessment

![Code Quality](./airecruiterimages/Step020_OverallCodeQualityUsingKG.png)

The **Quality Metrics** tab synthesizes all analyses into a comprehensive report:

### Overall Quality: 75.3/100 (Grade: B-)

**Category Breakdown:**

1. **Modularity: 65/100**
   - Functions per file: 9 (good)
   - Average function length: 35 lines (acceptable)
   - Coupling: 45% (moderate, could be better)
   - Cohesion: 70% (good)

2. **Complexity: 72/100**
   - **Cyclomatic Complexity**:
     - Average: 8 (acceptable)
     - Maximum: 15 in `solve_row_col_3rd_level` (high)
     - Functions > 10: 3 (20%)
   - **Cognitive Complexity**: 12 average (moderate)
   - **Nesting Depth**: Maximum 4 levels (acceptable)

3. **Documentation: 30/100** ⚠️
   - Documented functions: 2/18 (11%)
   - Comment density: 5% (very low)
   - README quality: None found
   - API documentation: Missing

4. **Testing: 20/100** ⚠️
   - Test coverage: 0% (tests not connected to code)
   - Unit tests: Present but non-functional
   - Integration tests: None
   - Test assertions: 3 (insufficient)

5. **Maintainability Index: 68/100**
   - Based on Halstead metrics and cyclomatic complexity
   - Formula: $MI = 171 - 5.2 \ln(V) - 0.23G - 16.2 \ln(LOC)$
   - Where: V = Halstead Volume, G = Cyclomatic Complexity, LOC = Lines of Code

### Graph-Based Quality Metrics:

**Structural Metrics:**
- Graph Density: 0.038 (sparse, good)
- Clustering Coefficient: 0.12 (low, procedural style appropriate for C)
- Modularity (Newman): 0.45 (moderate community structure)

**Coupling Metrics (from $A^2$):**
- Direct coupling: 18%
- Indirect (2-hop) coupling: 35%
- Temporal coupling: 22%
- Overall coupling grade: B (acceptable)

**Cohesion Metrics:**
- Functional cohesion: High (functions do one thing)
- Sequential cohesion: High (clear pipeline)
- Data cohesion: Medium (shared global state)

### Quality Grade Justification:

**Strengths (+):**
- Clear algorithm structure
- Reasonable complexity for most functions
- Good functional cohesion
- No external dependencies (self-contained)

**Weaknesses (-):**
- Extremely poor documentation
- Non-functional test suite
- Some functions are too complex
- Heavy reliance on global state

**Grade: B- (75.3/100)**
- "Code is functional and reasonably structured but lacks documentation and testing discipline expected in professional software. Would benefit from refactoring and establishing testing harness."

---

## Step 21: Automated Interview Question Generation

### Step 21a: Generated Questions Overview

![Interview Questions](./airecruiterimages/Step021a_InterviewQuestionsBasedOnSourceCode.png)

AI Recruiter 2.0 automatically generates **personalized technical questions** based on the candidate's code:

**Question Categories:**

1. **Code Understanding (5 questions)**
2. **Bug Fixing (3 questions)**
3. **Optimization (4 questions)**
4. **Architecture & Design (4 questions)**
5. **Security (2 questions)**
6. **Testing (2 questions)**

**Sample Questions:**

**Q1: Code Understanding**
"I noticed your `solve_sudoku` function uses a three-level solving strategy. Can you walk me through why you chose this particular decomposition? What are the trade-offs between depth-first and breadth-first approaches for sudoku solving?"

- **Difficulty**: Medium
- **Topics**: Algorithm design, Problem decomposition
- **Expected Duration**: 5-7 minutes
- **Evaluation Criteria**:
  - Understanding of algorithm strategy
  - Ability to discuss trade-offs
  - Knowledge of alternative approaches

**Q2: Bug Identification**
"In your code, I see you cast a 2D array to `int**` on line 148. Can you explain what this does and whether it's safe in C? How would you fix this if it causes issues on different platforms?"

- **Difficulty**: Medium-Hard
- **Topics**: C memory model, Pointer arithmetic, Type safety
- **Expected Duration**: 8-10 minutes
- **Evaluation Criteria**:
  - Understands pointer vs array decay
  - Recognizes undefined behavior
  - Can propose correct solution

**Q3: Optimization**
"Your code calls `print_sudoku` multiple times during solving. If we were to process millions of puzzles, how would you optimize this? What data structures or algorithms might help?"

- **Difficulty**: Medium
- **Topics**: Performance optimization, Profiling, Caching
- **Expected Duration**: 10-12 minutes
- **Evaluation Criteria**:
  - Identifies bottleneck
  - Proposes concrete optimizations
  - Understands big-O implications

### Step 21b: Question Details with Context

![Question Details](./airecruiterimages/Step021b_InterviewQuestionDetails.png)

Each question includes **rich context** for the interviewer:

**Question 4: Architecture & Design**

**Question:**
"Your test suite in `test_sudoku.c` doesn't actually link to your solver implementation. How would you restructure this project to enable proper unit testing? What testing strategies would you use?"

**Context for Interviewer:**
- **Code Reference**: test_sudoku.c:6-9 (stub `solveSudoku` function)
- **Issue Detected**: Test isolation bug found by knowledge graph analysis
- **Related Finding**: "Test functions have zero incoming edges in call graph"

**Ideal Answer Should Include:**
1. Create header file (sudoku.h) with function declarations
2. Link test suite against actual implementation
3. Use mocking for isolated unit tests
4. Implement fixture setup/teardown for test data
5. Discuss test pyramid (unit → integration → E2E)

**Follow-up Questions:**
- "How would you test the `solve_sudoku_1st_level` function in isolation?"
- "What's your approach to testing functions with global state?"
- "Have you used test coverage tools like gcov?"

**Scoring Rubric:**
- **Excellent (4/4)**: Comprehensive testing strategy, mentions mocking, fixtures, coverage
- **Good (3/4)**: Understands header files, linking, basic testing concepts
- **Fair (2/4)**: Identifies the problem, proposes partial solution
- **Poor (1/4)**: Doesn't recognize issue or proposes invalid solution

**Red Flags:**
- Dismisses testing as "not important for small projects"
- Doesn't understand header files in C
- Proposes copy-pasting code instead of linking

---

## Step 22: Workflow Timing and Performance Analysis

![Workflow Timing](./airecruiterimages/Step022_WorkflowTimingAndAnalysis.png)

The **Workflow Timing** tab provides transparency into processing time:

### Execution Timeline:

**Phase 1: Document Processing (90 seconds)**
- Extract Resume Text: 84.86 seconds
- Extract JD Text: 85.18 seconds
- *Observation*: Slow due to PDF parsing with table detection

**Phase 2: NER Analysis (120 seconds)**
- Resume NER (OpenAI): 45 seconds
- JD NER (OpenAI): 42 seconds
- *Optimization opportunity*: Run in parallel

**Phase 3: GitHub Analysis (180 seconds)**
- Repository clone: 30 seconds
- Code ingestion: 60 seconds
- File parsing: 90 seconds

**Phase 4: Multi-LLM Evaluation (300 seconds)**
- OpenAI analysis: 60 seconds
- Mistral analysis: 65 seconds
- Claude analysis: 70 seconds
- Gemini analysis: 55 seconds
- Grok analysis: 50 seconds
- *Note*: Run in parallel, wall-clock time = 70 seconds (slowest model)

**Phase 5: Knowledge Graph (120 seconds)**
- AST parsing: 45 seconds
- Entity extraction: 30 seconds
- Relationship mapping: 25 seconds
- Neo4j upload: 20 seconds

**Phase 6: Quality Metrics (60 seconds)**
- Matrix computation: 20 seconds
- Security analysis: 15 seconds
- Architecture scoring: 15 seconds
- Quality aggregation: 10 seconds

**Phase 7: Report Generation (30 seconds)**
- Diagram generation: 15 seconds
- Question generation: 10 seconds
- Export formatting: 5 seconds

### Total Time: ~8 minutes 30 seconds

### Performance Characteristics:

**Bottlenecks:**
1. PDF text extraction (slowest)
2. LLM API calls (network latency)
3. Neo4j batch operations (large repos)

**Optimization Strategies:**
1. **Caching**: Store parsed resumes for 24 hours
2. **Parallelization**: Run LLM calls concurrently (already implemented)
3. **Incremental Processing**: Process repos in background, reuse for future candidates
4. **Rate Limiting**: Batch API calls to avoid throttling

**Scalability:**
- **Current**: ~7 workflows/hour (sequential)
- **With Parallelization**: ~50 workflows/hour (7 parallel workers)
- **With Caching**: ~100 workflows/hour (cache hit rate ~60%)

---

## Step 23: Workflow Dashboard - Managing Multiple Candidates

### Step 23a: Active Workflows View

![Workflow Dashboard 1](./airecruiterimages/Step023a_WorkflowDashboard.png)

The **Workflow Dashboard** provides a central hub for managing all candidate evaluations:

### Dashboard Features:

**Workflow List:**
Each row shows:
- **Candidate Name**: Extracted from resume
- **Job Title**: Role being evaluated for
- **Status**: Running / Completed / Failed
- **Progress**: Real-time percentage (0-100%)
- **Score**: Final score (shown after completion)
- **Created**: Submission timestamp
- **Actions**: View, Retry, Delete

**Filtering & Search:**
- Filter by status: All / Running / Completed / Failed
- Search by candidate name or job title
- Sort by: Date, Score, Status

**Batch Operations:**
- Select multiple workflows
- Bulk export reports
- Comparative analysis

### Step 23b: Workflow Details Panel

![Workflow Dashboard 2](./airecruiterimages/Step023b_WorkflowDashboard.png)

Clicking a workflow expands details:

**Workflow ID**: 8ed52448-b3db-4dff-b3bb-d006f537778b

**Candidate**: Prakalya Resume v2
**Position**: Oracle Software Developer 2
**Submitted**: 2025-10-05 14:35:22
**Completed**: 2025-10-05 14:43:56
**Duration**: 8 minutes 34 seconds

**Files Uploaded:**
- Resume: Prakalya_Resume.v2.pdf (107 KB)
- Job Description: OracleSoftwareDeveloper2.docx (23 KB)

**GitHub Repositories Analyzed:**
1. github.com/prakalya/sudoku-solver (C, 850 LOC)
2. github.com/prakalya/code-evaluator (Python, 2,340 LOC)
3. github.com/prakalya/react-dashboard (JavaScript, 1,560 LOC)

**Final Assessment:**
- **Score**: 55.4/100 (Grade C)
- **Recommendation**: Consider with Reservations
- **Confidence**: 75%

**Quick Actions:**
- [View Full Report]
- [Download PDF]
- [Share via Email]
- [Schedule Interview]
- [Compare with Other Candidates]

### Dashboard Analytics:

**Summary Statistics:**
- Total Candidates Evaluated: 45
- Average Score: 62.3/100
- Pass Rate: 67% (score ≥ 60)
- Average Processing Time: 9.2 minutes
- Most Common Weaknesses: Documentation (avg 35%), Testing (avg 40%)

---

## Conclusion

AI Recruiter 2.0 represents a paradigm shift in technical hiring by combining:

1. **Multi-LLM Analysis**: Ensemble scoring across 5 AI models reduces bias and increases confidence
2. **Knowledge Graph Technology**: Graph theory and matrix mathematics provide rigorous, explainable quality metrics
3. **Automated Assessment**: End-to-end workflow from resume upload to interview questions
4. **Transparency**: Every score is traceable to mathematical formulas and specific code findings
5. **Efficiency**: Complete evaluation in 8-12 minutes vs. hours of manual review

### Key Differentiators:

**vs. Traditional ATS:**
- Traditional: Keyword matching, manual review
- AI Recruiter 2.0: Deep code analysis, mathematical scoring

**vs. Other AI Recruiters:**
- Others: Single LLM, subjective scores
- AI Recruiter 2.0: Ensemble methods, graph-based metrics

**vs. Code Assessment Platforms:**
- Others: Take-home challenges, manual grading
- AI Recruiter 2.0: Analyzes real GitHub projects, automated evaluation

### Impact:

- **Hiring Managers**: Save 10-20 hours per position
- **Candidates**: Receive meaningful feedback on actual code
- **Organizations**: Make data-driven, auditable hiring decisions
- **DEI**: Reduce bias through systematic, transparent evaluation

### Future Enhancements:

1. Real-time video interview analysis
2. Predictive performance modeling
3. Continuous skill tracking
4. Custom quality metrics per company
5. Hypergraph analysis for multi-way code relationships

---

**Thank you for exploring AI Recruiter 2.0!**

For more information:
- Repository: https://github.com/satishkumarvenkatasamy/ai-recruiter-2.0
- Contact: sativenk@gmail.com
- LinkedIn: https://www.linkedin.com/in/sativenk/
