# Examination System

A C# console app for creating and taking exams. A teacher builds an exam question by question, then a student takes it and gets their mark at the end.

## Features

- **Two exam types**
  - **Final exam:** True/False and multiple-choice (MCQ) questions. The student sees all the answers only at the end.
  - **Practical exam:** MCQ questions only. The student is told after each question whether they were right, along with the correct answer.
- **Build the exam:** for each question, enter a header, a body, its mark, the choices and the correct answer.
- **Take the exam:** answer each question by its choice number.
- **Results:** each question with the student's answer and the correct one, the total mark (for example `7 Out Of 10`) and the time taken.
- **Input validation everywhere:** the app keeps asking until it gets a valid number, a non-empty text or an existing choice.

## OOP design

| Concept | Where it's used |
|---|---|
| Abstract classes | `Exam` and `Question` define what every exam and question must do |
| Inheritance | `FinalExam` and `PracticalExam` extend `Exam`; `TrueFalseQuestion` and `MCQQuestion` extend `Question` |
| Polymorphism | `EnterQuestions()`, `ShowExam()`, `ShowResults()` and `EnterAnswers()` behave differently in each subclass |
| Interfaces | `Subject` implements `ICloneable` and `IComparable<Subject>` |
| Overriding `ToString()` | `Question`, `Answer` and `Subject` control how they are printed |

## Project structure

| File | What it does |
|---|---|
| `Program.cs` | Entry point: creates the subject and exam, then runs it |
| `Subject.cs` | A subject (ID and name) that owns one exam; asks for the exam type, duration and number of questions |
| `Exam.cs` | Abstract base class for exams |
| `FinalExam.cs` | Final exam: True/False and MCQ questions, results at the end |
| `PracticalExam.cs` | Practical exam: MCQ only, feedback after each question |
| `Question.cs` | Abstract base class for questions |
| `TrueFalseQuestion.cs` | Question with the two answers True and False |
| `MCQQuestion.cs` | Question with any number of choices |
| `Answer.cs` | One answer choice (ID and text) |

## Tech stack

- C#
- .NET 8 console app

## How to run

You need the [.NET 8 SDK](https://dotnet.microsoft.com/download).

**Visual Studio:** open `ExaminationSystem.sln` and press **F5**.

**Terminal:** from the repository folder, run:

```bash
dotnet run --project ExaminationSystem
```
