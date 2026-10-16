# ESG Message Triage: Exploring AI for Workplace ESG Issues

## About This Project

For this project, I wanted to explore how AI could help an organisation manage ESG-related messages from employees.

In a large workplace, employees may report issues such as water leaks, recycling problems or blocked accessible entrances. These messages may come through different channels, and checking them manually can take time.

My idea was to test whether an AI model could identify the type of issue, decide how urgent it was and suggest which team should handle it.

I developed this small experiment in Google Colab using Python.

## What I Tested

I used three example messages:

1. A water leak in Building C that had been running all morning.
2. Recycling bins that were repeatedly contaminated.
3. An accessible entrance that had been blocked for two days.

I tested two language models, FLAN-T5 Base and Qwen2.5-1.5B-Instruct. I also created a simple rule-based classifier using Python so I could compare the results.

For the language models, I designed a prompt asking for eight pieces of information, including the issue category, urgency, sentiment, recommended team and whether follow-up was required.

## My Experiment and Results

I started with FLAN-T5 Base and tried two versions of the prompt. However, neither produced the JSON format I requested. The first returned only `MEDIUM`, while the shorter prompt returned `LOW`.

I then tested Qwen2.5-1.5B-Instruct. This model was able to produce valid JSON for all three messages, which was an improvement.

However, I found that it still made a classification mistake. It identified the recycling contamination issue as `ACCESSIBILITY` instead of `WASTE`.

To check the results, I compared Qwen with my rule-based classifier.

| Method | Category accuracy |
|---|---|
| Qwen2.5-1.5B-Instruct | 66.67% (2 out of 3 correct) |
| Rule-based classifier | 100% (3 out of 3 correct) |

These results only reflect the three messages I tested.

## What I Learned

One interesting thing I found was that an AI model can follow the requested output format but still give the wrong answer.

I also learned that a simple rule-based approach can work well when the messages contain familiar keywords. However, it may struggle if employees describe the same problem using different words.

Based on this experiment, I think a combination of AI classification, predefined validation rules and human review would be more suitable for a real organisation.

## Tools I Used

- Google Colab and Python
- Hugging Face Transformers
- FLAN-T5 Base
- Qwen2.5-1.5B-Instruct
- Pandas for comparing and saving results

## Notebook

**Q3_ESG_Message_Triage_.ipynb**

This notebook includes my sample messages, prompt design, model testing, JSON validation, rule-based classifier and final accuracy comparison.

## Limitations and Future Improvements

This was a small experiment using only three sample messages, so the results are not enough to conclude which method would perform better in a real workplace.

If I continued developing this project, I would test more messages, improve the prompt and include additional checks for incorrect classifications. I would also make sure that sensitive messages and high-risk issues are reviewed by a person before any final action is taken.

The Azure architecture discussed in my assessment is a proposed design and was not implemented in this notebook.
