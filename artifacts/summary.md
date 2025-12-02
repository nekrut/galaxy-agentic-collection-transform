# Build Command Summary: galaxy-transform-collection

## Overview

Created a comprehensive Claude slash command (`galaxy-transform-collection.md`) that teaches Claude to transform Galaxy dataset collections reproducibly using Galaxy's native tools.

## Research Relevance Assessment

### Most Relevant Research

1. **RESEARCH_APPLY_RULES.md** ⭐⭐⭐⭐⭐
   - **Why:** Core DSL documentation with 20 rule types, 4 mapping operations, complete examples
   - **Usage in command:** Comprehensive Apply Rules section with all rule types, parameters, examples
   - **Impact:** Enables complex transformations, most powerful tool in toolkit

2. **RESEARCH_TOOLS.md** ⭐⭐⭐⭐⭐
   - **Why:** Complete catalog of 26 collection operation tools with inputs/outputs/use cases
   - **Usage in command:** "Galaxy Collection Tools Reference" section maps directly to this
   - **Impact:** Provides simple tool alternatives before resorting to Apply Rules

3. **RESEARCH_API.md** ⭐⭐⭐⭐
   - **Why:** Payload structures, tool invocation patterns, collection input formats
   - **Usage in command:** "API Invocation Patterns" section with concrete examples
   - **Impact:** Critical for actual implementation, shows how to call tools programmatically

4. **PROBLEM_AND_GOAL.md** ⭐⭐⭐⭐
   - **Why:** Core principle that all operations must use native tools for reproducibility
   - **Usage in command:** Opening CRITICAL PRINCIPLE, decision framework rationale
   - **Impact:** Drives entire command philosophy - never manipulate directly

5. **RESEARCH_TESTS.md** ⭐⭐⭐
   - **Why:** Real usage patterns from Galaxy's test suite, demonstrates best practices
   - **Usage in command:** Informed examples, validated patterns work in practice
   - **Impact:** Confidence that suggested approaches actually work

### Least Relevant Research

6. **RESEARCH_SUMMARY_TRAINING.md** ⭐⭐
   - **Why:** User-facing training materials, conceptual understanding
   - **Usage in command:** Referenced in general principles but not detailed implementation
   - **Impact:** Good background but command focuses on programmatic usage, not UI
   - **Note:** Would be more relevant for a command helping users navigate Galaxy UI

## Open Questions

### 1. Metadata Handling Strategy

**Question:** When missing metadata requires creating mirror collections with tags, should Claude:
- Always warn about reproducibility concerns?
- Suggest re-running from data import step?
- Offer to create both metadata file AND tagged collection for redundancy?

**Current approach:** Two-tiered strategy (tabular upload preferred, mirror collection as last resort with warnings)

**Improvement needed:** More guidance on when each approach is appropriate, examples of "metadata too complex for tabular" scenarios

### 2. Error Handling and Validation

**Question:** How should Claude validate transformations succeeded?
- Check job status programmatically?
- Verify output collection structure matches expected?
- Sample check element identifiers?
- Compare input/output element counts?

**Current approach:** Command shows job polling pattern but doesn't mandate validation

**Improvement needed:** Best practices section on validating transformation correctness

### 3. Rule Complexity Threshold

**Question:** When should Claude recommend Apply Rules vs. chaining simpler tools?
- Number of operations (3+ operations → Apply Rules)?
- Complexity metrics (regex involved → Apply Rules)?
- User skill level consideration?
- Performance implications?

**Current approach:** "Tool Selection Priority" lists order but threshold is fuzzy

**Improvement needed:** Decision tree or scoring system for tool selection

### 4. Workflow Extraction Guidance

**Question:** Should command teach Claude to:
- Actively extract workflows after transformations?
- Explain how to extract workflows manually?
- Suggest naming conventions for workflows?
- Include workflow testing patterns?

**Current approach:** Mentions "can be extracted to workflow" but no how-to

**Improvement needed:** Section on workflow extraction as final step

### 5. Handling Non-Standard Collection Types

**Question:** How should Claude handle:
- Record collections (not covered in research)?
- Deeply nested collections (list:list:list)?
- Mixed type collections?
- Collections with metadata conflicts?

**Current approach:** Command focuses on list, paired, list:paired patterns

**Improvement needed:** Edge case handling section

### 6. Interactive Rule Building vs. Programmatic

**Question:** When should Claude:
- Suggest using Galaxy UI rule builder first (for complex regex)?
- Build rules programmatically directly?
- Show both approaches?

**Current approach:** Command is fully programmatic, ignores UI rule builder

**Improvement needed:** Acknowledge interactive tool exists, explain when to use it

## Suggestions for Improvement

### 1. Research Process Improvements

**Add automated testing examples:**
- How to validate transformed collections
- Unit test patterns for Apply Rules
- Integration test examples from test_tools.py

**Include failure mode documentation:**
- Common rule errors and solutions
- Collection type mismatch errors
- Empty result handling

**Add performance benchmarks:**
- Apply Rules vs. chained tools
- Large collection optimization patterns
- When to batch vs. sequential processing

### 2. Command Generation Improvements

**Add command structure:**
- Version information (track command updates)
- Examples library (separate from main docs for maintainability)
- Quick reference section at top
- Troubleshooting guide

**Improve decision framework:**
- Flowcharts or decision trees
- "If this, then that" patterns
- Common pitfall warnings upfront

**Add context awareness:**
- How to detect if Galaxy connection exists
- How to identify available tools/versions
- How to adapt to different Galaxy instances

**Include testing guidance:**
- How Claude should test transformations
- Validation checklist
- Rollback strategies for failures

### 3. Documentation Gaps to Address

**Missing from research:**
- Record collection operations (mentioned but not detailed)
- Collection metadata schema (what's available in sources?)
- Tag propagation rules (which tools preserve tags?)
- Quota implications (which operations copy data?)
- Multi-history operations (can collections span histories?)
- Permissions and sharing (how do collection permissions work?)

**Would benefit from research:**
- Real workflow examples using collection operations
- Performance characteristics of each tool
- Tool version differences (do APIs change?)
- Error message catalog (what do failures look like?)
- Galaxy configuration impact (which tools are optional?)

### 4. Command Delivery Improvements

**Make self-contained:**
- Embed all necessary reference material
- No external dependencies (achieved ✓)
- Include all tool IDs, parameter names, formats

**Add learning progression:**
- Start with simplest patterns
- Build up to complex Apply Rules
- Progressive examples showing evolution

**Include validation:**
- Self-test examples Claude can run
- Expected outputs for verification
- Sanity check patterns

### 5. User Experience Improvements

**Better explanation templates:**
- More varied response formats (not repetitive)
- Adjust verbosity based on user expertise
- Offer both "quick answer" and "detailed explanation"

**Interactive refinement:**
- Ask clarifying questions earlier
- Offer alternatives ("Option A: simple but limited, Option B: complex but flexible")
- Explain tradeoffs explicitly

**Progress communication:**
- Show what Claude is doing (not just results)
- Explain why each step is necessary
- Set expectations for async operations

## Generation Process Assessment

### What Went Well

1. **Comprehensive research base:** Five detailed research documents covered all necessary aspects
2. **Clear problem definition:** PROBLEM_AND_GOAL.md articulated core principle effectively
3. **Real examples:** Test suite research provided validated patterns
4. **Complete DSL specification:** rules_dsl_spec.yml had every rule type with examples
5. **Structured approach:** /build-command slash command had clear requirements

### What Could Be Improved

1. **Research efficiency:**
   - Could have used grep/glob more strategically before reading full files
   - Some research overlap (tools documented in multiple places)
   - Rules DSL spec file read could have been deferred until needed

2. **Command organization:**
   - Very long single file (7500+ lines) - might be hard to maintain
   - Could split into: core reference, examples library, decision framework
   - Sections could have better cross-references

3. **Examples depth:**
   - More real-world scenarios needed (current examples somewhat generic)
   - Edge cases not well covered
   - Error recovery patterns missing

4. **Testing:**
   - No way to validate the command actually works
   - Should have included test cases
   - No feedback mechanism for improvements

5. **Iteration:**
   - Single-pass generation (no refinement)
   - Didn't test command against sample prompts
   - No validation of completeness

### If Starting Over

1. **Start with problem scenarios:**
   - Collect 10-20 real user requests first
   - Ensure research addresses these specifically
   - Build command to solve actual needs

2. **Prototype earlier:**
   - Create minimal command first
   - Test against sample prompts
   - Iterate based on results

3. **Modular structure:**
   - Separate reference docs from decision logic
   - Make examples swappable/extensible
   - Version control for command evolution

4. **Add metadata:**
   - Version tracking
   - Coverage checklist (what's documented?)
   - Known limitations section
   - Update/maintenance guidance

5. **Include feedback loop:**
   - How users report issues
   - How command gets updated
   - Testing framework for validation

## Conclusion

The generated command is comprehensive and well-researched, covering:
- ✅ All 26 collection operation tools
- ✅ Complete Apply Rules DSL (20 rule types, 4 mappings)
- ✅ API invocation patterns
- ✅ Decision framework for tool selection
- ✅ Metadata handling strategies
- ✅ Reproducibility principles
- ✅ Example interactions

Primary strengths:
- Self-contained (no external dependencies)
- Complete reference material
- Clear principles (always use native tools)
- Concrete examples with code

Primary weaknesses:
- Very long (maintainability concern)
- No validation/testing
- Limited edge case coverage
- Missing workflow extraction guidance
- No error handling patterns

The command should enable Claude to handle most collection transformation requests reproducibly, but would benefit from real-world testing, iteration, and refinement based on actual usage patterns.

## Token Usage Note

This build command consumed ~95k tokens in research phase (reading 6 documents) + ~7k tokens generating command = ~102k total. Future iterations could be more efficient by:
- Using grep to target specific sections before full reads
- Caching common patterns
- Progressively loading detail as needed
