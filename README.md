# JEV Model Test: Does My Resume Match This Job?

Testing **Jev**, the new System One model from TypeSafe AI, using the free Playground at [console.typesafe.ai](https://console.typesafe.ai).

## Why this test

The Playground already ships with an example question set for **recruiters**. It screens a candidate's resume on its own, for example coding depth, engineer type, and open source work.

I flipped it around. This version is for **me as a job seeker**: I give Jev my resume **and** a job description, and it tells me how well the two align before I apply.

## What does the model do?

Jev is not a chatbot. It does not write text.

- You give it a **state**: the information to look at (here, my resume and a job posting).
- You give it **questions**: each one has a fixed answer type.
- It returns one answer per question with a **probability**, usually in under a second.

The three answer types:

| Type | What it answers | Example |
|---|---|---|
| **Score** | How much, on a scale I define | How well do my past roles match this job? 0 to 4 |
| **Choice** | Which one, from a list I define | Is this a TPM, Program Manager, or Scrum Master role? |
| **Noul** | Yes or no, as a probability | Does this job require a certification I don't have? |

## Steps

1. **Sign up** at [console.typesafe.ai](https://console.typesafe.ai) and open the **Playground**.
2. **Prepare the state JSON.** Convert your resume and the job description into JSON. See the `state/` folder. Remove your name, email, and phone first.
3. **Prepare the questions JSON.** Write each question with its type and clear criteria. See the `questions/` folder.
4. **Paste** the state into the State box and the questions into the Questions box.
5. **Run.** All questions are answered in parallel, in one call.
6. **Read the results.** Trust answers with probability above 0.8 or below 0.2. Anything in between, judge yourself.
7. **Swap the job posting** and run again to compare jobs.

## Files

```
state/
  state_technical_customer_role.json resume + technical customer role at an AI company
  state_customer_success_pm.json     resume + Customer Success Program Manager role
questions/
  questions_general_fit.json         8 questions, works for any job posting
  questions_customer_success_pm.json 8 questions built from one job's requirements
results/
  screenshots and outputs from the Playground
```

Two question styles to try:

- **General fit:** one reusable set for any job. Scores overall fit, responsibilities, requirements, seniority, role type, and industry.
- **Requirement based:** each requirement in a job posting becomes its own question. More precise, but written per job.

## What I learned

- Writing clear criteria for each score level matters more than the question itself.
- Jev cannot do date math or arithmetic. Calculate years of experience yourself and put the number in the state.
- Jev gives no explanation. It tells you **what**, not **why**. Use a person or an LLM for the why.

## Try it yourself

Copy a question file, paste your own resume and any job description into the state, and run it in the Playground.

*Not affiliated with TypeSafe AI.*
