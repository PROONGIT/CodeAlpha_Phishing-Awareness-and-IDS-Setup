# Spot the Phish — User Guide

Nov 26, 2026 · @Barthelemy

## Overview

Spot the Phish is a bilingual (English and French) phishing awareness course delivered as one self-contained HTML file. It needs no server, no account and no installation.

The course has seven core modules, a fixed 10-question Mindset Quiz and an optional game called PhishGame with a bank of 50 questions. A progression bar at the top shows how much of the core course you have completed.

- **Audience:** staff, students and the general public who need to recognize phishing emails, fake websites and social engineering.
- **Languages:** English by default, with a switch to French at any time.
- **Works on:** any modern browser, on a computer or a phone.

## Getting and opening the code file

The whole app is the single file `spot-the-phish.html`; you can open it on your own computer or put it online.

1. **Save the file.** Keep `spot-the-phish.html` in any folder.
2. **Open it locally.** Double-click the file, or drag it into Chrome, Edge, Firefox or Safari. It runs straight from your disk.
3. **Publish it (optional).** Upload the same file to any static web host, such as GitHub Pages, Netlify or your organization's web server. Share the resulting address with learners.
4. **Share the published page (optional).** The page published from Claude is private until its owner shares it from the Share menu.

The page loads its fonts from Google Fonts, so a connection improves the look. Without internet it still works and falls back to your system fonts. To change anything, open the file in a plain text editor such as Notepad or VS Code; no build step is needed.

## Using the app

Work through the modules in order, or jump to any of them from the menu. The top bar has two lines: the full menu of eight links on the first line, then your progression, a "How is it calculated?" link and the EN/FR switch on the second.

| Module | What you do | How it counts |
| --- | --- | --- |
| 1. Basics | Read the types of phishing (phishing, spear phishing, whaling, smishing, vishing, BEC, quishing, fake sites) | Press **Done** |
| 2. Emails | Tap the 7 suspicious parts of a fake bank email; each one explains itself | Counts when all 7 are found |
| 3. Fake sites | Learn the parts of a web address, then judge 6 addresses as real or fake | Counts when all 6 are answered |
| 4. Social engineering | Read 7 manipulation tactics, each with a sample message and a counter | Press **Done** |
| 5. Habits | Tick the 11 safe habits; each ticked habit turns green | Counts when all 11 are ticked |
| 6. Real cases | Read 6 reported incidents with their lessons | Press **Done** |
| 7. Mindset Quiz | Answer 10 scenario questions | Counts when you reach the results |
| 8. PhishGame | Optional extra rounds of questions | Not counted |

The EN/FR switch changes every text, including questions and explanations, without losing your place.

## Progression and scoring

Your progression is the number of core modules completed out of 7, so each module is worth about 14%. The bar therefore moves through 14%, 29%, 43%, 57%, 71%, 86% and 100%. PhishGame is optional and never changes it.

Modules 1, 4 and 6 are reading modules, so they have a **Done** button; press it again to undo. Modules 2, 3, 5 and 7 complete on their own once you finish their activity. A card under the title lists the seven modules and shows a tick next to each one that counts.

Scores are kept separate from progression:

- **Module 2:** a counter shows how many of the 7 signs you have found.
- **Module 3:** each address gives instant feedback; there is no total.
- **Mindset Quiz:** 1 point per correct answer, out of 10. A score of 8 to 10 is "strong instincts", 5 to 7 is "solid base, revisit the missed modules", and 0 to 4 suggests another pass through modules 2 to 5.
- **PhishGame:** 1 point per correct answer, scored per round out of 10 and in total out of 50.

In the web version, progress and scores live in the open page and reset when you reload it. Only your language choice is remembered, when the browser allows it.

## Mindset Quiz

The Mindset Quiz is a fixed set of 10 scenario questions, always in the same order, so a learner can get familiar with them. The answer options also keep a fixed order.

1. Read the scenario and pick one of four answers.
2. The right answer turns green and a wrong pick turns red, followed by a short explanation.
3. Press **Next question** until the last one, then **See results**.
4. The results show your score out of 10, a short verdict, and an explanation for every question you missed.
5. Press **Try again** to replay, or **Go to PhishGame** to go further.

Reaching the results marks module 7 as complete, whatever your score. A retry replays the same 10 questions.

## PhishGame

PhishGame is an optional challenge of up to 5 rounds, each with 10 random questions drawn from a bank of 50. You need more than 50% in a round, which means at least 6 correct answers out of 10, to unlock the next one.

| Rule | How it works |
| --- | --- |
| Start | Press **Play Game**. The 50 questions are shuffled and Round 1 gets the first 10. |
| Scoring | 1 point per correct answer. There is no timer and no penalty for a wrong answer. |
| Passing a round | 6 or more out of 10 unlocks the next round. |
| No repeats | Each round takes the next 10 questions of the same shuffled list, so no question appears twice in a session. |
| Answer order | The four options are shuffled for every question. |
| Failing a round | 5 or fewer ends the session. You see your total, the rounds played and an explanation for each missed question. |
| Finishing | Passing Round 5 shows your total out of 50 and a review of missed questions. |
| New session | Press **New session** or **Play again**. The bank is reshuffled, so the questions, their order and the answer order all change. |

A full run of 5 rounds uses all 50 questions exactly once. A round you fail still uses up its 10 questions for that session. Progress through the rounds is shown by five numbered markers that fill in as you pass them.

## How questions are set and edited

Every question is one `Q(...)` line in the script at the bottom of the HTML file, written once in English and once in French. The 10 Mindset Quiz questions are in the list that starts with `var MQ=[`, and the 50 PhishGame questions are in the list that starts with `var GQ=[`.

The 50 PhishGame questions cover eight themes:

| Theme | Questions |
| --- | --- |
| Emails | 8 |
| Web addresses and fake sites | 7 |
| SMS, calls and chat scams | 7 |
| Social engineering | 6 |
| Good practices | 8 |
| After an incident | 5 |
| Work and payments | 5 |
| QR codes, apps and documents | 4 |

Each question has the same shape:

```javascript
Q("Which part of an email address shows who really sent it?",
  "Quelle partie d'une adresse e-mail montre qui l'a réellement envoyé ?",
  ["The display name|Le nom affiché",
   "The domain after the @|Le domaine après le @",
   "The subject line|L'objet",
   "The signature|La signature"],
  1,
  "Explanation in English.",
  "Explication en français."),
```

The parts, in order: the question in English, the question in French, four options written as `English|French`, the number of the correct option, then the explanation in English and in French. Options are counted from 0, so `1` means the second option.

To add or change a question:

1. Open the file in a text editor and search for `var GQ=[` (or `var MQ=[`).
2. Copy an existing `Q(...)` block and edit its texts. Keep exactly four options, keep the `|` between the English and French text, and do not use `|` inside a text.
3. Set the correct-option number, and keep a comma after the closing bracket, as in the lines around it.
4. Save, reload the page and test the question.

Keep at least 50 questions in the PhishGame bank, because every round deals 10. With more than 50, each session draws a different 50, which adds variety. The Mindset Quiz is written for 10 questions, and its intro text and score verdicts use that number. The shuffling lives in the PhishGame functions and affects only that game; the Mindset Quiz uses the order you wrote.

## Tips, limits and the mobile app

Use the course in two steps: let everyone take the Mindset Quiz first as a baseline, then offer PhishGame to those who want more depth. For a group session, ask learners to compare their results after each round and discuss the questions they missed.

Know these limits before you deploy it:

- **No saved results.** Scores are not stored or sent anywhere, so the web version suits self-study rather than tracking a team.
- **Easy to pass by luck.** With four options, a guesser can reach 6 out of 10 now and then. Raise the pass mark in the code if you need a stricter bar.
- **Fictional examples.** Banks, senders and addresses are invented, and training addresses end in `.example`. The real-world case summaries come from general knowledge, so check them before using the course in a formal training.
- **Fonts.** The look is best with an internet connection; the course works without one.

A mobile app version exists as an Expo (React Native) project with the same content and functions, and it also saves progress and language on the phone. To build an Android APK, unzip the project, run `npm install`, then `npx expo prebuild --platform android`, open the `android` folder in Android Studio and choose Build APK(s). The project's README repeats these steps.
