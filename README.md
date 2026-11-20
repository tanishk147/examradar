# ExamRadar

Know what's coming in your exam.

**Live site:** [https://tanishk147.github.io/examradar/](https://tanishk147.github.io/examradar/)

ExamRadar reads years of a university's past exam papers, finds the topics that keep coming back, and builds a study plan that fits the days you have left.

This repository is the public landing page. The product itself is in early access.

## The problem

The syllabus is huge. The time before exams is not.

Past papers are the best guide students have, and seniors hand down the same advice every year. Going through ten years of scanned PDFs by hand is the last thing anyone has time for during exam week.

- **Past papers are a mess.** Blurry scans, WhatsApp forwards, and random Drive folders. Nothing is sorted by topic, and half of it is hard to read.
- **Patterns are invisible.** Some topics show up every year for 10+ marks. Others have not appeared in five years. You cannot see that without counting.
- **Planning is guesswork.** With three exams in five days, students end up spending equal time on everything instead of what actually carries marks.

## How it works

From a folder of PDFs to a plan in minutes.

1. **Upload papers.** Drop in scanned PDFs or phone photos of past papers. Add a syllabus if you have one.
2. **AI reads and tags.** Every question is extracted, split into parts, and tagged by unit, topic, marks, and question type.
3. **See the radar.** A heatmap shows which topics repeat, how many marks they carry, and what is trending up.
4. **Get your plan.** Give it the exam date. ExamRadar builds a day-by-day plan with practice questions, ranked by weight.

ExamRadar shows patterns from past papers. It helps you prioritise. It is not a leak, and it does not replace studying the full syllabus.

## Features

- **Reads messy scans.** Blurry photos, handwritten papers, and mixed Hindi–English question sets.
- **Topic heatmaps.** Marks per topic, year by year, so the questions that always come are obvious.
- **Weighted predictions.** Topics ranked by how often and how heavily they appear, with recent years weighted higher.
- **Plans that fit your time.** Two weeks or two days. The plan adapts to the exam date, timetable, and what you already know.
- **Practice mode.** Real past questions grouped by topic, plus generated questions in the same style and difficulty.
- **Shared by class.** One student uploads, the whole class benefits. Each university's paper library grows every semester.

Papers come from students: the library, seniors, or the department. Shared libraries only include papers students choose to share. Any course with past papers can use it. It works especially well when a university reuses a similar paper format each year. Early access starts with engineering and science courses, and early access is free.

## Planned AWS architecture

Exam week means thousands of students uploading at once, often the night before. The product is planned to run on AWS so extraction stays fast when traffic spikes.

| Service | Role |
| --- | --- |
| **Amazon S3** | Stores uploaded papers securely |
| **Amazon Textract** | Extracts text and layout from scans |
| **Amazon Bedrock** | Splits, tags, and classifies every question, and generates plans |
| **Lambda + DynamoDB** | Topic index, heatmaps, and per-student plans |

```
Upload → Amazon S3 → Amazon Textract → Amazon Bedrock → Lambda + DynamoDB
```

## Roadmap

**Phase 1 · Now — Core radar**

- Upload and extract past papers
- Topic tagging and heatmaps
- Exam-date study plans

**Phase 2 · Next — Practice and library**

- Shared paper library per university
- Practice mode with similar questions
- Answer outlines for top questions

**Phase 3 · Later — Beyond university exams**

- Competitive exams such as GATE
- Faculty view for question coverage
- Mobile app with offline plans

## Run locally

This repo is a static site. No build step and no dependencies.

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server
```

Then visit [http://localhost:8000](http://localhost:8000).

The waitlist form opens the visitor's mail app with a pre-filled message. There is no backend yet.

## Contact

Tanish Kumar — [tanishkumar741@gmail.com](mailto:tanishkumar741@gmail.com)
