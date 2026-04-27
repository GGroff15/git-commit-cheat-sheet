# Commit Edge Cheat Sheet

## 🎯 Goal

Identify *where a commit should start and end* so that each commit expresses a single, clear intention and keeps the system in a valid state.

---

## 🧠 Core Principle

> A commit should represent **one meaningful change in behavior or concept**.

---

## ✂️ How to Identify a Commit Edge

### 1. Concept Boundary

**Rule:** If you are introducing a new concept, it deserves its own commit.

**Ask yourself:**

* “What new idea exists after this change?”
* “Can I name this change in one sentence?”

---

### 2. Responsibility Separation

**Rule:** Changes in different layers or responsibilities should usually not be mixed.

**Examples:**

* Domain ≠ Persistence
* Use case ≠ Controller

**Ask yourself:**

* “Am I mixing business logic with infrastructure?”
* “Would separating this make review easier?”

---

### 3. Revert Safety

**Rule:** A commit should be safely reversible without breaking unrelated parts.

**Ask yourself:**

* “If I revert this commit, does the system still make sense?”
* “Does reverting remove exactly one capability?”

---

### 4. Build Integrity

**Rule:** Every commit should leave the project in a working (or at least coherent) state.

**Ask yourself:**

* “Does the project still build/run?”
* “Would CI pass at this point?”

“If I introduce an interface, is there at least one working implementation in the same commit?”

---

### 5. Testability (Even if implicit)

**Rule:** You should be able to test what the commit introduces.

**Ask yourself:**

* “Can I validate this change in isolation?”
* “Does this commit introduce something testable?”

---

### 6. Cognitive Load (Reviewability)

**Rule:** A reviewer should understand the commit in a few minutes.

**Ask yourself:**

* “Can someone review this without scrolling forever?”
* “Is the intent obvious from the diff + message?”

---

### 7. Change Type Consistency

**Rule:** Don’t mix different types of changes.

**Avoid mixing:**

* Feature + refactor
* Refactor + bugfix
* Formatting + logic

**Ask yourself:**

* “Am I doing more than one type of change here?”

---

## 🔍 Smells That You Need to Split the Commit

* “This commit does a lot of things…”
* Commit message uses **“and”** multiple times
* Files from many unrelated layers changed
* Hard to explain *why* the change exists
* You need a long paragraph to justify it

---

## 🧱 Practical Commit Patterns

### Vertical (Preferred)

* `feat: add User entity`
* `feat: implement RegisterUser use case`
* `feat: expose registration endpoint`

👉 Each commit adds a **meaningful capability**

---

### Horizontal (Avoid)

* `feat: add controller, use case, repository, entity`

👉 Hard to review, unclear intent

---

## ❓ Final Checklist Before Committing

* Can I describe this commit in one clear sentence?
* Does it introduce exactly one concept or behavior?
* Is it independent enough to be reverted safely?
* Would a teammate understand it quickly?

If any answer is “no” → split the commit.

---

## 🧭 Quick Mental Model

> “If I delete this commit, what disappears?”

* If the answer is **one clear thing** → good commit
* If the answer is **“a bunch of stuff”** → split it

---

## 💬 Example of Good Commit Messages

* `feat: add Email value object with validation`
* `feat: define UserRepository contract`
* `feat: implement user registration use case`
* `feat: add HTTP endpoint for user registration`

---

Keep commits small, intentional, and meaningful.
Your future self (and your teammates) will thank you.
