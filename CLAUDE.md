# Cloudflare Pages Site Generator Project

## Project Overview
This project creates test sites for validating a Cloudflare Pages to Workers migration script. The goal is to have diverse Astro-based static sites that can serve as comprehensive test cases for the migration tool.

## Main Task
Create and maintain multiple Cloudflare Pages sites with varying complexity levels to test the Pages-to-Workers migration script thoroughly. Each site should represent different real-world use cases and deployment scenarios.

## Repository Structure
```
Pages-Site-Generator/
├── astro-portfolio-site/    # Simple blog/portfolio site
├── astro-docs-site/         # Documentation site with navigation
├── astro-landing-site/      # Marketing landing page with interactions
└── CLAUDE.md               # Project guidelines and diary
```

## Best Practices for This Codebase

### Working with Astro Sites
1. **Always test builds locally** before pushing to GitHub
2. **Use semantic HTML** and proper accessibility attributes
3. **Optimize images** - prefer SVGs for illustrations, WebP for photos
4. **Keep sites static** - these are test cases for static site migration
5. **Document any Pages-specific features** that might affect migration

### Cloudflare Pages Configuration
1. **wrangler.toml Structure**:
   - Always include `compatibility_date`
   - Set `pages_build_output_dir` to match Astro's output (usually `dist`)
   - Use environment variables for site-specific settings
   - Document any Pages Functions if added (impacts migration complexity)

2. **Deployment Best Practices**:
   - Use `production` branch for stable deployments
   - Test with `wrangler pages dev` locally when possible
   - Keep build commands simple and standard
   - Document any custom build steps

### Testing Migration Scenarios
When creating or modifying sites, consider these migration test cases:
- **Simple static assets** (HTML, CSS, JS, images)
- **Nested routing** (multiple directory levels)
- **Build outputs** (different dist structures)
- **Configuration variations** (different wrangler.toml setups)
- **Asset types** (various file formats and sizes)

### Git Workflow
1. Make atomic commits with clear messages
2. Push to GitHub after each site is complete
3. Keep each site in its own directory
4. Document significant changes in the code diary

## Important Reminders
- **NEVER** add Pages Functions unless specifically testing that migration path
- **ALWAYS** ensure sites build successfully before committing
- **DOCUMENT** any quirks or issues discovered during development
- **TEST** the actual deployment to Cloudflare Pages via the dashboard
- **KEEP** sites simple enough to debug but complex enough to be realistic

## Code Diary Instructions
**IMPORTANT**: This diary should be:
- **READ** at the beginning of every coding session to understand context
- **UPDATED** at the end of every session with work completed
- Include decisions made and rationale
- Note any learnings or discoveries
- List next actions clearly

---

## CODE DIARY

### Session 1: January 21, 2025

#### Tasks Completed
1. **Created three distinct Astro sites** for migration testing:
   - `astro-portfolio-site`: Blog template with markdown content, images, and RSS feed
   - `astro-docs-site`: Documentation site with Tailwind CSS, sidebar navigation, and code examples
   - `astro-landing-site`: Marketing landing page with hero sections, animations, and contact forms

2. **Configured each site for Cloudflare Pages**:
   - Added wrangler.toml files with Pages-specific configuration
   - Set up proper build outputs pointing to `dist` directory
   - Included environment variables for production settings

3. **Published all sites to GitHub**:
   - Created public repositories for each site
   - Used production branch as default
   - URLs: 
     - https://github.com/fergusmeiklejohn/astro-portfolio-site
     - https://github.com/fergusmeiklejohn/astro-docs-site
     - https://github.com/fergusmeiklejohn/astro-landing-site

#### Key Decisions & Rationale

1. **Choice of Astro Framework**:
   - **Why**: Astro is popular for Cloudflare Pages deployments
   - **Benefit**: Tests real-world migration scenarios
   - **Learning**: Astro's build output is consistently in `dist/` making migration predictable

2. **Three Different Site Types**:
   - **Portfolio**: Tests basic static site migration with blog functionality
   - **Documentation**: Tests complex routing and styled components
   - **Landing Page**: Tests client-side JavaScript and form handling
   - **Rationale**: Covers spectrum from simple to complex migrations

3. **Image Handling Strategy**:
   - **Decision**: Used SVG placeholders instead of downloading real images
   - **Why**: Avoids copyright issues, keeps repos lightweight, still tests asset handling
   - **Learning**: SVGs work well for both illustrations and placeholder content

4. **Tailwind CSS Issue in Docs Site**:
   - **Problem**: Build failed with Tailwind CSS class compilation in Astro components
   - **Solution**: Removed `@apply` directives, used inline styles instead
   - **Learning**: Astro's build process can be sensitive to CSS-in-JS patterns

5. **Code Block Escaping**:
   - **Problem**: Astro tried to parse URLs and colons in code blocks as JSX
   - **Solution**: Wrapped code blocks in template literals `{``}`
   - **Learning**: Astro components need special handling for code examples

#### Learnings & Discoveries

1. **Astro Build Quirks**:
   - Template literals are needed for code blocks containing special characters
   - Tailwind's JIT compiler needs careful configuration in Astro
   - The `md:` responsive prefix can cause build issues in some contexts

2. **Cloudflare Pages Configuration**:
   - `pages_build_output_dir` is crucial for Pages deployment
   - wrangler.toml for Pages is different from Workers configuration
   - Environment variables can be set per deployment environment

3. **Repository Structure**:
   - Keeping sites in separate directories allows independent testing
   - Each site can have its own git history for tracking changes
   - This structure makes it easy to test the migration script on each site

#### Next Actions

1. **Deploy Sites to Cloudflare Pages**:
   - [ ] Deploy each site via Cloudflare dashboard
   - [ ] Document the deployment URLs
   - [ ] Verify all features work in production

2. **Create Migration Test Suite**:
   - [ ] Write test scripts that run migration on each site
   - [ ] Document expected outcomes for each migration
   - [ ] Create a comparison checklist for pre/post migration

3. **Enhance Test Coverage** (if needed):
   - [ ] Consider adding a site with Pages Functions
   - [ ] Add a site with redirect rules
   - [ ] Create a site with custom headers
   - [ ] Add a site with large static assets

4. **Documentation**:
   - [ ] Create README for each site explaining its test purpose
   - [ ] Document any Pages-specific features used
   - [ ] Add migration notes for each site type

5. **Potential Improvements**:
   - [ ] Add GitHub Actions for automated deployment
   - [ ] Create a monorepo setup for easier management
   - [ ] Add performance benchmarks pre/post migration
   - [ ] Include real images from Unsplash API for more realistic testing

#### Session Notes
- Total development time: ~2 hours
- All sites build successfully locally
- Ready for Cloudflare Pages deployment
- Good test coverage for basic to intermediate migration scenarios

---

*End of Session 1*