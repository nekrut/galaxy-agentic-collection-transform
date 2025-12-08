Research Galaxy's tools API and create RESEARCH_API.md.

Read PROBLEM_AND_GOAL.md to understand the context and objectives.

Accept optional argument: path to Galaxy directory (defaults to ~/workspace/galaxy)

Read and summarize:
1. lib/galaxy/webapps/galaxy/api/tools.py - The tools API implementation
2. lib/galaxy_test/api/test_tools.py - API test examples
3. https://training.galaxyproject.org/training-material/topics/dev/tutorials/bioblend-api/slides-plain.html - BioBlend API tutorial

Focus on:
- How to invoke tools via the API
- Collection handling in tool API calls
- Input/output formats for collections
- Parameter passing and configuration
- Examples from tests showing real usage patterns

IMPORTANT - API Input Format Requirements (from real-world testing, see issue #7):
- Data inputs (collections/datasets) require `{"values": [{"src": "...", "id": "..."}]}` wrapper
- Conditional parameters use pipe notation: `"how|filter_source"` not nested `"how": {"filter_source": ...}`
- Incorrect format causes SILENT failures - Galaxy uses defaults without error
- Verify format by checking `/api/tools/{tool_id}/build` endpoint response structure

Output: Create/update RESEARCH_API.md with comprehensive API usage guide.
