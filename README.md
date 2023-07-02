
# Creating a function to process Python code and run it with GPT4 generated scripts.

In the article ‘Are transformers effective for Time Series? (Are Transformers Effective for Time Series Forecasting? (arxiv.org) the authors argues the superiority of other methods over transformer. Nevertheless given the lately success of transformers in producing GPT4 I decided to try it again. 

Using the calling function functionality provided in gpt-4-0613 to test the viability to obtain precise answer to queries containing some kind of computation. Although GPT-4 do a decent job computing data it is not always reliable, the idea was to let GPT detect when it requires to compute some functions and generate a Python script for that. That script will be then executed, and the result will be injected again into GPT to get the correct answer. 

## Program flow 

This version of the program is very straight forward. First it uses the standard process for defining functions explained in: https://platform.openai.com/docs/guides/gpt/function-calling 

The result, which should be a python script is obtained and then it is written to a .py file. The function ‘execute_python’ is executed using ‘ubprocess.run’. The result of the execution is then inserted into the context of the query and is passed to GPT-4 to get the last answer. 

# Remarks 

The first thing that I found important is the need to use a great deal of prompt engineering to be able to properly instruct GPT to perform as expected. This can be seen just by inspecting the program. 

The second thing is that while this technique should tend to produce more accurate results (I’ve found gpt-4 particularly good at producing Python scripts) it is not guaranteed that it will always produce an accurate result. 

A final thought is that if, using something similar, it could be useful to compare the results provided by GPT-4 with the one produced by gpt-4-0613 and then use it as a reliability measure to alert the user of potential errors. 

# Conclusion 

I will continue to investigate this function calling possibility because I found it extremely useful. Next versions will do with multiple computation and stacked computations.  

I know that there are other frameworks providing similar capabilities, but I think that the one provided by OpenAI will tend to be more permanent and consistent. 
