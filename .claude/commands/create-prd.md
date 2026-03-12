# Create PRD — Product Requirements Document

Generate a comprehensive, actionable PRD for a feature or product idea.

**Feature/Idea:** $ARGUMENTS

## Steps

### 1. Understand the Idea

Parse the input above. If critical details are missing (who is this for? what problem does it solve? what type of product?), ask up to **3 clarifying questions** before proceeding.

### 2. Read Context

- Read `.claude/rules/architecture.md` to understand current technical capabilities and constraints.
- Check `.agents/plans/` for any existing PRDs or related plans to avoid duplication and maintain consistency.

### 3. Generate the PRD

Write a structured document covering all sections below. Adapt depth and detail based on available information — emphasize architecture and technical stack for highly technical products; emphasize user stories and experience for user-facing products.

Save the PRD to `.agents/plans/prd-YYYY-MM-DD-<short-slug>.md` using today's date.

---

## PRD Template

Use this structure for the generated document. Every section is required unless marked "(if applicable)".

```markdown
# PRD: <Feature/Product Name>

Date: <today>
Status: draft
Author: AI-assisted

---

## 1. Executive Summary

- Concise product/feature overview (2-3 paragraphs)
- Core value proposition
- MVP goal statement

## 2. Mission

- Product/feature mission statement
- Core principles (3-5 key principles guiding decisions)

## 3. Problem Statement

- What problem exists? Who has it? Why does it matter?
- Ground this in user needs, not implementation desire

## 4. Target Users

- Primary user personas
- Technical comfort level
- Key user needs and pain points
- Context in which users encounter this problem

## 5. MVP Scope

- **Must-Have:** Core functionality for MVP (use ✅ checkboxes)
- **Nice-to-Have:** Valuable additions that can be deferred (use ⬜ checkboxes)
- **Out of Scope:** Explicitly excluded — features deferred to future phases (use ❌ checkboxes)
- Group by categories where useful (Core Functionality, Technical, Integration, Deployment)

## 6. User Stories

- Primary user stories (5-8 stories) in format: "As a [user], I want to [action], so that [benefit]"
- Include concrete examples for each story
- Add technical user stories if relevant

## 7. Core Architecture & Patterns

- High-level architecture approach
- Directory structure (if applicable)
- Key design patterns and principles
- Technology-specific patterns
- Ground this in the current codebase and architecture rules

## 8. Features / Tools Specification

- Detailed feature specifications
- If building an agent: Tool designs with purpose, operations, and key features
- If building an app: Core feature breakdown with interaction details
- If building an API: Endpoint overview

## 9. Technology Stack

- Backend/Frontend technologies with versions
- Dependencies and libraries
- Optional dependencies
- Third-party integrations

## 10. Security & Configuration

- Authentication/authorization approach
- Configuration management (environment variables, settings)
- Security scope (in-scope and out-of-scope for MVP)
- Deployment considerations

## 11. API Specification (if applicable)

- Endpoint definitions
- Request/response formats
- Authentication requirements
- Example payloads

## 12. Success Metrics

- MVP success definition
- 2-4 measurable outcomes
- Functional requirements (use ✅ checkboxes)
- Quality indicators
- User experience goals

## 13. Implementation Phases

- Break down into 3-4 phases
- Each phase includes: Goal, Deliverables (✅ checkboxes), Validation criteria
- **Timeline estimate:** Rough t-shirt size (S/M/L/XL) with brief justification for each phase

## 14. Future Considerations

- Post-MVP enhancements
- Integration opportunities
- Advanced features for later phases

## 15. Risks & Open Questions

- 3-5 key risks with specific mitigation strategies
- Open questions that need more research
- Assumptions being made

## 16. Appendix (if applicable)

- Related documents and existing plans
- Key dependencies with links
- Repository/project structure notes
```

---

## Quality Checks

Before finalizing, verify:

- ✅ All required sections present and substantive
- ✅ User stories have clear benefits
- ✅ MVP scope is realistic and well-defined
- ✅ Technology choices are justified
- ✅ Implementation phases are actionable with timeline estimates
- ✅ Success metrics are measurable
- ✅ Consistent terminology throughout

## Style Guidelines

- **Tone:** Professional, clear, action-oriented
- **Format:** Use markdown extensively (headings, lists, code blocks, tables)
- **Checkboxes:** Use ✅ for must-have/in-scope items, ⬜ for nice-to-have, ❌ for out-of-scope
- **Specificity:** Prefer concrete examples over abstract descriptions
- **Length:** Comprehensive but scannable

## Output Confirmation

After creating the PRD:

1. Confirm the file path where it was saved
2. Show a brief summary: problem statement, must-have requirements, and top risks
3. Highlight any assumptions made due to missing information
4. Suggest running `/plan` next to break the PRD into implementable tasks

## Notes

- If critical information is missing, ask clarifying questions before generating
- Adapt section depth based on available details
- For highly technical products, emphasize architecture and technical stack
- For user-facing products, emphasize user stories and experience
- This command contains the complete PRD template structure — no external references needed
