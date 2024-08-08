# Standup Recap Action

GitHub Action to summarize Slack standup messages using AI for streamlined team updates

## Features

- Reads standup messages from a specified Slack channel
- Uses AI (ChatGPT or Claude) to generate concise summaries
- Posts the summary to Slack or saves as a GitHub artifact (JSON format is optional)
- Customizable time range and AI model selection
- Message Format or Slack
- Detect and create issue links (e.g., JIRA tickets)
- Tracks and reports team members missing from standup

## Usage

```yaml
- name: Generate Standup Recap
  uses: mariocesar/standup-recap@v1
  with:
    slack_token: ${{ secrets.SLACK_TOKEN }}
    channel_id: 'CXXXXXXXX'
    time_range: '24h'
    link_patterns:
      - pattern: "\\s(PROJ-\\d+)\\s"
        url: https://your-company.atlassian.net/browse/$1
      - pattern: "\\s(#\\d+)\\s"
        url: https://github.com/your-company/your-project/pull/$1
    system_prompt: |
      You are an AI assistant tasked with summarizing daily standup updates.
      Focus on key accomplishments, ongoing tasks, and blockers.
      Keep the tone professional but friendly.
    prompt_file: '.github/standup_prompt.md'
```
