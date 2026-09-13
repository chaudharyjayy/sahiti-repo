# Sahiti welcome-page refinement ideas

## Three possible directions

### Theme Name: Civic Clarity
Very Brief Intro: A calm, government-adjacent editorial direction that uses generous whitespace, confident navy, saffron accents, and practical information hierarchy. It makes Sahiti feel trustworthy without becoming bureaucratic.
Probability: 0.03

### Theme Name: Bazaar of Possibility
Very Brief Intro: A warmer, people-first direction inspired by local markets, paper textures, and regional craft. It gives the product more optimism and personality while retaining clarity for first-time users.
Probability: 0.08

### Theme Name: Quiet Signal
Very Brief Intro: A restrained product direction with lots of air, fine rules, subtle data motifs, and a small number of expressive color moments. It makes the experience feel modern, focused, and quietly intelligent.
Probability: 0.02

## Chosen direction: Civic Clarity

### Design Movement
Contemporary civic editorial design: the visual restraint of public-service information design combined with the warmth of a field guide for small-business owners.

### Core Principles
- Give important ideas room to breathe; use whitespace as reassurance, not emptiness.
- Keep trust cues visible through navy structure, saffron highlights, and practical microcopy.
- Balance useful information with small human moments so the page feels approachable.
- Prefer crisp borders, gentle depth, and purposeful asymmetry over decorative clutter.

### Color Philosophy
Navy carries stability and institutional trust. Saffron functions as a small signal of energy and forward movement rather than a dominant fill. Soft blue-grey surfaces keep the page legible and calm, while restrained green moments suggest progress and opportunity.

### Layout Paradigm
A vertical editorial flow: centered introduction copy opens into a roomy two-column welcome band, where the left side explains the service and the right side holds a visual trust card. The login card remains the clear action point below, with breathing room separating orientation from commitment.

### Signature Elements
- A fine saffron rule and small uppercase eyebrow to establish the page's civic identity.
- A compact “Sahiti signal” card with a map-grid motif and three practical promises.
- Gentle entrance motion and hover lift on feature tiles, kept short and functional.

### Interaction Philosophy
Every interaction should reduce uncertainty. Buttons feel direct, feature tiles respond with a small lift, and supporting copy answers the next question before the user has to ask it.

### Animation
Use short ease-out transitions under 240ms for buttons, selects, and feature tiles. Let the welcome band rise in softly on first load with a 40ms stagger between child groups. Respect prefers-reduced-motion and remove decorative motion when requested.

### Typography System
Use Georgia for editorial headings and Segoe UI / Nirmala UI for interface copy, preserving strong Indic-script fallback. Headings should be bold but not oversized; eyebrow labels use tracked uppercase sans text; body copy stays at a comfortable 1.6 line height.

### Brand Essence
Sahiti is a multilingual financial starting point for entrepreneurs and small businesses who want clearer decisions before taking the next step. Personality: grounded, encouraging, clear.

### Brand Voice
Headlines sound confident and human. CTAs are specific and low-friction. Microcopy explains the benefit without hype.

Example lines:
- “Plan your next move with more clarity.”
- “A clearer first step for every kind of business.”

### Wordmark & Logo
Use the existing Sahiti wordmark treatment in the navy banner, paired with a simple saffron signal mark built from three ascending bars and one connecting line. It should read as progress across regions, not as a generic finance icon.

### Signature Brand Color
Sahiti Saffron — #f29a38. Use it as the ownable signal color for rules, focus moments, and progress accents, not as a full-page background.

## Style Decisions
- Keep the new welcome content inside the existing HTML/CSS experience rather than converting the site to a different framework.
- Make the welcome section visibly more spacious, but preserve the login card as the primary conversion point.
- Use generated artwork only as a supporting visual cue; the page should remain readable and practical even if the artwork is not loaded.
