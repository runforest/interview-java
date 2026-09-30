# Java / Spring Boot Practical Recruitment Task

Build a small support-ticket REST API using the existing Spring Boot project.

Work only in the [`interviews/java`](https://github.com/sourceallies/interviews/tree/main/java) project. Do not modify projects for other programming languages.

## What you need to deliver

- a REST API for creating, listing, and resolving support tickets;
- validation and clear JSON error responses;
- focused unit tests;
- an explanation of your decisions while you work.

<details>
<summary><strong>Core task</strong></summary>

Extend the existing application with a small support-ticket API.

A support ticket has the following structure:

```json
{
  "id": 1,
  "subject": "Unable to reset password",
  "resolved": false
}
```

Use the Spring Boot, Spring MVC, Spring Data JPA, and database components already available in the project.

</details>

<details>
<summary><strong>API contract</strong></summary>

| Method | Endpoint | Expected behavior |
| --- | --- | --- |
| `POST` | `/tickets` | Create a support ticket and return `201 Created` with the created ticket in the JSON response body |
| `GET` | `/tickets` | Return all existing support tickets |
| `PATCH` | `/tickets/{id}/resolve` | Mark an existing support ticket as resolved |

### Create a support ticket

```http
POST /tickets
```

Example request:

```json
{
  "subject": "Unable to reset password"
}
```

Expected status:

```http
201 Created
```

The response must include the created support ticket as JSON, with the generated `id`, the supplied `subject`, and `resolved` set to `false`. Do not return an empty response body.

Example response body:

```json
{
  "id": 1,
  "subject": "Unable to reset password",
  "resolved": false
}
```

### List all support tickets

```http
GET /tickets
```

Return all existing support tickets.

### Resolve a support ticket

```http
PATCH /tickets/{id}/resolve
```

Mark the selected support ticket as resolved.

</details>

<details>
<summary><strong>Validation and error handling</strong></summary>

The application must:

1. reject a blank or missing subject with `400 Bad Request`;
2. return `404 Not Found` when a selected support ticket does not exist;
3. return clear JSON error responses;
4. follow reasonable Spring Boot conventions;
5. avoid unnecessary abstractions.

Validation must be implemented using capabilities already available in the project.

</details>

<details>
<summary><strong>Unit-test requirements</strong></summary>

Implement unit tests only.

Do not create:

- integration tests;
- end-to-end tests;
- full Spring context tests;
- database integration tests;
- HTTP-level tests using `MockMvc` or similar tools.

Tests should focus on individual classes and business behavior using lightweight test doubles or mocks where needed.

Add unit tests covering at least:

1. successful support-ticket creation;
2. rejection of a blank subject;
3. resolving an existing support ticket;
4. attempting to resolve a support ticket that does not exist.

</details>

<details>
<summary><strong>Technical constraints</strong></summary>

Prefer:

- the Java standard library;
- Spring Boot or Spring Framework components already available in the project;
- dependencies already declared in `build.gradle`.

Do not add new dependencies unless they are strictly necessary to complete the task.

If you believe a new dependency is necessary:

1. explain why the existing project capabilities are insufficient;
2. discuss the decision with the interviewer before adding it;
3. add only the minimum required dependency.

Convenience alone is not a sufficient reason to introduce a new dependency.

</details>

<details>
<summary><strong>How to work during the interview</strong></summary>

Follow this sequence:

1. inspect the existing Java project;
2. explain your implementation plan;
3. implement the required behavior;
4. add the required unit tests;
5. run the unit tests;
6. review the final changes.

During the exercise, explain:

- how you approach the task;
- which files you create or modify;
- why you choose a particular structure;
- how you review generated or handwritten code;
- how you verify the behavior;
- which limitations or trade-offs you identify.

The goal is to understand how you work, not only to inspect the final code.

</details>

<details>
<summary><strong>Final review</strong></summary>

At the end, briefly show:

1. which endpoints were implemented;
2. which unit tests pass;
3. the command used to run the tests;
4. any incomplete requirements;
5. any important limitations.

A partially completed solution that you understand is preferable to generated code that you cannot explain.

</details>

---

## Appendices

<details>
<summary><strong>Appendix A — GitHub Copilot variant</strong></summary>

Follow this appendix only when the interviewer asks you to complete the task using GitHub Copilot.

### 1. Create a Copilot skill

Before modifying production code, create one repository-level Copilot skill.

The skill must enforce the following rule:

> Every new or modified test method created during this task must contain the word `interview` in its name.

The effect of the skill must be visible in the final unit-test code.

### 2. Create a testing agent

Before modifying production code, create one custom Copilot testing agent.

The testing agent must:

- load and follow the skill;
- inspect the implemented behavior;
- identify missing unit-test cases;
- create or improve relevant unit tests;
- run the relevant unit tests;
- verify that new and modified test methods follow the skill;
- summarize which tests it created or modified.

Before continuing, briefly explain:

- what the skill does;
- how the testing agent will use it;
- how you will verify that the skill was applied.

### 3. Implement the production code

Use Copilot to implement the core task.

While working, explain:

- what you ask Copilot to do;
- what context you provide;
- which suggestions you accept;
- which suggestions you modify or reject;
- how you review the generated code.

During production-code implementation, Copilot must not run tests.

Copilot may inspect existing tests, but test creation and test execution must be delegated to the custom testing agent.

Use the following workflow:

```text
skill
→ testing agent
→ production-code implementation
→ candidate review
→ testing agent
→ unit-test execution
→ final review
```

### 4. Implement an additional endpoint

Also implement:

```http
DELETE /tickets/{id}
```

The endpoint must:

- delete an existing support ticket;
- return `204 No Content`;
- return `404 Not Found` when the support ticket does not exist.

The appropriate unit test must be created by the testing agent.

### 5. Use the testing agent

After completing the production-code changes:

1. run the custom testing agent;
2. review the tests it creates or modifies;
3. accept, modify, or reject its suggestions;
4. allow the testing agent to run the relevant unit tests;
5. verify that the skill affected the test method names.

The testing agent must not create integration, database, Spring context, or HTTP-level tests.

You remain responsible for all generated code and test results.

### Additional final-review evidence

Also show:

1. the Copilot skill;
2. the custom testing agent;
3. where the word `interview` appears in test method names;
4. how the testing agent used the skill;
5. one Copilot suggestion you modified or rejected;
6. how you verified that Copilot did not run tests during production-code implementation.

</details>

<details>
<summary><strong>Appendix B — Project setup</strong></summary>

### Local IDE

Required software:

- Java 25;
- Git;
- your preferred Java IDE.

Gradle does not need to be installed because the project contains the Gradle Wrapper.

Clone and open the Java project:

```bash
git clone https://github.com/sourceallies/interviews.git
cd interviews/java
```

### GitHub Codespaces

Use this option to work entirely in the browser.

1. Open [the source repository](https://github.com/sourceallies/interviews).
2. Select `Code → Codespaces → Create codespace`.
3. If asked to choose a Dev Container configuration, select `Java`.
4. Wait until the Codespace finishes initializing.

The Java project should open in:

```text
/workspaces/interviews/java
```

Confirm the current directory:

```bash
pwd
```

Expected result:

```text
/workspaces/interviews/java
```

</details>
