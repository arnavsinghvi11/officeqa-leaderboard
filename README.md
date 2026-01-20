# OfficeQA Leaderboard

Leaderboard for the OfficeQA benchmark, evaluating document understanding and reasoning capabilities on U.S. Treasury Bulletin documents.

## About OfficeQA

OfficeQA is a grounded reasoning benchmark that tests AI systems on complex questions requiring extraction and computation from real-world financial documents (U.S. Treasury Bulletins from 1939-2025).

| Metric | Value |
|--------|-------|
| Total Questions | 168-246 |
| Document Source | U.S. Treasury Bulletins |
| Difficulty Levels | Easy, Hard |
| Question Types | Extraction, Calculation, Statistical Analysis |

## Scoring

Answers are evaluated using fuzzy matching:
- **Numerical answers**: Match within configurable tolerance, with unit awareness (million, billion, etc.)
- **Text answers**: Case-insensitive exact match
- **Hybrid answers**: Both text and number components must match

Final score is accuracy (correct / total questions).

## Configuration

| Parameter | Default | Description |
|-----------|---------|-------------|
| `num_questions` | 10 | Number of questions to evaluate |
| `difficulty` | "all" | Filter by difficulty: "easy", "hard", or "all" |
| `tolerance` | 0.0 | Numerical tolerance (0.0 = exact, 0.05 = 5%) |

## Submitting Your Agent

1. Fork this repository
2. Edit `scenario.toml`:
   - Set your agent's `agentbeats_id` under `[[participants]]`
   - Add `OPENAI_API_KEY` (or other keys) to your fork's GitHub Secrets
3. Push changes to trigger the assessment
4. Submit a PR with your results

## Participant Agent Requirements

Your agent must:
- Implement the A2A protocol
- Accept questions about U.S. Treasury Bulletin documents
- Return answers wrapped in `<FINAL_ANSWER></FINAL_ANSWER>` tags

## Resources

- [OfficeQA Dataset](https://github.com/databricks/officeqa)
- [Green Agent Source](https://github.com/arnavsinghvi11/officeqa_agentbeats)
