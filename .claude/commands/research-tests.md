Research Galaxy's collection operation tests and create RESEARCH_TESTS.md.

Read PROBLEM_AND_GOAL.md to understand the context and objectives.

Accept optional argument: path to Galaxy directory (defaults to ~/workspace/galaxy)

First read from artifacts/research/<latest_version>/:
1. RESEARCH_TOOLS.md - Previously researched tool information
2. RESEARCH_API.md - Previously researched API information

(Find latest version by listing artifacts/research/v* directories)

Use prior research as context - don't re-explain tools, just show test usage patterns.

Then read lib/galaxy_test/api/test_tools.py from Galaxy and summarize:
- Test examples for collection operations
- How apply rules are tested and used
- Real-world usage patterns
- Input/output structures for collection manipulation
- Edge cases and best practices demonstrated in tests

Focus particularly on apply rules examples and collection operation testing patterns.

Output: Create/update artifacts/research/v<N>/RESEARCH_TESTS.md with comprehensive test-based usage examples.

Version detection:
1. List directories in artifacts/research/ matching v*
2. Find latest version (highest number)
3. If RESEARCH_TESTS.md exists in latest version → create v<N+1>
4. If not exists → use latest version (continuing cycle)
5. Create version directory if needed, write output there
