Add voice maths quiz "Say the Sum"

Single-file web app (index.html) that reads maths questions aloud,
listens for the spoken answer and says whether it was right.

Quiz
- Random questions for addition, subtraction, multiplication and
  division; each operation can be switched on or off and has its own
  number range (default: subtraction only, 1 to 15)
- Questions are read with on-device speech synthesis voices only
- A beep marks the moment to answer; countdown timer per question
  (default 20 s)
- Large correct/wrong result text, session score and streak
- Praise after N correct answers in a row (default 5, 0 = off)

Voice recognition
- Offline mode (default): Vosk speech model runs in the page, number
  words only; the model preloads on page open so the first question is
  not delayed
- Browser mode: Web Speech API, asks for on-device recognition where
  Chrome supports it
- Off mode: type answers
- Answers are cleaned of the spoken question and feedback echo; number
  parsing handles "twenty one", "minus 3" and similar
- Fresh recognition session per question when served over http(s)
- Falls back to typing (never to an online recognizer) if offline mode
  cannot start

Tracking
- Settings saved in localStorage, with "Reset to defaults"
- Every answer is recorded; wrong answers go into a review list
- "Practise mistakes" quizzes only saved mistakes; a correct answer
  clears the mistake
- Totals, recent answers and clear buttons (two-click confirm)

UI
- Themes: Auto, Notebook, Dark, Forest, Sunset, Candy, Night
- Voice recognition, seconds per question, streak length and the
  negatives option are under a collapsed "Advanced options"
- Privacy note that changes with the recognition mode

Developer notes
- Console logging for each step (filter the console by "SayTheSum")
- Comments throughout, with a file map and "how to add things"
  checklist at the top

To use offline mode without the demo host, add
vosk-model-small-en-us-0.15.tar.gz next to index.html.
Older saved settings keep their operations and ranges but take the new
defaults for recognition mode and seconds per question.