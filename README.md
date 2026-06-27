# AH-GS Model

This repository contains R implementations of the AH-GS matching model. The model combines student preferences, institutional preferences over majors, final student rankings, and institutional quotas.

## Overview

We consider a matching problem with students and institutions. Each student has a final performance rank, a major, and a strict preference ordering over institutions. Each institution has a fixed quota and a preference ordering over majors. The objective is to assign all students to institutions while respecting quotas and combining three elements:

1. students' preferences over institutions;
2. institutions' preferences over academic majors;
3. students' final performance rankings.

## Algorithm 1: AH-GS Model

The first algorithm extends the student-proposing Gale-Shapley logic by adding institutional preferences over majors and final student rankings.

Students apply to institutions according to their preference lists. If an institution exceeds its quota, it removes the student belonging to the least preferred major among those currently assigned. If several students belong to that major, the institution removes the lowest-ranked student among them. The rejected student then applies to the next institution in their preference list.

## Algorithm 2: AH-GS Model with Policy Variable

The second algorithm introduces a policy variable v, which defines the size of ranking classes. Students are grouped according to their final ranking. Students in higher-ranked classes have priority over students in lower-ranked classes.

Within each class, the algorithm follows the same AH-GS logic as Algorithm 1. However, students from a lower-ranked class cannot remove students from a higher-ranked class. This allows the planner to control the trade-off between performance incentives and institutional matching quality.

## Example

The repository includes an example with six students, four institutions, and three majors: Economics, Law, and Engineering.

Students have final rankings, majors, and institution preferences. Institutions have quotas and preferences over majors. The policy variable is set to `v = 2`, meaning that students are grouped into ranking classes of two students each.

## Files

* AH-GS Model Algo 1: R code for the first AH-GS algorithm.
* AH-GS-Model Algo 2: R code for the AH-GS algorithm with the policy variable v.

## How to Run

Open the R file in RStudio or any R environment and run the full script.

The code prints:

* the ranking classes;
* the final assignment by institution;
* the assignment vector for each student;
* the step-by-step history of proposals, acceptances, and rejections.

## Requirements

The code uses base R only. No additional R packages are required.

## Author

Gasindikira Josue Issa
