# PRD: Claude Code ROI Calculator for PMs & PMMs

## Overview

A simple, interactive web calculator that shows product managers and product marketing managers how much time they'd save per week by using Claude Code. The calculator takes real workflow inputs and outputs concrete time savings, helping prospects quickly understand the value proposition before signing up.

## Problem Statement

**Target users:** PMs and PMMs at Series B SaaS companies (see [persona.md](persona.md) for full context)

**Core challenge:** Non-technical roles are skeptical that AI coding tools are relevant for them. They see Claude Code as "for engineers" and don't immediately understand how it fits into their workflow.

**Current objection:** "I already use ChatGPT for productivity. Why do I need another AI tool?"

**What's missing:** A concrete, personalized estimate of time savings that maps to their actual job responsibilities. They need to see the ROI before investing time in a trial.

## Goals

### Primary Goal
Convert landing page visitors into trial signups by demonstrating clear, quantifiable time savings (5-10+ hours/week).

### Secondary Goals
1. Educate prospects on which tasks Claude Code can help with
2. Collect data on what tasks take the most time (for product and marketing insights)
3. Create a shareable artifact ("I could save 8 hours/week!") for social proof

### Success Metrics
- **Conversion rate:** % of calculator users who sign up for a trial
- **Completion rate:** % of users who complete all inputs
- **Viral coefficient:** % of users who share their results on LinkedIn/Twitter
- **Data insight:** Distribution of time spent across different tasks (informs content strategy)

## User Stories

### As a PMM (persona: Sarah Chen)
> "I spend 3 hours/week researching competitors, 5 hours writing content, and 2 hours asking engineering questions. I want to see how much time Claude Code could give me back so I can decide if it's worth trying."

**Acceptance criteria:**
- Input fields map to tasks I actually do (not generic "coding" tasks)
- Output shows weekly and monthly time savings
- Calculator explains *how* Claude Code helps with each task
- I can share my result on LinkedIn to show my team

### As a PM (persona: Alex Martinez)
> "I spend 6 hours/week writing PRDs, 4 hours in technical discussions, and 2 hours reviewing code. I want to understand if Claude Code is relevant for product managers or just for engineers."

**Acceptance criteria:**
- Input fields include PM-specific tasks (writing specs, technical research)
- Calculator shows I'm not alone in spending this much time on these tasks
- Output suggests specific use cases for PMs (not just PMMs)

### As a VP of Product/Marketing
> "My team of 3 PMMs is underwater. I want to understand if Claude Code could help them ship faster without hiring another headcount."

**Acceptance criteria:**
- Calculator shows total team time savings (multiplied by team size)
- Output includes annual time savings and rough cost savings
- I can see what tasks are eating up the most time across roles

## Functional Requirements

### Input Fields

**1. Technical Q&A and Research**
- **Label:** "Hours per week asking engineers questions or researching technical details"
- **Default value:** 3 hours
- **Range:** 0-20 hours
- **Claude Code efficiency:** 70% time savings
- **Explanation:** "Claude Code can answer most technical questions instantly by reading your codebase"

**2. Competitive Intelligence**
- **Label:** "Hours per week analyzing competitor features, APIs, or products"
- **Default value:** 2 hours
- **Range:** 0-15 hours
- **Claude Code efficiency:** 60% time savings
- **Explanation:** "Claude Code can analyze competitor APIs, documentation, and open-source code to extract insights"

**3. Writing PRDs and Specs**
- **Label:** "Hours per week writing product requirements, specs, or technical documentation"
- **Default value:** 4 hours
- **Range:** 0-20 hours
- **Claude Code efficiency:** 50% time savings
- **Explanation:** "Claude Code helps draft specs based on existing code patterns and can validate technical feasibility"

**4. Content Creation**
- **Label:** "Hours per week writing release notes, blog posts, or sales collateral"
- **Default value:** 5 hours
- **Range:** 0-20 hours
- **Claude Code efficiency:** 60% time savings
- **Explanation:** "Claude Code can generate release notes from commits, explain features in plain English, and draft technical content"

**5. Code Review and Prototyping**
- **Label:** "Hours per week reviewing code, building prototypes, or validating implementations"
- **Default value:** 2 hours
- **Range:** 0-15 hours
- **Claude Code efficiency:** 50% time savings
- **Explanation:** "Claude Code can review PRs, explain implementation details, and help you prototype faster"

**6. Team Size (Optional)**
- **Label:** "How many PMs/PMMs on your team?"
- **Default value:** 1
- **Range:** 1-20
- **Purpose:** Multiply individual savings to show team-level impact

### Calculation Logic

```
For each task category:
  time_saved = (hours_per_week * efficiency_percentage)

Total weekly savings = sum of all time_saved values
Total monthly savings = weekly_savings * 4.3
Total annual savings = monthly_savings * 12

If team_size > 1:
  Team weekly savings = total_weekly_savings * team_size
  Team annual savings = total_annual_savings * team_size
```

### Output Display

**Primary result (large, bold):**
```
You could save 8.2 hours per week with Claude Code
```

**Breakdown by category:**
- Technical Q&A: 2.1 hours/week saved
- Competitive Intelligence: 1.2 hours/week saved
- Writing PRDs: 2.0 hours/week saved
- Content Creation: 3.0 hours/week saved
- Code Review: 1.0 hours/week saved

**Extended view:**
- Monthly savings: 35 hours/month
- Annual savings: 426 hours/year (10.6 work weeks)
- What you could do with that time:
  - Ship 12 more blog posts per quarter
  - Launch 2 additional products per year
  - Reduce time-to-market by 15%

**Team view (if team_size > 1):**
```
Your team of 3 could save 25 hours/week
That's 1,278 hours/year — equivalent to hiring 0.6 FTEs
```

**Call to action:**
```
[Primary button] Try Claude Code Free
[Secondary button] Share Your Results
```

### Social Sharing

**Pre-filled LinkedIn post:**
```
I just calculated that I could save 8 hours/week using @Claude Code for product work.

That's time I could spend on strategy instead of chasing down technical details.

Worth a look if you're a PM/PMM who wants to ship faster 👇
[Link to calculator]
```

**Pre-filled Twitter post:**
```
Turns out I spend 8+ hours/week on tasks @ClaudeCode could handle in minutes

Time to try it out: [link]
```

## Non-Functional Requirements

### Performance
- Calculator should update results in real-time (< 100ms latency)
- Page should load in < 2 seconds on 3G connection
- Works on mobile, tablet, and desktop

### Design
- Clean, minimal interface (similar to linear.app or stripe.com calculators)
- Inline tooltips to explain what each input means
- Visual breakdown (bar chart or pie chart) showing where time is spent
- Professional, not gimmicky — this is a decision-making tool, not a toy

### Data Collection (Optional)
- Track anonymized input distributions to understand:
  - What tasks take the most time for PMs vs PMMs?
  - What's the average time savings across all users?
  - Which inputs correlate most with trial signups?
- No PII collection; purely for product insights

### Accessibility
- WCAG 2.1 AA compliant
- Keyboard navigable
- Screen reader friendly

## User Flow

1. **Entry:** User lands on calculator (linked from landing page, LinkedIn post, or email campaign)
2. **Input:** User adjusts sliders/inputs for each task category
3. **Output:** Results update in real-time as they adjust inputs
4. **Social proof:** "Join 1,200+ PMs and PMMs using Claude Code" (dynamic count)
5. **CTA:** Primary button to start free trial; secondary button to share results
6. **Follow-up:** Email drip campaign for users who calculate but don't sign up

## Edge Cases

### User inputs zero hours for everything
**Behavior:** Show message: "Looks like you're already moving fast! Claude Code can still help with technical Q&A and competitive research as your workload grows."

### User inputs 40+ hours/week total
**Behavior:** Show message: "That's a lot of time! Claude Code can help, but you might also want to talk to your manager about workload prioritization."

### User is skeptical of efficiency percentages
**Behavior:** Add footnote: "Time savings based on case studies with 50+ PMs and PMMs. Your mileage may vary depending on workflow and codebase complexity."

## Open Questions

1. **Should we include a salary input to show cost savings in dollars?**
   - Pro: Makes ROI even more concrete for managers
   - Con: Feels invasive; may reduce completion rate
   - **Decision:** No for V1. Test in V2 if conversion rate is low.

2. **Should we gate the results behind an email capture?**
   - Pro: Builds email list for nurture campaigns
   - Con: Reduces completion rate and social sharing
   - **Decision:** No gate for V1. Focus on virality and education over lead gen.

3. **Should we show industry benchmarks ("You spend 20% more time on competitive research than average")?**
   - Pro: Social proof and normalization
   - Con: Requires significant data collection first
   - **Decision:** No for V1. Add in V2 after we have baseline data.

4. **Should we differentiate between PM and PMM personas?**
   - Pro: More personalized messaging
   - Con: Adds complexity; many users wear both hats
   - **Decision:** Single calculator with inputs relevant to both roles. Consider A/B test in V2.

## Success Criteria

**Must have (V1):**
- ✅ All 5 input categories functional
- ✅ Real-time calculation and display
- ✅ Mobile-responsive design
- ✅ CTA to free trial
- ✅ Social share buttons

**Should have (V1):**
- ✅ Team size multiplier
- ✅ Breakdown by category
- ✅ Extended view (annual savings, "what you could do")
- ✅ Tooltips explaining each input

**Nice to have (V2):**
- ⬜ Anonymous data collection for insights
- ⬜ Industry benchmarks
- ⬜ Persona toggle (PM vs PMM)
- ⬜ Cost savings in dollars
- ⬜ Exportable PDF report

## Launch Plan

**Pre-launch:**
- Build calculator as standalone page: `/roi-calculator`
- Add link to main landing page nav
- Create 3-5 LinkedIn posts showcasing example results
- Prep email campaign: "Calculate how much time you could save"

**Launch day:**
- Post to LinkedIn (personal account + company page)
- Share in 5-10 product marketing Slack communities
- Email existing trial users who haven't converted (re-engagement)

**Post-launch (Week 1-2):**
- Monitor completion rate and conversion rate
- A/B test: Calculator as landing page vs. calculator as secondary page
- Iterate on copy based on user feedback

**Long-term:**
- Use data to inform content strategy (write case studies for highest-time tasks)
- Build similar calculators for other personas (engineers, founders)

## Technical Implementation

**Tech stack:**
- Vanilla HTML/CSS/JavaScript (no framework required for V1)
- Hosted on same domain as landing page: `lukestahl.io/roi-calculator`
- Analytics: Plausible or Google Analytics for page views, completion rate

**Estimated effort:**
- Design: 4 hours
- Frontend development: 8 hours
- Testing: 2 hours
- **Total: ~2 days**

## Appendix: Sample Calculations

### Persona 1: Sarah (PMM at Series B SaaS)
- Technical Q&A: 3 hrs/week → **2.1 hrs saved**
- Competitive Intel: 2 hrs/week → **1.2 hrs saved**
- Writing PRDs: 2 hrs/week → **1.0 hrs saved**
- Content Creation: 5 hrs/week → **3.0 hrs saved**
- Code Review: 1 hr/week → **0.5 hrs saved**
- **Total: 7.8 hours/week saved (340 hours/year)**

### Persona 2: Alex (PM at Series B SaaS)
- Technical Q&A: 4 hrs/week → **2.8 hrs saved**
- Competitive Intel: 3 hrs/week → **1.8 hrs saved**
- Writing PRDs: 6 hrs/week → **3.0 hrs saved**
- Content Creation: 2 hrs/week → **1.2 hrs saved**
- Code Review: 3 hrs/week → **1.5 hrs saved**
- **Total: 10.3 hours/week saved (535 hours/year)**

### Team Scenario: VP Marketing with 3 PMMs
- Individual savings: 7.8 hrs/week
- Team savings: 23.4 hrs/week (1,217 hrs/year)
- Equivalent to: 0.58 FTE (assuming 2,080 work hours/year)
- Message: "Save enough time to ship a major product launch without hiring another PMM"
