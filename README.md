# Prompts

Role: Legacy Application Reverse-Engineering and Knowledge Extraction Architect

You are a senior software architect, business analyst, .NET engineer, Forms Engine specialist and technical documentation expert.

Project context

We have an existing enterprise-level mortgage application built using .NET, C#, SQL Server, XML, XSLT and a Forms Engine.

We are planning to completely rebuild its frontend using React and TypeScript. The existing source code can be accessed only once, during this knowledge-extraction phase. The new application must be developed later using the generated knowledge base, without referring to the legacy source code.

Your primary objective

Analyse the existing source code and extract all relevant technical and functional knowledge required to independently rebuild the application's functionality.

Your task is to create a comprehensive, structured, accurate and traceable knowledge base.

You must NOT generate the replacement React application or modify the legacy source code during this phase.

Mandatory rules

1. Never invent business rules, workflows, validations, fields, calculations, APIs or architectural details.
2. Clearly distinguish:
   - Confirmed facts from source code
      - Inferred behaviour
         - Unverified assumptions
            - Missing or ambiguous requirements
            3. Include source file paths, class names, method names, XML nodes, XSLT templates or SQL object names wherever possible.
            4. Identify dependencies across C#, XML, XSLT, SQL and external integrations.
            5. Document both normal and exceptional application behaviour.
            6. Identify implicit business rules embedded in conditional logic, database procedures and configuration.
            7. Where runtime behaviour cannot be established from source code alone, explicitly mark it as requiring validation.
            8. Preserve the original business meaning when documenting legacy behaviour. Do not propose modernisation changes unless specifically requested.
            9. Do not expose credentials, secrets, personal information or production customer data in generated documentation.
            10. Never claim a module is fully analysed unless all relevant dependencies and evidence have been reviewed.

            Documentation standards

            - Use Markdown for functional and technical specifications.
            - Use JSON or YAML for structured inventories, field definitions, rules and mappings where appropriate.
            - Use Mermaid for architecture, sequence and workflow diagrams.
            - Assign unique IDs to business rules, fields, workflows, screens, integrations and test scenarios.
            - Maintain traceability between extracted requirements, source references and validation scenarios.
            - Use consistent terminology throughout the knowledge base.

            Working approach

            Analyse the application incrementally, by project, module, feature and dependency.

            For each task:

            1. Identify relevant source files.
            2. Analyse their relationships and behaviour.
            3. Record findings in the appropriate knowledge-base document.
            4. Identify missing information and dependencies.
            5. Record source traceability.
            6. Update the analysis coverage report.
            7. Present a concise summary of findings and unresolved questions.

            Do not silently skip inaccessible or unanalysed files.

            Final objective

            The knowledge base must be sufficiently detailed for a separate AI coding assistant and development team to rebuild the application's documented functionality using React, TypeScript and new or retained backend APIs without needing the legacy source code.

            Treat the knowledge base as an engineering specification, not a high-level summary.



Task: Perform a Complete Legacy Codebase Inventory

Analyse the accessible legacy application repository and create a comprehensive inventory of its structure and components.

Analyse

1. All solutions, projects, folders and files.
2. C# classes, interfaces, controllers, services, repositories and utilities.
3. ASP.NET MVC, Web API, background jobs and scheduled tasks.
4. XML files, XSLT templates, Forms Engine configurations and dynamic form definitions.
5. SQL scripts, stored procedures, views, functions, tables and database references available in the repository.
6. JavaScript, CSS, client-side validation and browser-specific functionality.
7. Configuration files, feature flags, environment dependencies and application settings. Do not disclose secret values.
8. External libraries, packages, frameworks and third-party dependencies.
9. Authentication, authorisation and logging mechanisms.
10. External service and internal project dependencies.

Required outputs

Save the results in:

- "01-codebase-inventory/application-inventory.md"
- "01-codebase-inventory/project-inventory.json"
- "01-codebase-inventory/dependency-inventory.md"
- "01-codebase-inventory/unanalysed-files.md"

For every identified project or module, document:

- Name and purpose
- Technology and framework
- Important source files
- Entry points
- Dependencies
- Known database and service interactions
- Associated Forms Engine components, where applicable

Generate a Mermaid dependency diagram showing relationships between major projects and modules.

Identify duplicate functionality, potentially unused components, dynamically loaded files and dependencies that cannot be resolved from static code analysis.

Important

Do not infer that a file is unused merely because it is not referenced directly. Consider reflection, configuration-based registration, dependency injection, dynamic loading and database-driven references.

Do not proceed to detailed business-rule extraction yet.

At the end, provide:

- Total files and projects inventoried, where measurable
- Modules identified
- Major dependencies
- Unresolved references
- Analysis coverage and limitations

Do not invent file counts or claim complete coverage without evidence.


2/
Task: Reverse-Engineer the Existing Application Architecture

Using the codebase inventory, analyse the architecture of the existing enterprise mortgage application.

Analyse

1. Application entry points and execution flow.
2. Frontend rendering architecture, including Forms Engine, XML and XSLT.
3. ASP.NET MVC controllers, Web API controllers and backend services.
4. Dependency injection and service registration.
5. Database access patterns, repositories, ORM usage and stored procedure execution.
6. Authentication and authorisation architecture.
7. Session management, caching, state persistence and error handling.
8. Internal and external system communication.
9. Logging, monitoring and background processing.
10. Configuration-driven and dynamically loaded functionality.

Required outputs

Save:

- "02-architecture/system-architecture.md"
- "02-architecture/component-diagram.md"
- "02-architecture/request-lifecycle.md"
- "02-architecture/dependency-diagrams.md"
- "02-architecture/technology-stack.md"

Create Mermaid diagrams for:

- High-level system architecture
- Frontend-to-backend request flow
- Forms Engine rendering lifecycle
- Backend service and database interactions
- Authentication and authorisation flow

For every major component, document its responsibility, inputs, outputs, dependencies and failure behaviour.

Trace representative user requests from the browser through the Forms Engine, backend services and database, then back to the UI.

Identify architecture decisions evident in the source code, distinguishing explicit design choices from inferred ones.

Migration-relevant findings

Identify:

- Existing frontend responsibilities
- Business logic currently coupled to the frontend
- Logic that belongs in the backend
- Existing APIs that could potentially be retained
- Dependencies that must be replaced
- Runtime behaviours that need validation

Do not redesign the application at this stage. Document the existing architecture faithfully, and clearly distinguish observations from recommendations.

3/
Task: Extract Business Rules, Validations and Calculations

Conduct a detailed analysis of the entire legacy application to identify business logic and rules that affect application behaviour.

Areas to analyse

1. Applicant eligibility and validation
2. Mortgage and loan calculations
3. Affordability and income assessment
4. Employment and financial details
5. Property-related rules
6. Conditional field visibility and mandatory requirements
7. Application submission and validation
8. Product eligibility and business constraints
9. Workflow and status-related rules
10. User-role restrictions
11. Error and exception conditions
12. Database-level constraints and triggers

Include logic from C#, XML, XSLT, JavaScript, SQL, configuration and any other relevant source files.

For each business rule, document

- Unique rule ID
- Rule name
- Business purpose, if established
- Description
- Trigger or condition
- Inputs
- Processing logic
- Expected outcome
- Validation or error messages
- Dependencies on other rules
- Relevant user roles
- Source references
- Verification status
- Unresolved questions

Represent rules using a consistent structured schema, such as JSON, where appropriate.

Calculations

For every identified calculation, document:

- Formula as implemented
- Inputs and their data types
- Rounding and precision behaviour
- Currency or unit conventions
- Default values
- Boundary conditions
- Exception behaviour
- Source references

Do not replace legacy formulas with industry-standard assumptions or independently reinterpret them.

Conditional behaviour

Explicitly capture rules such as:

- If condition A is met, display section B.
- If value C changes, recalculate value D.
- If field E is empty, prevent submission.
- If status F is reached, restrict editing.

Include chained dependencies and interactions between fields.

Required outputs

Save:

- "03-business-rules/business-rules.md"
- "03-business-rules/business-rules.json"
- "03-business-rules/calculations.md"
- "03-business-rules/validations.md"
- "03-business-rules/conditional-logic.md"
- "03-business-rules/unresolved-rules.md"

Cross-reference each rule with its source and affected module.

Mark inferred, incomplete and unverified rules explicitly. Do not claim a rule is confirmed if its execution depends on unavailable runtime information.


4/
Task: Reverse-Engineer Forms Engine, XML and XSLT

Analyse the Forms Engine implementation, all accessible XML definitions, XSLT templates, client-side scripts and associated backend functionality.

The objective is to document the existing UI and form behaviour in a framework-independent format, without generating React code.

Analyse

1. Every form, page, tab, section, subsection and field.
2. XML-based field definitions and their attributes.
3. XSLT transformations and conditional rendering.
4. Dynamic field creation and repeatable sections.
5. Dropdowns, radio buttons, checkboxes, date pickers, tables and other controls.
6. Conditional visibility, mandatory fields, read-only behaviour and disabled states.
7. Field dependencies, calculated values and dynamic defaults.
8. Client-side and server-side validation.
9. Navigation between form sections and steps.
10. Save, resume, submission and error display behaviour.
11. Dynamic lookup lists and data-driven controls.
12. Accessibility, layout and styling rules where identifiable.

For each screen

Document:

- Screen ID and name
- Business purpose
- User roles
- Route or navigation entry point, if known
- Sections and field hierarchy
- Field definitions
- Conditional visibility rules
- Validation requirements
- Navigation behaviour
- API or backend dependencies
- Error and success states
- Source references
- Unknown or unverified behaviour

For each field

Document:

- Unique field ID
- Display label
- Internal identifier
- Data type
- UI control type
- Default value
- Required or optional status
- Read-only or editable status
- Visibility conditions
- Validation constraints
- Dependencies
- Data binding and persistence mapping
- Source reference

Required outputs

Save:

- "04-ui-and-forms/screen-inventory.json"
- "04-ui-and-forms/field-dictionary.json"
- "04-ui-and-forms/form-definitions.md"
- "04-ui-and-forms/conditional-rendering.md"
- "04-ui-and-forms/validation-behaviour.md"
- "04-ui-and-forms/navigation-flows.md"

Generate Mermaid diagrams where they help explain complex interactions.

Document behaviour, not merely the visual structure. Do not assume that an XML field definition fully describes runtime behaviour; trace related XSLT, JavaScript, C# and configuration dependencies.


5/
Task: Reverse-Engineer Application Workflows and User Journeys

Analyse the legacy application to identify every significant user journey, workflow, status transition and business process.

Analyse

1. User login and landing journeys
2. New mortgage application creation
3. Applicant and property information entry
4. Saving drafts and resuming applications
5. Application submission
6. Case review and assessment
7. Approval, rejection, referral and exception handling
8. Document collection and verification
9. Application amendments
10. Cancellation, withdrawal and closure
11. Role-based tasks and administrative operations

Only document workflows that are supported by source evidence. Do not assume that every mortgage application follows the same process.

For every workflow

Document:

- Unique workflow ID
- Business purpose
- Actors and permissions
- Initial state
- Triggering event
- Ordered steps
- Conditions and decision points
- Status transitions
- Data required at each step
- Valid and invalid transitions
- Notifications and integrations
- Failure and recovery behaviour
- Completion criteria
- Source references

Required diagrams

Create Mermaid flowcharts and state diagrams showing:

- Main application lifecycle
- Decision points
- User role interactions
- Alternative and exception paths
- Status transitions

Required outputs

Save:

- "05-workflows/workflow-inventory.md"
- "05-workflows/state-transitions.json"
- "05-workflows/workflow-diagrams.md"
- "05-workflows/user-journeys.md"
- "05-workflows/exception-scenarios.md"

Clearly distinguish user navigation from actual business workflow transitions.

Identify workflows that are partially implemented, dependent on external services or require runtime validation. Do not invent missing workflow steps.

6/
Task: Reverse-Engineer the Data Model and Data Flows

Analyse all available database scripts, SQL references, C# models, DTOs, repositories, stored procedures, XML definitions and data transformation logic.

The objective is to create a complete data model specification that supports development of a new frontend and its backend contracts.

Analyse

1. Database tables, views, functions, stored procedures and triggers.
2. Entity relationships and foreign keys.
3. C# entities, models, DTOs and view models.
4. Data transfer between UI fields, backend services and databases.
5. Field mappings, type conversions and serialization.
6. Nullable fields, default values and calculated fields.
7. Data persistence, update, deletion and archival behaviour.
8. Audit fields, history tables and versioning.
9. Transaction handling and concurrency controls.
10. Sensitive data and data retention rules identifiable from source.

For each entity and field

Document:

- Entity ID and name
- Business description
- Database object and source references
- Field name and data type
- Nullability
- Constraints
- Default values
- Relationships
- UI mappings
- API mappings
- Persistence behaviour
- Sensitivity classification, if known

Data flow

Trace representative fields from user input to the UI model, backend processing, database persistence and subsequent retrieval.

Identify discrepancies between database types, C# types, XML definitions and UI controls.

Required outputs

Save:

- "06-data-model/entity-relationships.md"
- "06-data-model/database-dictionary.json"
- "06-data-model/csharp-models.md"
- "06-data-model/data-mappings.json"
- "06-data-model/data-flow-diagrams.md"
- "06-data-model/audit-and-history.md"

Create Mermaid entity relationship diagrams where supported by the extracted schema.

Do not expose actual customer data, secrets or connection credentials. Do not infer the intended meaning of unclear columns without evidence. Flag incomplete mappings and database dependencies requiring validation.

7/
Task: Reverse-Engineer APIs and System Integrations

Analyse the existing application's API controllers, service clients, HTTP calls, messaging code, configuration, database interactions and external system references.

Analyse

1. Internal REST APIs and service endpoints
2. Request and response models
3. Authentication and authorisation mechanisms
4. Request validation and response handling
5. Third-party integrations
6. Document management systems
7. Credit checking or financial data services, where present
8. Notification and messaging services
9. Background processing and scheduled tasks
10. Retry, timeout, circuit-breaker and error handling behaviour
11. Data transformations and external dependencies

For each API or integration

Document:

- Unique integration ID
- Name and purpose
- Internal or external classification
- Endpoint and HTTP method, if available
- Request schema
- Response schema
- Required headers, excluding secret values
- Authentication mechanism
- Input validation
- Error responses
- Timeout and retry behaviour
- Data mappings
- Calling components
- Dependencies
- Source references
- Known limitations

Required outputs

Save:

- "07-api-and-integrations/api-inventory.md"
- "07-api-and-integrations/api-contracts.yaml"
- "07-api-and-integrations/external-services.md"
- "07-api-and-integrations/sequence-diagrams.md"
- "07-api-and-integrations/error-handling.md"

Create Mermaid sequence diagrams for important end-to-end integration flows.

Distinguish implemented APIs from planned, disabled or configuration-dependent integrations. Do not generate replacement APIs at this stage, and do not fabricate missing endpoints or response schemas.

8/
Task: Reverse-Engineer Application Security and Access Control

Analyse authentication, authorisation, roles, permissions, session management and data protection mechanisms in the existing application.

Analyse

1. Login and authentication flows
2. User roles and access groups
3. Role-based and resource-based permissions
4. Screen, section, field and action-level access
5. Read, create, update, delete, submit and approve permissions
6. Session lifecycle and timeout behaviour
7. Authentication tokens, cookies and security configuration
8. Data protection and sensitive data handling
9. Audit logging and security-related event tracking
10. Server-side enforcement and client-side access restrictions

For every role or permission

Document:

- Unique role or permission ID
- Name
- Description, if known
- Accessible modules and screens
- Allowed operations
- Restrictions
- Related workflow actions
- Source references
- Verification status

Create a role-permission matrix and document security flows.

Required outputs

Save:

- "08-security-and-permissions/authentication.md"
- "08-security-and-permissions/role-inventory.json"
- "08-security-and-permissions/permission-matrix.md"
- "08-security-and-permissions/session-management.md"
- "08-security-and-permissions/data-protection.md"
- "08-security-and-permissions/security-findings.md"

Identify access restrictions enforced only by the frontend and flag them for review. Never treat frontend-only restrictions as sufficient security controls.

Do not include credentials, tokens, secrets, exploitable sensitive configuration values or personal information in the knowledge base. Report security findings responsibly without including unnecessary exploit instructions.

9/
Task: Generate Complete Module-Level Functional Specifications

Use the approved codebase inventory, architecture, business rules, UI specifications, workflows, data model, API contracts and security documentation to create complete functional specifications for each application module.

Do not reanalyse or invent requirements. Use only documented evidence and explicitly identified uncertainties.

For every module

Document:

1. Module overview and business purpose
2. User roles and permissions
3. Entry points and navigation
4. Screens, tabs, sections and fields
5. Conditional rendering behaviour
6. Business rules and calculations
7. Field-level and section-level validation
8. User interactions and expected responses
9. API requests and responses
10. Data persistence and retrieval
11. Workflow transitions
12. Loading, error, empty and success states
13. Security and access restrictions
14. Accessibility and responsive behaviour, where evidenced
15. Dependencies on other modules
16. Acceptance criteria
17. Known gaps and unverified behaviour

Implementation-oriented specification

For each screen, provide:

- Screen ID
- Page layout
- Component hierarchy
- Field definitions
- UI states
- User actions
- Expected outcomes
- Validation behaviour
- API dependencies
- Navigation rules
- Relevant business rule IDs
- Relevant workflow IDs
- Relevant test scenario IDs

Include a component inventory that identifies which UI elements can be reused across modules.

Required outputs

Save individual specifications under:

"09-functional-specifications/modules/"

Also generate:

- "09-functional-specifications/module-index.md"
- "09-functional-specifications/component-inventory.md"
- "09-functional-specifications/cross-module-dependencies.md"
- "09-functional-specifications/acceptance-criteria.md"

Each specification must be detailed enough for a separate React development team to implement the module without seeing the legacy source.

Clearly identify every missing requirement that could prevent implementation. Do not replace unknown behaviour with a suggested design without marking it as a proposed change requiring approval.


10/
Task: Generate Legacy Application Functional Parity Test Scenarios

Using the complete knowledge base, create comprehensive test scenarios to validate that the new application reproduces the documented functionality of the legacy application.

Test coverage

1. UI and field behaviour
2. Required fields and validation
3. Conditional visibility and dynamic forms
4. Business rules and calculations
5. Workflow transitions
6. Data persistence and retrieval
7. API requests and responses
8. User roles and permissions
9. External integrations
10. Error handling and recovery
11. Boundary conditions and edge cases
12. Cross-module dependencies
13. Accessibility and responsive behaviour, where required

For each test case

Document:

- Unique test ID
- Module and feature
- Requirement IDs
- Business rule IDs
- Preconditions
- User role
- Test data requirements
- Test steps
- Expected results
- Expected data changes
- API or integration interactions
- Negative scenarios
- Priority based on business impact
- Automation suitability
- Verification status

Include:

- Positive tests
- Negative tests
- Boundary tests
- Conditional-path tests
- Regression scenarios
- End-to-end user journeys

For calculations, include verified input and expected output examples only where reliable expected results are available. Otherwise, mark expected results as requiring business verification.

Required outputs

Save:

- "10-test-scenarios/test-scenario-inventory.json"
- "10-test-scenarios/functional-test-cases.md"
- "10-test-scenarios/calculation-test-cases.md"
- "10-test-scenarios/workflow-test-cases.md"
- "10-test-scenarios/negative-and-edge-cases.md"
- "10-test-scenarios/end-to-end-scenarios.md"
- "10-test-scenarios/requirements-coverage.md"

Ensure every documented requirement has at least one associated test scenario, or is explicitly flagged as not yet testable.

Do not claim a test has passed simply because an expected result has been documented. Test execution and outcome verification are separate activities.

11/
Task: Generate Knowledge Base Traceability and Coverage Reports

Review all available knowledge-base documents and establish end-to-end traceability from legacy source evidence to the new application's implementation requirements and test scenarios.

Traceability relationships

Establish mappings between:

- Source files and components
- Components and business rules
- Business rules and screens
- Screens and fields
- Fields and data models
- Business rules and workflows
- Modules and APIs
- Requirements and acceptance criteria
- Acceptance criteria and test cases
- Requirements and their verification status

Required outputs

Save:

- "11-traceability/source-to-rule-mapping.json"
- "11-traceability/requirement-traceability-matrix.csv"
- "11-traceability/module-coverage.md"
- "11-traceability/business-rule-coverage.md"
- "11-traceability/test-coverage.md"
- "11-traceability/missing-dependencies.md"
- "11-traceability/unresolved-questions.md"

Identify

1. Source components with no documented functionality.
2. Business rules with no source evidence.
3. Fields without documented data mappings.
4. Workflows with incomplete state transitions.
5. API dependencies with incomplete contracts.
6. Requirements without acceptance criteria.
7. Requirements without test scenarios.
8. Conflicting rules across modules.
9. Unverified runtime behaviour.
10. Missing information that would prevent independent development.

Use unique identifiers consistently and validate that all cross-references resolve to existing knowledge-base records.

Provide quantitative coverage metrics only when the underlying inventory and denominators are sufficiently complete. Clearly distinguish documented coverage from verified functional coverage.

Do not silently discard contradictory findings. List conflicts with their evidence and mark them for resolution.


12/
Task: Perform a Comprehensive Knowledge Base Audit

You are the independent quality assurance and solution architecture reviewer for the legacy application knowledge base.

Review all generated knowledge-base documents and determine whether they are sufficiently complete, consistent, accurate and traceable to support independent development of the replacement application.

Audit areas

1. Completeness of application inventory
2. Architecture and dependency consistency
3. Business rule accuracy and traceability
4. Forms Engine and UI behaviour coverage
5. Workflow and state transition completeness
6. Data model and field mapping consistency
7. API and external integration documentation
8. Security and permissions coverage
9. Module specification completeness
10. Test scenario coverage
11. Cross-document consistency
12. Unresolved requirements and runtime dependencies

Validation process

For each documented requirement:

- Verify that its supporting evidence is identified.
- Check that referenced source components exist in the inventory.
- Confirm that related business rules, screens, fields, APIs and workflows are consistent.
- Check whether acceptance criteria and test scenarios exist.
- Identify assumptions or undocumented behaviour.
- Flag contradictions and missing dependencies.

Review representative end-to-end journeys against the extracted documentation and identify any gaps that could cause incorrect implementation.

Do not treat AI-generated documentation as independent proof of correctness. Identify areas that require validation by business analysts, developers, testers or system owners.

Classify findings

Assign each finding a status:

- Verified against source
- Verified through observed application behaviour
- Inferred from source
- Unverified
- Contradictory
- Missing

Assign impact levels based on the potential effect on application behaviour, data integrity, security or delivery.

Required outputs

Save:

- "12-knowledge-validation/knowledge-base-audit.md"
- "12-knowledge-validation/coverage-report.json"
- "12-knowledge-validation/critical-gaps.md"
- "12-knowledge-validation/contradictions.md"
- "12-knowledge-validation/approval-checklist.md"
- "12-knowledge-validation/final-readiness-report.md"

Final assessment

Provide a module-by-module assessment showing:

- Document completeness
- Source traceability
- Business rule verification
- Workflow coverage
- Test coverage
- Outstanding critical questions
- Required human approvals

Conclude with a list of outstanding blockers to independent React development.

Do not declare the knowledge base ready solely because all documents exist. It must be sufficiently verified to support implementation without the original source code.


13/
Task: Generate AI Instructions for Building the Replacement React Application

You are a senior solution architect preparing the official AI development guidelines for a new enterprise mortgage application.

Use only the approved and validated knowledge base, the newly agreed architecture, and the new project's source code and API contracts.

The legacy source code is no longer available to the development environment.

Objective

Create a comprehensive "AI-INSTRUCTIONS.md" that guides AI coding assistants in implementing the new React + TypeScript application consistently and accurately.

Include

Project context

- Application purpose
- Target users
- Approved technical stack
- Architecture and module boundaries

Knowledge base usage

- Which documents are authoritative
- How to retrieve relevant module specifications
- How to reference business rule IDs and field IDs
- How to resolve cross-module dependencies
- How to handle missing and conflicting requirements

Coding standards

- TypeScript conventions
- React component design
- Feature-based folder structure
- State management conventions
- API integration patterns
- Form management and validation
- Accessibility and responsive UI standards
- Error and loading state handling
- Naming conventions

Business logic

- Preserve approved business rules
- Avoid duplicating authoritative backend validation
- Use documented calculations and verified test cases
- Do not invent or silently modify business behaviour

Development process

- Implement one feature at a time
- Read its functional specification before coding
- Identify required dependencies
- Generate code and tests
- Run linting, type checks and tests
- Review changes against acceptance criteria
- Report missing requirements and assumptions

Security

- Follow approved authentication and authorisation architecture
- Never expose sensitive data
- Do not hardcode secrets
- Follow secure API communication and data-handling practices
- Escalate security-sensitive ambiguities for human review

Quality assurance

- Maintain requirement-to-test traceability
- Generate unit, integration and end-to-end tests
- Use approved test data
- Do not claim test success without execution results
- Flag all deviations from approved specifications

Prohibited practices

- Do not invent endpoints, business rules, calculations or workflow transitions.
- Do not bypass authentication, authorisation or validation.
- Do not introduce new architectural dependencies without approval.
- Do not modify approved business rules without documented change approval.
- Do not claim parity without supporting test evidence.

Output

Create "AI-INSTRUCTIONS.md" in the root of the approved knowledge base.

Make the instructions specific to this application, based on verified documents, rather than generic React development guidance.

Ensure a new AI coding assistant can use the file alongside the approved knowledge base to implement a feature without access to the original legacy source code.

