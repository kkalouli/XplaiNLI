# About

This is XplaiNLI, an interactive, user-friendly, visualization interface for NLI. It uses the principles of the Hy-NLI system to compute inference with a deep learning (DL), 
a symbolic and a hybrid approach. Instead of targetting performance as Hy-NLI does, XplaiNLI focuses on explainability. Thus, additionally to the inference labels,
it offers sketches of explanations for the features that lead to the decision of each component. The interface also allows interaction with the user. The user can define their 
own heuristics as potential explanations for the decisions and also annotate the pair with the correct label. Find more details in our paper:

*Kalouli, A.-L., R. Sevastjanova, R. Crouch, V. de Paiva and M. El-Assady. 2020. XplaiNLI: Explainable Natural Language Inferencethrough Visual Analytics. In Proceedings of the COLING 2020 System Demonstrations (link coming soon).*

If you are interested in the performance of our system, check out our paper on Hy-NLI:

*Kalouli, A.-L., R. Crouch and V. de Paiva. 2020. Hy-NLI: a Hybrid system for Natural Language Inference. In Proceedings of COLING 2020 (link coming soon).*

If you use this software in writing scientific papers, or you use this software in any other medium serving scientists or students (e.g. web-sites,
CD-ROMs) please include the above citation.

# Demo
Check out XplaiNLI under http://bit.ly/XplaiNLI

# License
Copyright 2020 Aikaterini-Lida Kalouli and Rita Sevastjanova. GKR is a free-software discributed under the conditions of the Apache License 2.0, without warranty. See LICENSE file for more details. You should have received a copy of the LICENSE file with the source code. If not, please visit http://www.apache.org/licenses/ for more information. 

# Installation 
If you are only interested in the backend of the system and its performance, check out our Hy-NLI repo: ``` https://github.com/kkalouli/Hy-NLI ```


If you are interested in the demo system, read further:

The demo runs as part of the symbolic component of the system, GKR4NLI, as an HtmlServlet. Therefore, you need to clone the repository: ``` https://github.com/kkalouli/GKR4NLI ```
A pair is input on the frontend and is then forwarded to the XplaiNLIServlet (found in gnli/src/main/java).  The servlet processes the pair in 3 ways:

- it passes it to the *InferenceComputer* main class, which produces the symbolic label of GKR4NLI, along with the exact rules that led to the decision

- it passes it to the script *get_dl_inference_decision.py*, which predicts the DL label of the pair based on the fine-tuned BERT model (for details on fine-tuning, see information
in our Hy-NLI repo). The servlet also checks which of the implemented literature findings can explain the label of the DL component and outputs the explanations-features accordinly.

- it passes the pair, the labels given by GKR4NLI and the DL component, and the rules that led to the GKR4NLI decision converted to features to the script *read_hybrid_model_and_classify_sample.py*, which
predicts a hybrid label for the pair based on the pretrained Random Forest Classifier. The classifier also outputs the weight each feature had for the prediction. 

The fine-tuned BERT model and the trained hybrid classifier model are provided in this repository. The Servlet itself and the scripts for the DL and the hybrid component are
available within the GKR4NLI repository under *gnli/src/main/webapp*. To run the demo, clone and install the GKR4NLI code and modify the scripts *get_dl_inference_decision.py* and
*read_hybrid_model_and_classify_sample.py* to use the models available here. The frontend code of the demo is also available within the *gnli/src/main/webapp* folder of GKR4NLI.

# Contact 
For troubleshooting, comments, ideas and discussions, please contact aikaterini-lida.kalouli(at)uni-konstanz.de or rita.sevastjanova(at)uni-konstanz.de
