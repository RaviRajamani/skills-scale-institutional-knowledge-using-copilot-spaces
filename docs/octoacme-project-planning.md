# OctoAcme — Project Planning

## Purpose
Turn an approved initiative into an actionable plan and backlog for delivery.

## Objectives
- Break work into shippable increments
- Identify dependencies and risks
- Align timelines, releases, and responsibilities

## Activities
1. Kickoff meeting with stakeholders and delivery team
2. Create prioritized backlog with acceptance criteria
3. Estimate scope (T-shirt sizing or story points)
4. Define Definition of Done (DoD)
5. Identify dependencies and integration points
6. Create release plan and milestone map

> **Note:** This activity flows from the project initiation phase. See [`octoacme-project-initiation.md`](./octoacme-project-initiation.md) for how initiatives are approved before planning begins.

## Backlog Item Template

```markdown
- Title:
- Description:
- Acceptance criteria:
- Priority: (P0/P1/P2/P3)
- Estimate:
- Owner:
- Dependencies: (list of related backlog items/cross-team blockers)
- Blocks: (items blocked by this one)
- Related docs/links:
```

### Backlog Item Template Example
```markdown
- Title: Implement user authentication module
- Description: Add OAuth2-based authentication to support multiple identity providers
- Acceptance criteria:
  - Users can sign in via GitHub, Google, or Microsoft
  - Login flow includes MFA option
  - Session tokens expire after 24 hours
- Priority: P0
- Estimate: 13 story points (or M in T-shirt sizing)
- Owner: @jane-dev
- Dependencies: Database schema setup (BP-045), Identity provider API integration (BP-046)
- Blocks: Admin dashboard implementation (BP-082)
- Related docs/links: [OAuth2 Standards](https://tools.ietf.org/html/rfc6749), [Design Decision Record: Auth Strategy](../decisions/auth-strategy.md)
```

## Estimation Guidance

### T-Shirt Sizing Scale
Use this scale when relative sizing is preferred:

| Size | Time Estimate | Complexity | Risk | Example |
|------|---------------|-----------|------|---------|
| **XS** | < 1 day | Trivial | None | Update documentation, fix typo |
| **S** | 1–2 days | Low | Low | Add new utility function, simple UI fix |
| **M** | 3–5 days | Medium | Medium | Implement new feature with tests |
| **L** | 1–2 weeks | High | Medium-High | Major refactoring, API overhaul |
| **XL** | 3+ weeks | Very High | High | New system architecture, large integration |

### Story Points (Fibonacci Scale)
If using story points, follow the Fibonacci sequence: **1, 2, 3, 5, 8, 13, 21, 34**

- **1–3 points**: Simple, well-understood work
- **5–8 points**: Moderate complexity, some unknowns
- **13+ points**: Complex work that may need breaking down further
- **Consider splitting**: Items > 13 points should be evaluated for breakdown

**Recommendation:** Document your team's preferred estimation method in your Definition of Done (see section below).

## Definition of Done (DoD)

A Definition of Done ensures consistent quality and completeness. Here's a sample template for OctoAcme teams:

### Sample Definition of Done Checklist

- [ ] **Code Quality**
  - [ ] Code reviewed and approved by at least one peer
  - [ ] All code follows OctoAcme style guide
  - [ ] No security vulnerabilities detected (SAST scan passed)

- [ ] **Testing**
  - [ ] Unit tests written and passing (target: >80% coverage)
  - [ ] Integration tests written and passing
  - [ ] Manual QA testing completed and sign-off obtained

- [ ] **Documentation**
  - [ ] Code comments added for complex logic
  - [ ] User-facing documentation updated (if applicable)
  - [ ] API documentation updated (if applicable)

- [ ] **Compliance & Security**
  - [ ] Accessibility requirements met (WCAG 2.1 AA minimum)
  - [ ] Performance benchmarks met or improvement noted
  - [ ] No sensitive data logged or exposed

- [ ] **Deployment Readiness**
  - [ ] Deployed successfully to staging environment
  - [ ] Smoke tests passed in staging
  - [ ] Database migrations tested (if applicable)
  - [ ] Feature flags added for rollout control (if needed)

- [ ] **Monitoring & Support**
  - [ ] Observability/logging configured
  - [ ] Runbook created for on-call support (if applicable)
  - [ ] Customer support team briefed on changes (if customer-facing)

**Note:** Adjust this template based on your team's specific needs. Document exceptions and deviations in sprint retros.

## Sprint / Iteration Planning

- Time-box planning to the agreed sprint length (typically 1–2 weeks)
- Pull items that meet DoD and have clear acceptance criteria
- Ensure team capacity is respected (account for support, maintenance, and meetings)
- Review backlog prioritization with product/stakeholders before planning begins

## Risk & Dependency Management

### Risk Register Template

Capture risks in a structured format to track and mitigate them:

| ID | Description | Impact | Probability | Owner | Mitigation | Status |
|----|-------------|--------|-------------|-------|-----------|--------|
| R001 | Key team member unavailable during critical phase | High | Medium | @project-lead | Cross-train backup developer; document critical workflows | Active |
| R002 | Third-party API latency affecting performance | Medium | High | @tech-lead | Implement caching layer; set SLA expectations with vendor | Mitigated |
| R003 | Database migration may cause downtime | High | Low | @dba | Schedule during maintenance window; test rollback procedure | Active |

### Dependency Management
- Mark cross-team dependencies in the project board with a "blocked-by" label
- Escalate external blockers during weekly sync meetings
- Maintain a dependency graph or critical path diagram for complex initiatives
- Document dependency owners and resolution timelines

## Scope Creep Handling

Prevent unplanned scope expansion during active sprints:

1. **Establish Clear Sprint Boundaries**
   - Communicate sprint goals to all stakeholders at kickoff
   - Lock backlog once sprint planning is complete
   - Require sprint lead approval for mid-sprint changes

2. **Triage New Requests**
   - Route ad-hoc requests to a "Next Sprint" backlog
   - Document reason for deferral (e.g., already committed, lower priority)
   - Schedule triage meeting if request is truly urgent

3. **Track Changes**
   - Log all scope changes and their impact (effort, timeline)
   - Update release timeline and communicate to stakeholders
   - Include change decisions in sprint retrospective notes

4. **When to Adjust**
   - If change is critical and small (<4 hours), negotiate trade-off with another item
   - If change is significant, defer to next sprint or create a separate initiative
   - Document decision rationale in ticket comments

## Stakeholder Communication Cadence

Keep stakeholders aligned and informed throughout the planning process:

| Cadence | Audience | Format | Purpose |
|---------|----------|--------|---------|
| **Weekly** | Steering Committee, Tech Leads | Sync meeting | Risk escalation, dependency review, blockers |
| **Sprint Kickoff** | Entire Team + Product | In-person/video | Communicate sprint goals, backlog, timeline |
| **Mid-Sprint** | Team Lead, Product Lead | Async update | Status check, course correction if needed |
| **Sprint Review** | Team + Stakeholders | Demo + discussion | Showcase completed work, gather feedback |
| **As-Needed** | Relevant stakeholders | Ad-hoc | Escalate risks, resolve blockers, adjust scope |

**Recommendation:** Establish a shared Slack channel or email alias for planning updates to ensure transparency and reduce meeting fatigue.

## Post-Sprint Activities

After sprint completion, close the loop and prepare for the next iteration:

1. **Sprint Review**
   - Demo completed work to stakeholders
   - Gather feedback and prioritize for future sprints
   - Measure against acceptance criteria

2. **Sprint Retrospective**
   - See [`octoacme-retrospective-and-continuous-improvement.md`](./octoacme-retrospective-and-continuous-improvement.md) for full guidance
   - Discuss what went well, what didn't, and improvement actions
   - Update Definition of Done if process gaps emerged

3. **Backlog Refinement**
   - Incorporate retrospective learnings into future backlog items
   - Refine top backlog items for next sprint
   - Estimate upcoming work and identify dependencies

4. **Metrics Review**
   - Track velocity (story points or items completed)
   - Identify trends in estimation accuracy
   - Update sprint burndown or similar tracking artifacts

## Planning Checklist

- [ ] Stakeholders aligned on initiative goals and success metrics
- [ ] Project kickoff held with delivery team
- [ ] Backlog prioritized and estimated using team's agreed method
- [ ] Release timeline and milestones agreed and communicated
- [ ] Definition of Done documented and agreed by team
- [ ] Initial test plan / QA approach drafted (see QA Approach Guidance section below)
- [ ] Dependencies and risks identified and captured in Risk Register
- [ ] Team capacity planned and resource constraints noted
- [ ] Communication cadence established with stakeholders
- [ ] Scope boundaries clearly communicated to prevent creep

## QA Approach Guidance

Develop a comprehensive test strategy during planning to ensure quality throughout delivery:

### Test Coverage Expectations

Define what "done" means for testing:

- **Unit Test Coverage:** Target 80%+ of production code
- **Integration Test Coverage:** Critical user workflows and API endpoints
- **End-to-End (E2E) Testing:** High-risk or customer-facing features
- **Manual Testing:** Exploratory testing for UX, accessibility, and edge cases

### Manual vs. Automated Testing Split

| Test Type | Manual | Automated | Notes |
|-----------|--------|-----------|-------|
| Unit tests | None | 100% | Automated by developers |
| Integration tests | 10% | 90% | Manual for complex scenarios only |
| E2E tests | 20% | 80% | Manual for new user flows or major changes |
| Regression testing | 5% | 95% | Use test automation to catch regressions |
| Exploratory testing | 100% | 0% | Always manual; not scripted |
| Performance testing | 0% | 100% | Automated load and stress tests |

### Performance & Load Testing Criteria

- Define baseline performance metrics (e.g., page load < 2 seconds, API response < 500ms)
- Identify load testing thresholds (e.g., support 1,000 concurrent users)
- Schedule load tests before major releases
- Document performance requirements in acceptance criteria

### Security Testing Requirements

- **Static Analysis:** Automated SAST scan during CI/CD
- **Dependency Scanning:** Check for known vulnerabilities in libraries
- **Penetration Testing:** Conduct for customer-facing or sensitive features
- **Secrets Scanning:** Ensure no credentials or API keys hardcoded
- **Compliance Checks:** If applicable (GDPR, HIPAA, SOC 2, etc.)

### QA Handoff Checklist

- [ ] Test plan documented and approved
- [ ] Test cases created and linked to acceptance criteria
- [ ] Test data and environments provisioned
- [ ] Regression test suite identified
- [ ] Performance baselines established
- [ ] Security scanning tools configured
- [ ] QA resource allocated and on-call schedule set

---

## Related Process Documents

- **Before Planning:** See [`octoacme-project-initiation.md`](./octoacme-project-initiation.md) for initiative approval workflow
- **After Planning:** See [`octoacme-execution-and-tracking.md`](./octoacme-execution-and-tracking.md) for sprint execution
- **Post-Sprint:** See [`octoacme-retrospective-and-continuous-improvement.md`](./octoacme-retrospective-and-continuous-improvement.md) for retrospective process
- **Overview:** See [`octoacme-project-management-overview.md`](./octoacme-project-management-overview.md) for end-to-end PM framework
