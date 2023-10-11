This repository finetune base model on coherence data.

The Data is under 'data' folder with explaination about its format. 

In order to finetune models run: main.py
Important arguments: 
1. model_name: model name
2. coherence_type: "incremental" or "holistic" based on method
3. classification_label: 
    a. "score" - final paragraph coherence score
    b. "sent_binary" - per sentence coherence detection 
    c. "sent_cohesion" - per sentence cohesion detection
    d. "sent_consistency" - per sentence consistency detection
    e. "sent_relevance" - per sentence relevance detection
4. only_prediction: True for zero-shot

In order to finetune models from openai run: 
1. python main.py with --model_name="gpt" and the other wanted parameters
2. python main_gpt.py with the wanted parameters

The data should be in 'data' folder in the format: 
1. holistic or incremental final score data should be named: "<train/dev/test>_<holistic/incremental>.csv"
the csv file has 3 columns: 'title', 'text', 'label':
    a. "title" - string with the stroy title 
    b. "text" - string with the text
    c. "label" - int with the consensus score
2. sentence level data should be names: "<train/dev/test>_per_sent.csv"
the csv file has those columns: 
    a. "title" - string with the stroy title 
    b. "text" - string with the text
    c. "sents" - the text splitted into list 
    d. "coherence_per_sent" - dictionary with sentences id as key and True/False if it is incoherent 
    e. "cohesion_per_sent" - dictionary with sentences id as key and True/False if it is incohesive
    f. "consistency_per_sent" - dictionary with sentences id as key and True/False if it is inconsistent
    g. "relevance_per_sent" - dictionary with sentences id as key and True/False if it is irrelevant

for the data to change from the given json format you can run: 
python preprocess_data.py 

The output will be in 'output' folder in a "predict_results.txt" file 

