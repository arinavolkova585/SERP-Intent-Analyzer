# SERP-Intent-Analyzer
An n8n workflow that analyzes Google SERP results for a keyword and classifies search intent, audience, content angle, and AEO recommendations using Gemini AI

# n8n Canvas
<img width="1265" height="412" alt="image" src="https://github.com/user-attachments/assets/863c238a-1820-4b02-bdb4-d8466279d1f3" />

# Output 
<img width="834" height="452" alt="image" src="https://github.com/user-attachments/assets/a247b611-fb90-4a80-9286-dca77df56143" />

## Live chat URL: https://arinavolkova.app.n8n.cloud/workflow/q7Qc0YMKO9hPpidt 
note: only works till June 4th, 2026

# Prompt
You are an SEO and content strategy analyst. A user has searched for the keyword: "{{ $('When chat message received').item.json.chatInput }}"

Here are the top 10 Google search results for this keyword:
{{ $json.organic_results.map(r => `Title: ${r.title}\nSnippet: ${r.snippet}`).join('\n\n') }}

Analyze these results and return the following in clean structured format:

1. SEARCH INTENT: Classify as one of: Informational, Commercial, Navigational, or Transactional. Explain in 2 sentences why.

2. AUDIENCE: Who is most likely searching this keyword and what stage of the funnel are they in?

3. CONTENT ANGLE: Recommend the best content angle to rank for this keyword and appear in AI search results (AEO). Be specific.

4. RECOMMENDED FORMAT: What content format works best for this keyword (FAQ, how-to guide, comparison, listicle, etc.) and why.

5. AEO TIP: One specific recommendation to make this content extractable by AI search engines like ChatGPT or Google AI Overviews.

