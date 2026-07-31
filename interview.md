# Java / Spring Boot Practical Recruitment Task

## Repository

Use the following repository:

https://github.com/sourceallies/interviews

All implementation work must be performed inside:

```text
java/
```

After cloning the repository, the project directory is:

```text
interviews/java
```

Do not modify projects for other programming languages.

---

# 1. Core Task

Extend the existing Spring Boot application with a small task-management REST API.

A task has the following structure:

```json
{
  "id": 1,
  "title": "Prepare release",
  "completed": false
}
```

Use the Spring Boot, Spring MVC, Spring Data JPA, and database components already available in the project.

## Required Endpoints

### Create a task

```http
POST /tasks
```

Example request:

```json
{
  "title": "Prepare release"
}
```

Expected response:

```http
201 Created
```

### List all tasks

```http
GET /tasks
```

Return all existing tasks.

### Complete a task

```http
PATCH /tasks/{id}/complete
```

Mark the selected task as completed.

---

# 2. Validation and Error Handling

The application must:

1. reject a blank or missing title with `400 Bad Request`;
2. return `404 Not Found` when a selected task does not exist;
3. return clear JSON error responses;
4. follow reasonable Spring Boot conventions;
5. avoid unnecessary abstractions.

Validation must be implemented using:

* the Java standard library;
* Spring Boot or Spring Framework components already available in the project;
* dependencies already declared in `build.gradle`.


---

# 3. Dependency Policy

Do not add new dependencies unless they are strictly necessary to complete the task.

Prefer:

* the Java standard library;
* Spring components already available in the project;
* dependencies already declared in `build.gradle`.

If you believe a new dependency is necessary:

1. explain why the existing project capabilities are insufficient;
2. discuss the decision with the interviewer before adding it;
3. add only the minimum required dependency.

Convenience alone is not a sufficient reason to introduce a new dependency.

---

# 4. Test Scope

Implement unit tests only.

Do not create:

* integration tests;
* end-to-end tests;
* full Spring context tests;
* database integration tests;
* HTTP-level tests using `MockMvc` or similar tools.

Tests should focus on individual classes and business behavior using lightweight test doubles or mocks where needed.

Add unit tests covering at least:

1. successful task creation;
2. rejection of a blank title;
3. completing an existing task;
4. attempting to complete a task that does not exist.

---

# 5. Choose Your Working Mode

Tell the interviewer which mode you are using before starting.

## Mode A: Without GitHub Copilot

Complete the core task and the required unit tests.

## Mode B: With GitHub Copilot

Complete the core task, the required unit tests, and the additional Copilot requirements described below.

---

# 6. Open the Project

Choose one environment option.

## Option A: GitHub Codespaces

Use this option to work entirely in the browser.

1. Open:

```text
https://github.com/sourceallies/interviews
```

2. Select:

```text
Code → Codespaces → Create codespace
```

3. If asked to choose a Dev Container configuration, select:

```text
Java
```

4. Wait until the Codespace finishes initializing.

The Java project should open automatically in:

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

## Option B: Local IDE

Required software:

* Java 25;
* Git;
* your preferred Java IDE.

Gradle does not need to be installed because the project contains the Gradle Wrapper.

Clone the repository:

```bash
git clone https://github.com/sourceallies/interviews.git
cd interviews/java
```

Open this directory in your IDE:

```text
interviews/java
```


---

# 7. Working Sequence

## Mode A: Without GitHub Copilot

Follow this sequence:

1. inspect the existing Java project;
2. explain your implementation plan;
3. implement the core task;
4. add the required unit tests;
5. run the unit tests;
6. review the final changes.

---

## Mode B: With GitHub Copilot

Follow this sequence exactly.

### Step 1: Create a Copilot Skill

Before modifying production code, create one repository-level Copilot skill.

The skill must enforce the following rule:

> Every new or modified test method created during this task must contain the word `interview` in its name.

The effect of the skill must be visible in the final unit-test code.

### Step 2: Create a Testing Agent

Before modifying production code, create one custom Copilot testing agent.

The testing agent must:

* load and follow the skill;
* inspect the implemented behavior;
* identify missing unit-test cases;
* create or improve relevant unit tests;
* run the relevant unit tests;
* verify that new and modified test methods follow the skill;
* summarize which tests it created or modified.

Before continuing, briefly explain:

* what the skill does;
* how the testing agent will use it;
* how you will verify that the skill was applied.

### Step 3: Implement the Production Code

Use Copilot to implement the core task.

While working, explain:

* what you ask Copilot to do;
* what context you provide;
* which suggestions you accept;
* which suggestions you modify or reject;
* how you review the generated code.

During production-code implementation, Copilot must not run tests.

Copilot may inspect existing tests, but test creation and test execution must be delegated to the custom testing agent.

The expected workflow is:

```text
skill
→ testing agent
→ production-code implementation
→ candidate review
→ testing agent
→ unit-test execution
→ final review
```

### Step 4: Additional Endpoint

Also implement:

```http
DELETE /tasks/{id}
```

The endpoint must:

* delete an existing task;
* return `204 No Content`;
* return `404 Not Found` when the task does not exist.

The appropriate unit test must be created by the testing agent.

### Step 5: Use the Testing Agent

After completing the production-code changes:

1. run the custom testing agent;
2. review the tests it creates or modifies;
3. accept, modify, or reject its suggestions;
4. allow the testing agent to run the relevant unit tests;
5. verify that the skill affected the test method names.

The testing agent must not create integration, database, Spring context, or HTTP-level tests.

You remain responsible for all generated code and test results.

---

# 9. Explain Your Work

During the exercise, explain:

* how you approach the task;
* which files you create or modify;
* why you choose a particular structure;
* how you review generated or handwritten code;
* how you verify the behavior;
* which limitations or trade-offs you identify.

The goal is to understand how you work, not only to inspect the final code.

---

# 10. Final Review

At the end, briefly show:

1. which endpoints were implemented;
2. which unit tests pass;
3. the command used to run the tests;
4. any incomplete requirements;
5. any important limitations.

When using Copilot, also show:

1. the Copilot skill;
2. the custom testing agent;
3. where the word `interview` appears in test method names;
4. how the testing agent used the skill;
5. one Copilot suggestion you modified or rejected;
6. how you verified that Copilot did not run tests during production-code implementation.

A partially completed solution that you understand is preferable to generated code that you cannot explain.
 
