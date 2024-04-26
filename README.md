# MPA_Bench
MPA (Multi-prompt Arithmetic) LLM Benchmark for Quants and Fine-Tunes
A benchmark that tests LLM model degradation due to quantization or fine-tuning. It runs 50 5-digit addition questions in a 2-turn prompt (~300 input and 600 output tokens). This more closely resembles complex questions/coding, etc and can result in steep accuracy reduction with quantization.

The prompt is very simple:

please solve these math problems:

13478+19245

24691+85123
... (continued for 50 problems)

I specifically do not use numbering or an '=' sign. All tests are run with a temperature of 0. This will give you output such as:

Here are the solutions to the math problems:

1. 13478 + 19245 = 32623
2. 24691 + 85123 = 109814
...

I then do a second prompt and ask it to return only the final answers with no commas. This further tests the ability of the model to keep track of all the numbers and not get confused. It also tests multi-turn conversation. The final output should be a list of 50 numbers:

32723

109814

70329
...

Then I compare the results to the correct answers and give it a % correct score.

Full example prompt is included as well as an Excel file with results of my tests.

Results from 4/26/2024:

![image](https://github.com/jd-3d/MPA_Bench/assets/51132497/b7fbd195-ee3a-4996-93ee-7b5b47670701)
