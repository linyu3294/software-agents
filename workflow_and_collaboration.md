# Team Collaboration Workflow

## Typical Feature Development Flow

### 1. Product Agent
- **Action**: `define_detailed_requirements`
- **Output**: `feature_specification`

### 2. Design Agent
- **Action**: `create_user_experience_design`
- **Input**: `feature_specification`
- **Output**: `design_mockups_and_prototypes`

### 3. Architect Agent
- **Action**: `design_technical_architecture`
- **Input**: [`feature_specification`, `design_requirements`]
- **Output**: `technical_architecture_plan`

### 4. Engineering Agent
- **Action**: `provide_implementation_estimate`
- **Input**: [`feature_specification`, `design_mockups`, `architecture_plan`]
- **Output**: `effort_estimate_and_implementation_plan`

### 5. Team Review
- **Participants**: [product_agent, design_agent, architect_agent, engineering_agent]
- **Decision**: `approve_or_revise_plan`

### 6. Engineering Agent
- **Action**: `implement_feature`
- **Checkpoints**: [design_review, architecture_review, code_review]

### 7. All Agents
- **Action**: `validate_implementation`
- **Validation Types**: [user_acceptance, design_compliance, architecture_compliance, code_quality]

## Inter-Agent Communication Matrix

### Product to Design
- User requirements and acceptance criteria
- Market feedback and user research

### Product to Architect
- Scalability and performance requirements
- Business constraints and priorities

### Design to Architect
- Interaction patterns and technical requirements
- Accessibility and performance considerations

### Architect to Engineering
- Technical standards and implementation patterns
- System constraints and quality requirements

### Engineering to All
- Implementation progress and blockers
- Effort estimates and technical risks

# Artifact Ownership Matrix

| Artifact | Primary Owner | Co-Owners | Consumers |
|----------|---------------|-----------|-----------|
| `README.md` | Documentation_Agent | - | All Stakeholders |
| `NOTES.md` | Documentation_Agent | Project_Manager | All Agents |
| `project_documentation/` | Documentation_Agent | - | All Stakeholders |
| `knowledge_base/` | Documentation_Agent | - | All Agents |
| `architecture_overview.md` | Documentation_Agent | - | External Stakeholders |
| `glossary.md` | Documentation_Agent | - | All Stakeholders |
| `product_requirements_document.md` | Product_Agent | - | Design_Agent, Architect_Agent, Engineering_Agent, Documentation_Agent |
| `feature_prioritization_matrix.md` | Product_Agent | - | All Agents |
| `user_personas.md` | Product_Agent | - | Design_Agent, Architect_Agent, Documentation_Agent |
| `user_stories.md` | Product_Agent | Design_Agent | Architect_Agent, Engineering_Agent, Documentation_Agent |
| `acceptance_criteria.md` | Product_Agent | Engineering_Agent | Design_Agent, Architect_Agent, Documentation_Agent |
| `feature_specifications.md` | Product_Agent | Design_Agent, Architect_Agent | Engineering_Agent, Documentation_Agent |
| `design_system_documentation.md` | Design_Agent | - | Product_Agent, Engineering_Agent, Documentation_Agent |
| `user_interface_mockups/` | Design_Agent | - | Product_Agent, Architect_Agent, Engineering_Agent, Documentation_Agent |
| `wireframes/` | Design_Agent | - | Product_Agent, Architect_Agent, Documentation_Agent |
| `interactive_prototypes/` | Design_Agent | - | Product_Agent, Engineering_Agent, Documentation_Agent |
| `usability_test_reports.md` | Design_Agent | - | Product_Agent, Architect_Agent, Documentation_Agent |
| `accessibility_audit_reports.md` | Design_Agent | - | Engineering_Agent, Documentation_Agent |
| `user_guide.md` | Design_Agent | Documentation_Agent | Product_Agent, External Users |
| `technical_architecture_document.md` | Architect_Agent | - | Product_Agent, Design_Agent, Engineering_Agent, Documentation_Agent |
| `technology_stack_specification.md` | Architect_Agent | - | Engineering_Agent, Documentation_Agent |
| `coding_standards_guide.md` | Architect_Agent | - | Engineering_Agent, Documentation_Agent |
| `security_requirements_specification.md` | Architect_Agent | - | Engineering_Agent, Documentation_Agent |
| `performance_benchmarks.md` | Architect_Agent | - | Engineering_Agent, Documentation_Agent |
| `component_implementation_guide.md` | Design_Agent | Architect_Agent, Engineering_Agent | Documentation_Agent |
| `infrastructure_as_code/` | Architect_Agent | Engineering_Agent | Documentation_Agent |
| `source_code/` | Engineering_Agent | - | All Agents (for review), Documentation_Agent |
| `test_suites/` | Engineering_Agent | - | All Agents, Documentation_Agent |
| `build_and_deployment_configs/` | Engineering_Agent | - | Architect_Agent, Documentation_Agent |
| `effort_estimates.md` | Engineering_Agent | - | Product_Agent, Architect_Agent, Documentation_Agent |
| `implementation_documentation.md` | Engineering_Agent | Documentation_Agent | All Agents |
| `performance_metrics.md` | Engineering_Agent | - | Product_Agent, Architect_Agent, Documentation_Agent |

# Artifact Lifecycle & Responsibilities

## Ownership Types Defined

### Primary Owner
- Creates the initial version
- Maintains ongoing updates
- Final approval authority for changes
- Responsible for quality and accuracy

### Co-Owner
- Collaborates during creation
- Provides input and feedback
- Can propose changes
- Shares responsibility for quality

### Consumer
- Uses artifact as input for their work
- May request clarifications or changes
- Provides feedback on usability
- No direct editing rights

## Artifact Update Workflow

### 1. Change Request
- **Initiator**: Any agent (Consumer or Co-Owner)
- **Target**: Primary Owner
- **Format**:
  ```yaml
  artifact: "artifact_name"
  change_type: "addition|modification|deletion"
  rationale: "business_justification"
  impact_assessment: "affected_agents_and_workflows"
  ```

### 2. Primary Owner Review
- **Actions**:
  - Evaluate change impact
  - Consult co-owners if needed
  - Approve or request modifications

### 3. Implementation
- **Primary Owner**: Makes the changes
- **Notification**: All affected consumers notified
- **Version Control**: Change tracked with reasoning

### 4. Validation
- **Co-Owners**: Review and approve changes
- **Consumers**: Validate changes meet their needs

## Cross-Artifact Dependencies

### `user_stories.md`
- **Depends On**: [`user_personas.md`, `product_requirements_document.md`]
- **Triggers Update**: [`feature_specifications.md`, `acceptance_criteria.md`]

### `feature_specifications.md`
- **Depends On**: [`user_stories.md`, `design_system_documentation.md`, `technical_architecture_document.md`]
- **Triggers Update**: [`effort_estimates.md`, `component_implementation_guide.md`]

### `source_code/`
- **Depends On**: [`feature_specifications.md`, `coding_standards_guide.md`, `component_implementation_guide.md`]
- **Triggers Update**: [`test_suites/`, `performance_metrics.md`]

## Conflict Resolution

### When Co-Owners Disagree

#### 1. Discussion
- **Participants**: [primary_owner, co_owners]
- **Goal**: Reach consensus through collaboration

#### 2. Escalation (if needed)
- **Arbiter**: Team Lead or Product Owner
- **Decision Criteria**: [business_impact, user_value, technical_feasibility]

#### 3. Documentation
- **Record Decision**: Decision rationale documented in artifact
- **Alternatives Noted**: Other options considered and why rejected

## Quality Assurance

### Artifact Quality Gates
- **Completeness**: All required sections filled
- **Clarity**: Clear, understandable language
- **Consistency**: Aligned with other artifacts
- **Accuracy**: Information is correct and current
- **Accessibility**: Appropriate for intended audience

### Review Cycles
- **Weekly**: Documentation_Agent reviews all artifacts for consistency
- **Sprint End**: All agents review artifacts they consume
- **Major Releases**: Full artifact audit and cleanup
- **Quarterly**: Knowledge base organization and archival

## Version Control Strategy

### Branching Model
- **Main Branch**: Current production state
- **Feature Branches**: Agent-specific updates
- **Documentation Branch**: Documentation_Agent updates

### Commit Standards
- **Format**: `[AGENT] [ARTIFACT]: Brief description`
- **Examples**:
  - `[PRODUCT] user_stories: Add checkout flow scenarios`
  - `[DESIGN] mockups: Update navigation component`
  - `[ARCHITECT] tech_spec: Add caching layer requirements`

### Change Approval Process
1. Agent creates feature branch
2. Makes changes to owned/co-owned artifacts
3. Submits pull request
4. Co-owners and affected consumers review
5. Primary owner approves and merges
6. Documentation_Agent updates related docs if needed