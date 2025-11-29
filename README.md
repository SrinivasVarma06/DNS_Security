# DNS_Security Implementation Details

## Loading Ollama Models

I have provided the ollama github repository link in the Links folder from where you can load them locally into your system using ollama pull model_name command and ollama list to check if they are present or not.

## Dataset Preparation

1. You have the raw datasets in the Datasets folder which were converted from pcap files(links provided in the Links Folder) through wireshark by filtering only for dns traffic and converted into txt.
2. Now, next step is to convert these raw txt files into summaries in natural language so that the LLMs can understand it. There are 2 python files in the Converting_Raw_Data_into_Summary folder where one is specifically for converting the tunneling.txt into its summary while the other transform_pcap.py is for the other 3 raw datasets(amplification,spoofing,benign).

## Zero And Few Shot Prompting

Once you have the summary txt files, you can then run the zero and few shot python codes inside the folder Zero_and_Few_Shot_Prompting folder by changing the path name inside the code to the respective file and then observe its output in the terminal. Check for the Output it gives before its explanation instead of the parsed one which it gives at the end of the explanation(doesn't match since it was parsed through regex).

## Fine-Tuning by Packet-by-Packet and Flow-wise

1. There are specific python files for converting the summary datasets again into json files since we are using mini-instruct models. preparing_dataset.py and without explanation are 2 types of datasets I have used for fine-tuning the model. The ipynb file contains the code for fine-tuning Phi-4-mini-instruct model. Run each cell and get the inferences.

2. Similarly, repeat the same things for Flow-Wise inference in the Fine-Tuning-Flow-Level Folder which contains specific ipynb and dataset conversion files.
