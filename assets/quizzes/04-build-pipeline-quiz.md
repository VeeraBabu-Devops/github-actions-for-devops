# 📝 GitHub Actions Build Pipeline Quiz

## Question 1

Which action downloads repository code?

- A. setup-node
- B. checkout
- C. upload-artifact
- D. deploy

**Answer:** B

---

## Question 2

Which action installs Node.js?

- A. setup-node
- B. checkout
- C. upload-artifact
- D. download-artifact

**Answer:** A

---

## Question 3

Which command installs project dependencies?

- A. npm build
- B. npm deploy
- C. npm install
- D. npm start

**Answer:** C

---

## Question 4

Which command builds the application?

- A. npm run build
- B. npm install
- C. npm deploy
- D. npm package

**Answer:** A

---

## Question 5

Which action stores build output?

- A. checkout
- B. setup-node
- C. upload-artifact
- D. download-artifact

**Answer:** C

---

## True or False

Artifacts are commonly used to share build output between jobs.

**Answer:** True

---

## Scenario

You have separate Build and Deploy jobs.

How can the Deploy job access the files generated during Build?

**Answer:**

Upload the build output using `actions/upload-artifact` in the Build job and retrieve it using `actions/download-artifact` in the Deploy job.
