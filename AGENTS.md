# Resume Review Context

## Goals
- Must fit on 1 page
- Primary: Show career trajectory (promotions) with tenure + time in role
- Secondary: Show major impact at each role
- Willing to rewrite sections to accommodate

## Career Progression
- IBM: Advisory Software Engineer, Open Technology (Oct 2015 - Jan 2017)
- Google: 3 promotions in ~3 years
  - L4 Developer Advocate (Jan 2017 - Mar 2018) - 15 months
  - L5 Senior Developer Advocate (Apr 2018 - Sep 2019)
  - L6 Staff Developer Advocate (Oct 2019 - Jun 2020)
- GitHub: Staff PM → Director (Jun 2020 - Sep 2024)
  - Staff PM, Open Source (Jun 2020 - Aug 2022)
  - Director of PM (Sep 2022 - Sep 2024)
- Snowflake: Sr. Manager of PM (Oct 2024 - Present, ~16 months as of Feb 2026)

## Impact Details from Promo Packets

### Google L4→L5 (2018 Q1, Superb rating)
- Led 17 of 29 Node.js releases (45% of 2018 releases)
- Championed Top-Level Await to TC39 Stage 1 ("extremely controversial", building consensus was "a large accomplishment")
- Created ES Modules working group: 42 participants, 10 countries, 10 corporations, 14 OSS projects, 3 standards bodies
- Elected TSC Director → Node.js Foundation Board member
- Navigated 2017 governance crisis, engaged arbitrator, created Leadership subcommittee
- Peer signal: Sarah Novotny (L6): "exceeds my expectations of a L5 DA"; Manager: "L6+ scope and influence"

### Google L5→L6 (2019 Q3, Strongly Exceeds Expectations)
- Top-Level Await to Stage 3 after 1.5 years of consensus-building
- ES Modules implementation landed in Node.js (March 2019)
- 45% of all Node.js releases in 2018, then scaled by onboarding 4 new releasers
- Created OpenJS Foundation (merger of Node.js + JS Foundations), "pivotal to success"
- Vice-Chair of OpenJS Board, #1 governance committer
- GCP Node.js revenue grew from zero to a meaningful line in one year (keep directional)
- Peer signal: Chris DiBona (Director): "I thought he didn't have a good chance of pulling it off, but he showed me his mettle"
- Survey: 61% "Far above expectations", peer wrote "His impact is like that of a 7"

### GitHub Impact
- **Codespaces**: Made it profitable (was significantly unprofitable). DON'T share specific margin numbers (potentially confidential)

- **npm security -- full story (DRI across all initiatives, 2020-2024):**

  Context: npm was acquired by GitHub in 2020. Myles was hired to lead the integration and became PM DRI for npm's entire security posture, navigating a series of back-to-back crises and building systematic responses that became industry standards.

  **ATO Incidents (Oct-Nov 2021) -- the catalyst:**
  - Three account takeover attacks in 6 weeks, malware deployed via `postinstall` hook:
    - ua-parser-js hijacked (Oct 22, 2021): 1,200+ dependents, 7.5M+ weekly downloads, 9h to removal
    - coa hijacked (Nov 4, 2021): 166 dependents, 9M+ weekly downloads, 30m to removal
    - rc hijacked (Nov 4, 2021): 1,300+ dependents, 13M+ weekly downloads, 15m to removal
  - Key lesson: none of the compromised accounts had 2FA enabled
  - Myles led post-incident response and built the npm security roadmap

  **Login Verification (Dec 2021 - Mar 2022):**
  - Immediate interim measure: all non-2FA accounts required email OTP on every new session
  - Phased rollout: Dec 7, 2021 (publishers start) → Jan 4, 2022 (all publishers) → Mar 1, 2022 (all accounts)

  **Mandatory 2FA Enforcement (Feb 2022 - Nov 2022):**
  - Phased to avoid disrupting critical maintainers ("limbo" mechanism: existing tokens keep working for publish but no new sessions until 2FA enabled):
    - Feb 1, 2022: Top-100 package maintainers
    - May 31, 2022: Top-500 package maintainers
    - Nov 1, 2022: High-impact maintainers (packages with 1M+ weekly downloads OR 500+ dependents)
  - Results as of April 2024: Top-500: 90%, Top-100: 92%, High-Impact: 86%
  - WebAuthn (security keys) added alongside TOTP to make 2FA adoption frictionless
  - Model later adopted by GitHub.com and other registries industry-wide

  **Stolen OAuth Token Incident (April 2022) -- infrastructure breach:**
  - Attack chain: Travis CI / Heroku OAuth tokens stolen → authenticated with GitHub → npm private repos cloned → AWS access key found in a repo → npm AWS infrastructure accessed
  - Exfiltrated: skimdb backup (hashed passwords for 100k+ user accounts, from 2015 backup), S3 inventory CSV (names and version numbers of all packages on the registry), private package contents of 2 organizations
  - Confirmed via log analysis and package verification: no packages were modified, no new versions published

  **Registry Package Signing (response to OAuth incident):**
  - The incident made clear: if packages had been modified, there was no way for users to verify registry integrity
  - Built new signing infrastructure; re-signed every version of every package on the registry using ECDSA
  - Reused the same signing infrastructure to verify the historic integrity of all packages at signing time
  - Shipped `npm verify` CLI command so any user can verify their `node_modules` against registry signatures
  - This is distinct from build provenance: registry-generated signing (npm signs packages), not publisher-provided source attestation
  - NOTE: No evidence this specific model was adopted industry-wide the way 2FA and build provenance were. It was npm's own breach response, not a standard others followed.

  **Granular Access Tokens (Public Beta Q4 2022, GA Q1 2023):**
  - Replaced broad user-scoped tokens with fine-grained tokens: restrict by package, by scope, or by organization
  - Configurable expiration dates and IP range (CIDR) restrictions
  - Significantly reduces blast radius of a compromised token

  **Build Provenance / Linking packages to source and build (Public Beta Q1 2023, GA Q3 2023):**
  - First major package registry to ship build provenance
  - CI/CD providers (e.g., GitHub Actions) securely attest build and source information at publish time
  - Uses Sigstore instead of long-lived private keys that maintainers would have to manage
  - Deep npm package page UI integration: surfaces provenance info and warns on metadata mismatch
  - OpenSSF Securing Software Repositories working group published a guide directing all other registries (PyPI, RubyGems, etc.) to follow npm's model; npm CLI was the reference implementation
  - Third distinct supply chain security initiative where npm led and the industry followed

- **GitHub Releases**: Multi-quarter product development effort delivering automatically generated release notes and a refreshed UI. Part of the expanded Packages scope under the Director role.

- **Copilot Workspaces**: GitHub Next built Copilot Workspaces on top of Codespaces infrastructure. User was early adopter, one of first dogfooders, helped with productization strategy, led experiments like "Copilot Workspaces for PRs". Experiments informed today's agentic Copilot features. User did NOT personally make Codespaces the foundation (R&D team did that), but advised.
- **AI disruption**: Led team through the disruption as LLMs and coding agents emerged

### Snowflake (Oct 2024 - Present, ~18 months as of Apr 2026)

**Team scope:** Developer Platform across Driver Ecosystem, Database Change Management, Git Integration, Terraform Provider, REST APIs (SQL + Control Plane), Python API, SnowCLI, SnowSQL. Tools underpin billions in annual revenue.

**What "previously fragmented" means (for interviews):**
- No OKRs before Myles joined -- the team had no shared goal-setting or measurement framework
- 8 product areas operating independently with no unified strategy or portfolio-level coherence
- This is the honest answer to "what was fragmented and what did you do about it"

**New product launch: DCM (Database Change Management)**
- Created "Database as Code" as a native Snowflake primitive: a prescriptive SDLC with PLAN / ANALYZE / TEST / DEPLOY stages that both humans and AI agents can use safely.
- Launched to Public Preview (2026), growing quickly from a near-zero base.
- Snowflake objects under DCM control grew quickly after launch (keep directional).
- Positioned as Snowflake's agentic sandbox: the safe, object-aware surface where AI agents can propose and dry-run changes before promoting to production.


**Strategic framing:**
- Authored FY27 Dev Platform strategy (reviewed by leadership). Reframed mandate from "SQL-centric tooling" to "All Builders." Introduced "Building ON vs Building WITH Snowflake" framing.
- Driving Universal Driver: consolidating 7 independent codebases (Python, JDBC, ODBC, Go, Node, .NET, PHP) onto a single Rust core. The driver layer carries the majority of platform credits. Designing formal LTS program (3-year lifecycle) to give the embedded builder ecosystem a clear, stable upgrade path.
- CLI Nucleus strategy: making SnowCLI the single authoritative interface for the SDLC in local and CI/CD environments, reducing secure pipeline setup from 120+ minutes to under 5 minutes via Golden Path integrations.

**Still to capture:**
- Incident leadership specifics (what P0/Sev1 you owned and resolved)
- Manager/peer signal from calibrations or 1:1s
- Named customer escalation wins

## Standards Work
- TC39: Delegate (2017-Present), Co-Chair (2020), championed Top-Level Await from proposal to Stage 4
- ECMA: Vice President (2019-2020), Executive Committee member
- OpenJS Foundation: Vice Chair (2019-2020), helped found it, chaired merger negotiations, drafted governance

## Writing Guidelines
- Avoid em-dashes (AI smell)
- Avoid excessive numbers (eyes glaze over). Strategic use only.
- Keep financial numbers directional unless publicly safe (e.g., "made profitable" not specific margins)
- Show promotions with timing in titles when possible
- Consolidate roles at same company to show trajectory

## Structure Decisions
- Google: Consolidated from 4 entries to 2 (Staff + DA→Senior)
- GitHub: Consider consolidating Staff + Director to show promotion
- Standards: Consolidated from 8 entries to 2 (ECMA + OpenJS)
