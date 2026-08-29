# OWL Ontology for College of Computing (UQU)

An ontology engineering project submitted for the **Knowledge Representation and Inference** course at **Umm Al-Qura University**. This project designs, models, and queries a comprehensive semantic domain model for the College of Computing using **OWL** and **Protégé**.

---

## Author
* **Wasan Alzubaidi** - *Data Science Student, Umm Al-Qura University*

---

## Project Overview
The ontology captures the structural, organizational, and academic framework of the College of Computing. It incorporates core class hierarchies (TBox), individuals/instances (ABox), functional & transitive properties, cardinality axioms, and automated reasoning to classify entity roles dynamically.

---

## Ontology Design & Structure

### 1️ Class Hierarchy (TBox)
* **CollegeOfComputing** (Root Class)
  * **Person:** `Student`, `FacultyMember`, `AdministrativeStaff`
  * **Activity:** `ResearchProject`, `Workshop`
  * **Facility:** `ComputerLab`, `MeetingRoom`, `SmartClassroom`
  * **Course**, **Department**, **Program**

### 2️ Property Definitions
* **Object Properties:** `teachesCourse`, `enrolledIn`, `supervisesProject`, `offersProgram`, `hasFacility`, `participatesIn`
* **Data Properties:** `hasName` (string), `hasID` (string), `hasCredits` (integer), `hasCapacity` (integer), `hasDate` (date)

### 3️ Axioms & Constraints
* **Disjointness:** Defined between disjoint roles (e.g., `Student` $\cap$ `FacultyMember` = $\emptyset$).
* **Cardinality:** Enforced constraints such as `Student enrolledIn EXACTLY 1 Program`.
* **Equivalence & Reasoning:**
  * `ActiveStudent` $\equiv$ `Student and (enrolledIn SOME Program)`
  * `TeachingFaculty` $\equiv$ `FacultyMember and (teachesCourse SOME Course)`
  * `ResearchActive` $\equiv$ `FacultyMember and (supervisesProject SOME ResearchProject)`

---

## Reasoning & SPARQL Analytics
* **Automated Inference:** Utilized HermiT / Pellet reasoners to infer implicit types (`ActiveStudent`, `TeachingFaculty`, `ResearchActive`).
* **SPARQL Execution:** Evaluated complex queries including aggregation (`COUNT`, `GROUP BY`), data ordering (`ORDER BY`), and conditional filtering (`FILTER(?capacity > 25)`).

---

## Tech Stack & Tools
* **Ontology Modeling:** Protégé
* **Web Ontology Language:** OWL / RDF
* **Query Language:** SPARQL
