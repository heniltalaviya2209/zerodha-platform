# robot.md

Copilot context file for this repository.

## Project Snapshot

- Stack: React (Create React App), React Router, Bootstrap classes in JSX.
- Entry point: src/index.js
- Layout pattern: Navbar and Footer are rendered once around all routes from src/index.js.
- Static assets are used from public/media/images via relative paths like media/images/....

## Route Map

Defined in src/index.js:

- / -> src/landing_page/home/HomePage.js
- /signup -> src/landing_page/signup/Signup.js
- /about -> src/landing_page/about/AboutPage.js
- /product -> src/landing_page/products/ProductsPage.js
- /pricing -> src/landing_page/pricing/PricingPage.js
- /support -> src/landing_page/support/SupportPage.js
- * -> src/landing_page/NotFound.js

## Page Composition

### Shared

- src/landing_page/Navbar.js
  - Top navigation links to Signup, About, Product, Pricing, Support.
- src/landing_page/Footer.js
  - Multi-column footer with legal/disclaimer copy.
- src/landing_page/OpenAccount.js
  - Reusable call-to-action section used on Home and Pricing pages.
- src/landing_page/NotFound.js
  - 404 fallback view.

### Home

- src/landing_page/home/HomePage.js
  - Composes Hero, Awards, Stats, Pricing, Education, OpenAccount.
- src/landing_page/home/Hero.js
- src/landing_page/home/Awards.js
- src/landing_page/home/Stats.js
- src/landing_page/home/Pricing.js
- src/landing_page/home/Education.js

### About

- src/landing_page/about/AboutPage.js
  - Composes Hero and Team.
  - Function is currently named PricingPage (name mismatch, export works).
- src/landing_page/about/Hero.js
- src/landing_page/about/Team.js

### Products

- src/landing_page/products/ProductsPage.js
  - Composes Hero, alternating LeftSection/RightSection blocks, and Universe.
  - Function is currently named PricingPage (name mismatch, export works).
- src/landing_page/products/Hero.js
- src/landing_page/products/LeftSection.js
- src/landing_page/products/RightSection.js
- src/landing_page/products/Universe.js

### Pricing

- src/landing_page/pricing/PricingPage.js
  - Composes Hero, OpenAccount, Brokerage.
- src/landing_page/pricing/Hero.js
- src/landing_page/pricing/Brokerage.js

### Support

- src/landing_page/support/SupportPage.js
  - Composes Hero and CreateTicket.
  - Function is currently named PricingPage (name mismatch, export works).
- src/landing_page/support/Hero.js
- src/landing_page/support/CreateTicket.js

### Signup

- src/landing_page/signup/Signup.js
  - File exists but is currently empty. Route /signup points here.

## Styling and Conventions

- Bootstrap utility/grid classes are the main styling approach.
- Global CSS lives in src/index.css.
- Most links are plain <a href=""> placeholders; internal route navigation should prefer react-router-dom Link.
- Several JSX nodes use class instead of className for icons; normalize to className during cleanup.

## Known Gaps and Risks

- Empty component file at src/landing_page/signup/Signup.js will break imports/build.
- Component function names are inconsistent in multiple files (AboutPage/ProductsPage/SupportPage use PricingPage function name).
- Duplicate repetitive ticket blocks in support/CreateTicket.js suggest data should be mapped from arrays.
- Many image tags are missing alt attributes.

## Copilot Working Rules for This Repo

- Preserve route paths in src/index.js unless explicitly requested.
- Keep Navbar/Footer global placement unchanged unless user asks for layout refactor.
- Reuse existing section components rather than rewriting whole pages.
- When adding links between pages, use Link for internal routes and <a> for external URLs.
- Prefer small, surgical edits to maintain current structure.
- If fixing obvious JSX issues, prioritize: empty Signup.js, class -> className, missing alt text, and naming consistency.

## Suggested Next Improvements

1. Implement a valid Signup component in src/landing_page/signup/Signup.js.
2. Rename mismatched function declarations to match file purpose for readability.
3. Refactor repeated support ticket blocks into reusable data-driven rendering.
4. Replace placeholder href="" values with real routes/URLs or safe fallbacks.