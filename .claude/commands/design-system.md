# Design System — Load UI Context Before Frontend Work

Load or generate the project's design system reference to ensure visual consistency across all UI work.

## Steps

1. **Check for existing design system reference:**
   - Look for `.claude/reference/design-system.md`.
   - If it exists, proceed to step 4 (load it).
   - If it does not exist, proceed to step 2 (offer to generate one).

2. **Offer to generate a design system reference:**
   - Ask: "No design system reference found. Want me to analyze the project and generate one?"
   - If declined, print: "Proceeding without a design system reference. UI consistency is not guaranteed." and stop.
   - If accepted, proceed to step 3.

3. **Analyze the project and generate a design system doc:**
   - Search for CSS, SCSS, LESS, Tailwind config, styled-components, or other styling files.
   - Search for component library usage (e.g., imports from UI libraries, component directories).
   - Extract patterns for:
     - **Colors**: palette, semantic color names, CSS variables, theme tokens
     - **Typography**: font families, sizes, weights, line heights
     - **Spacing**: margin/padding scale, gap patterns, consistent units
     - **Components**: common UI components, naming conventions, composition patterns
     - **Layout**: grid system, breakpoints, responsive approach
     - **Shadows, borders, radius**: elevation and shape patterns
   - If a Tailwind config, theme file, or CSS variables file exists, use it as the primary source of truth.
   - If no styling patterns are found, generate a minimal starter design system with sensible defaults.
   - Create `.claude/reference/` directory if needed.
   - Save the generated reference to `.claude/reference/design-system.md`.

4. **Load and internalize the design system:**
   - Read `.claude/reference/design-system.md` fully.
   - Confirm to the user what design system is now active:
     - Name or description of the system
     - Key color palette (primary, secondary, accent, etc.)
     - Typography stack
     - Core constraints (e.g., "use only 4px spacing increments", "max content width 1200px")

5. **State readiness:**
   - Print: "Design system loaded. All UI work in this session will follow these constraints."
   - List the top 3-5 constraints that are most important to remember.

## Notes
- Run this command BEFORE starting any UI or frontend work.
- The generated reference is a living document. Update it when the design system evolves.
- This command does not install any packages or modify application code. It only creates/reads reference documentation.
- If the project has no frontend, say so and stop early.
