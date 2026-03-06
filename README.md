# Math Question Classifier
An automated classification engine that maps primary school math questions to the official Singapore Ministry of Education (MOE) mathematics syllabus. This project utilizes the Gemini 3 Flash model to perform granular classification across five levels of the syllabus hierarchy.

# Usage
Running the Engine

1.Open Classifier.ipynb in a Jupyter Notebook environment.

2.Ensure Syllabus.csv is located in the root directory of the project.

3.Update the API Key: Replace the existing Google API key in the configuration cell with your own to avoid rate limits.

4.Initialize: Execute the cells sequentially to load the data and initialize the classification engine.

5.Launch the Menu: Run the final cell to start the Interactive Menu, where you can choose:

-Option 1: Run batch accuracy tests (all 67 questions).

-Option 2: Input a custom math question for real-time classification.

-Option 3: Exit the program.

# Classification Strategy
1.Flattened Syllabus Injection
-Rather than providing raw, unstructured data, the syllabus is "flattened" into a searchable, text-based knowledge.
-LLMs process linear text more efficiently and accurately than complex nested structures, leading to more reliable classification.

2.Constraint-Based Prompting
-The engine is strictly instructed to copy syllabus fields exactly as they appear in the knowledge.
-The prompt includes specific data-cleaning and filtering rules to ensure the output is valid JSON that can be seamlessly parsed by the Python automation script.

3.Few-Shot Examples
-I added a few examples to the prompt. This helps the model learn the pattern and handle the classification correctly.

4.Granularity-First Selection
-If a question fits more than one category, the engine is programmed to choose the most specific outcome available in the syllabus hierarchy.

# Performance Summary
The engine currently demonstrates high accuracy at the structural levels of the syllabus, with opportunities for refinement at the granular learning outcome level:

Accuracy [STRAND         ]:  97.01%
Accuracy [SUBSTRAND      ]:  97.01%
Accuracy [TOPIC          ]:  74.63%
Accuracy [LEARNINGOUTCOME]:  56.72%
Accuracy [LOID           ]:  55.22%

Learning Outcome and loId accuracy is lower because many syllabus points are very similar. The best way to improve this is to split the classification into two steps. This reduces complexity and helps the model focus on a smaller number of choices at each stage.