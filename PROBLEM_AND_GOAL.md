# Problem and Goal

## The Problem

When users interact with Galaxy Dataset Collections through Claude, the AI can directly manipulate collections via the Galaxy API - filtering, splitting, reorganizing, and recreating collections on-the-fly. While this demonstrates Claude's capability to understand and execute complex data operations, it introduces several critical issues:

1. **Loss of Reproducibility**: Direct API manipulation creates ephemeral operations that exist only in the conversation context, similar to downloading a dataset, modifying it locally, and re-uploading. The transformation steps are lost.

2. **Workflow Extraction Impossible**: Since the collection operations happen outside of Galaxy's workflow system, they cannot be captured, shared, or reused as part of a reproducible analysis pipeline.

3. **Stochastic Analysis Steps**: Each API-based collection manipulation is a one-off operation. Re-running the "analysis" would require re-engaging with Claude, potentially producing different results or approaches.

4. **Non-Galactic Approach**: Galaxy has comprehensive, well-tested tools and techniques specifically designed for collection operations. Direct API manipulation bypasses these established patterns and best practices.

## The Goal

Build a Claude slash command that enables intelligent, reproducible collection operations by:

1. **Teaching Claude Galaxy's Native Tools**: Educate the AI about Galaxy's collection operation tools, the apply rules framework, and established techniques for collection manipulation.

2. **Preferring Tool-Based Operations**: Guide Claude to recommend and use Galaxy's built-in tools instead of direct API manipulation, ensuring all operations are captured in workflow-compatible formats.

3. **Maintaining Reproducibility**: Ensure all collection operations can be extracted into workflows, shared, and re-executed with consistent results.

4. **Leveraging Galaxy Expertise**: Utilize training materials, tool documentation, API patterns, and test examples to inform Claude's recommendations.

5. **Intelligent Decision Making**: Allow Claude to analyze the user's requirements and select the most appropriate Galaxy-native approach, whether that's collection operation tools, apply rules, or other established techniques.

## Success Criteria

- Claude recommends Galaxy tools over direct API manipulation
- All suggested operations can be captured in Galaxy workflows
- Operations are reproducible and shareable
- Recommendations align with Galaxy best practices and training materials
- Users maintain the convenience of conversational interaction while gaining the benefits of Galaxy's structured approach
