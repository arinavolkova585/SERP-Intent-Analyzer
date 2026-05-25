# SERP-Intent-Analyzer
An n8n workflow that analyzes Google SERP results for a keyword and classifies search intent, audience, content angle, and AEO recommendations using Gemini AI

# n8n Canvas
<img width="1265" height="412" alt="image" src="https://github.com/user-attachments/assets/863c238a-1820-4b02-bdb4-d8466279d1f3" />

# Output Examples
<img width="834" height="452" alt="image" src="https://github.com/user-attachments/assets/a247b611-fb90-4a80-9286-dca77df56143" />

Here's an analysis of the search results for "the best bank in canada":

SEARCH INTENT: Commercial The user is clearly looking to compare and evaluate different banking options to make an informed decision about which bank best suits their needs. The term "best" indicates a strong intent to find a service they might eventually "purchase" (open an account with), placing it beyond mere informational gathering.

AUDIENCE: The most likely audience is individuals (or potentially small businesses) actively considering opening a new bank account or switching their existing one in Canada. They are in the Consideration/Evaluation stage of the funnel. They have identified a need for banking services and are now researching various providers, comparing features, fees, customer service, and overall value before making a selection.

CONTENT ANGLE: "The Best Canadian Bank for Your Specific Needs: A Personalized Guide to Top Traditional, Digital, and Credit Union Options." This angle acknowledges the subjectivity of "best" and positions the content as a comprehensive, user-centric guide. It should categorize recommendations based on common user priorities (e.g., lowest fees, best digital experience, strongest branch network, best for students/newcomers, best interest rates, best for investing) while still providing an overall "top picks" summary.

RECOMMENDED FORMAT: A hybrid format combining a listicle with an in-depth comparison guide and an interactive element.

Listicle Component: Present a "Top X" list of banks, with each entry featuring a concise overview, key pros, and cons.
Comparison Guide Component: Dedicate sections to specific "best for" categories (e.g., "Best for No Fees," "Best for Digital Banking," "Best for In-Person Service").
Comparison Table: Include a sortable/filterable table summarizing key features (fees, interest rates, branch network, app rating, account types) for easy at-a-glance comparison.
Interactive Quiz (optional but highly recommended): A short quiz ("Which Canadian Bank is Best for You?") guiding users to personalized recommendations based on their answers to questions about their priorities. This format addresses different user scanning and reading preferences, providing quick answers while also offering deep dive opportunities.
AEO TIP: To make the content highly extractable by AI search engines, implement clear, descriptive headings (H2s and H3s) for each bank profile and for each "best for" category, then use concise bullet points or short, direct sentences to summarize key features, pros, and cons immediately beneath those headings.

Example Structure:
The Best Bank for Low Fees
Tangerine Bank
Pros: No monthly fees, good interest rates, cashback credit cards.
Cons: No physical branches, limited investment products.
Best for: Savers, budget-conscious individuals, digital-savvy users.
EQ Bank
Pros: High-interest savings accounts, no monthly fees, strong GIC rates.
Cons: No chequing accounts, limited lending products.
Best for: Maximizing savings, GIC investors.

# Live chat URL: https://arinavolkova.app.n8n.cloud/workflow/q7Qc0YMKO9hPpidt 
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

