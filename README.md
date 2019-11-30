# Code summarization tasks

The following page contains the papers on Source Code Summarization problem that I found interesting and related to my thesis. Every entry contains a brief description of the paper task, solution and evaluation techniques.

## Table of Contents

* [Surveys](#surveys)
* [Corpus](#corpus)
* [Code-to-Text](#code-to-text)
  * [Auto-generation of Summary Commentaries](#auto-generation-of-summary-commentaries)
  * [Auto-generation of Commit Messages](#auto-generation-of-commit-messages)
  * [Pseudo Code Generation](#pseudo-code-generation)
* [Text-to-Code](#text-to-code)
  * [Code retrieval](#code-retrieval)
* [Code Embeddings](#code-embeddings)

## Contents

### Surveys

1. Paul W. McBurney, Collin McMillan (2014) - An empirical study of the textual similarity between source code and source code summaries
Tasks: empirical study examining summaries of source code written by authors, readers, and auto-matic source code summarization tools
2. Najam Nazar, Yan Hu, and He Jiang (2016) - Summarizing Software Artifacts: A Literature Review
Tasks: a literature review in the field of summarizing software artifacts, focusing on bug reports, source code, mailing lists and developer discussions artifacts
3. Graham Neubig (2016) - Survey of Methods to Generate Natural Language from Source Code
Tasks: give an informal survey of methods to generate natural language from source code
4. Som Gupta, S.K Gupta (2017) - Summarization of Software Artifacts: a Review
Tasks: present the review of the state of the art of summarization techniques in software engineering context; give a brief overview to the software artifacts which are mostly used for summarization; describe the general process of summarization; review the papers published from 2010 to June 2017 and classify the works into extractive and abstractive summarization; review the evaluation techniques used for summarizing software artifacts; discuss the open problems and challenges in this field of research; discuss the future scopes in the area for new researchers.

### Corpus

1. https://www.ics.uci.edu/~lopes/datasets/ - UCI Source Code Data Sets
2. https://github.com/flobrosch/msr-data - Dataset of Developer-Labeled Commit Messages from Andreas Mauczka, Florian Brosch, Christian Schanes, Thomas Grechenig (2015) - Dataset of Developer-Labeled Commit Messages: 2,027,734 filtered commits from 1000 top GitHub project
3. https://notredame.app.box.com/s/wghwpw46x41nu6iulm6qi8j42finuxni - the commit messages and the diffs from 1006 Java Projects on Github from Siyuan Jiang, Ameer Armaly, Collin McMillan (2017) - Automatically generating commit messages from diffs using neural machine translation
4. http://leclair.tech/data/funcom/ - a collection of 2.1 million Java methods and their associated Javadoc comments from LeClair, A., McMillan, C. (2019) - Recommendations for Datasets for Source Code Summarization

### Code-to-Text

#### Auto-generation of summary commentaries

1. Giriprasad Sridhara, Emily Hill, Divya Muppaneni, Lori Pollock and K. Vijay-Shanker (2010) - Towards Automatically Generating Summary Comments for Java Methods
Tasks: automatically generate descriptive summary comments for Java methods
Solution: Software Word Usage Model; selecting the content, to be included in the summary comments; lexicalizing and generating the natural language text to express the content; combining and smoothing the generated text
Data: open-source Java projects: Megamek, SweetHome3D, JHotDraw, Jajuk
Evaluation: accuracy, content adequacy, conciseness
2. Brian P. Eddy, Jeffrey A. Robinson, Nicholas A. Kraft, Jeffrey C. Carver (2013) - Evaluating source code summarization techniques: Replication and expansion
Tasks: topic modeling based approach to source code summarization for the automatic generation of class and method summaries.
Solution: generate source code summaries using hPAM + Lead, Random, and Lead+VSM from a study of Haiduc et al.
Data: methods from aTunes and Art of Illusion open-source Java systems
Evaluation: intrinsic online evaluation in which human judges rated each summary based on their perceptions of its internal quality
3. Miltiadis Allamanis, Hao Peng, Charles Sutton (2016) - A Convolutional Attention Network for Extreme Summarization of Source Code
Tasks: detect local time-invariant and long-range topical attention features in a context-dependent way; and apply this architecture to the problem of extreme summarization of source code snippets into short, descriptive function name-like summaries.
Solution: Convolutional Attention Model
Data: most popular GitHub Java projects collected by taking the sum of the z-scores of the number of watchers and forks of each project, using GHTorrent
Evaluation: exact match and F1-score
4. Srinivasan Iyer, Ioannis Konstas, Alvin Cheung, Luke Zettlemoyer (2016) - Summarizing Source Code using a Neural Attention Model
Tasks: generating high level summaries of source code; code retrieval
Solution: CODE-NN model (built on Nematus) that uses Long Short Term Memory (LSTM) networks with attention
Data: C# and SQL posts from StackOverflow - only the title from the post and use the code snippet from those accepted answers that contain exactly one code snippet
Evaluation: METEOR, BLEU-4 scores and human evaluation + Mean Reciprocal Rank
5. Jaroslav Fowkes, Pankajan Chanthirasegaran, Razvan Ranca, Miltiadis Allamanis, Mirella Lapata, Charles Sutton (2017) - Autofolding for Source Code Summarization
Tasks: automatically create a code summary by folding less informative code regions
Solution: a simple vector space model (VSM) and a topic model, built on work in NLP summarization
Data: top six Java projects from GitHub, divided by size and annotated by humans
Evaluation: Accuracy, Precision, Recall, F1
6. Xing Hu, Ge Li, Xin Xia, David Lo, Zhi Jin (2018) - Deep Code Comment Generation
Tasks: automatically generate code comments for Java methods
Solution: DeepCom approach which represents the code as an Abstract Syntax Tree with Structure-based Traversal method for summarization via Seq2Seq model
Data: Java methods parsed by Eclipse’s JDT compiler into ASTs with Javadocs 
Evaluation: BLEU-4 score
Research Questions: RQ1: DeepCom vs. Baseline (CODE-NN); RQ2: BLEU-4 scores for source code and comments of different lengths
7. Alexander LeClair, Siyuan Jiang, Collin McMillan (2019) - A Neural Model for Generating Natural Language Summaries of Program Subroutines
Tasks: automatically generate code comments for Java methods
Solution: DeepCom approach which represents the code as an Abstract Syntax Tree with Structure-based Traversal method for summarization via Seq2Seq model
Data: Java methods parsed by Eclipse’s JDT compiler into ASTs with Javadocs 
Evaluation: BLEU-4 score
Research Questions: RQ1: DeepCom vs. Baseline (CODE-NN); RQ2: BLEU-4 scores for source code and comments of different lengths
Links: https://github.com/mcmillco/funcom - Funcom Source Code Summarization Tool based on the described model


#### Auto-generation of commit messages

1. Mario Linares-Vásquez, Kamal Hossen, Hoang Dang, Huzefa Kagdi, Malcom Gethers, Denys Poshyvanyk (2012) - Triaging Incoming Change Requests: Bug or Commit History, or Code Authorship?
Tasks: recommend expert developers to assist with a software change request (e.g., a bug fixes or feature), triaging incoming change requests
Solution: Latent Semantic Indexing, IR-based concept location technique
Data: open source systems, ArgoUML, JEdit, and MuCommander
Evaluation: Precision, Recall
2. Mario Linares-Vásquez, Luis Fernando Cortés-Coy, Jairo Aponte, Denys Poshyvanyk (2015) - ChangeScribe: A Tool for Automatically Generating Commit Messages
Tasks: assisting developers when committing changes and evade non-informative notes
Solution: ChangeScribe, a tool for automatically generating commit messages, which relies on line-based differencing
Links: http://www.cs.wm.edu/semeru/changescribe - Eclipse IDE plugin
3. Siyuan Jiang, Collin McMillan (2017) - Towards Automatic Generation of Short Summaries of Commits
Tasks: exploratory data analysis of human-written and auto-generated commits; automatically generate the commit message in a version control system
Solution: “verb+object” format of auto-generated commits with tf/idf feature extraction and Naive Bayes Classifier to classify diffs into the verb groups
Data: A. Mauczka, F. Brosch, C. Schanes, T. Grechenig, “Dataset of developer-labeled commit messages”
Evaluation: Accuracy, Precision, Recall
Links: https://www3.nd.edu/~sjiang1/commitact/ - scripts, data, results
4. Siyuan Jiang, Ameer Armaly, Collin McMillan (2017) - Automatically generating commit messages from diffs using neural machine translation
Tasks: automatically propose the commit message from a diff
Solution: Nematus model 
Data: 1000 Java projects (ordered by the number of stars) in GitHub, with the first sentences as the summaries of the commit messages and removed merge, roll-back commits and diffs larger than 1 Mb.
Evaluation: BLEU score
Notes: QA Filter to automatically detect the diffs for which the NMT model does not generate good commit message built on human evaluated generated diffs with extracted features of tf/idf and SVM classifier. QA filter has 44.9% precision and 43.8% recall.
Links: https://sjiang1.github.io/commitgen/ - scripts, data
5. Pablo Loyola, Edison Marrese-Taylor, Yutaka Matsuo (2017) - A Neural Architecture for Generating Natural Language Descriptions from Source Code Changes
Tasks: automatically describe changes introduced in the source code of a program using natural language
Solution: an attention-augmented encoder-decoder neural network architecture
Data: diff and metadata of full commit history files of Python, Java, JavaScript, C++ projects form GitHub top list
Evaluation: BLEU score

#### Pseudo Code Generation

1. Yusuke Oda, Hiroyuki Fudaba, Graham Neubig, Hideaki Hata, Sakriani Sakti, Tomoki Toda, Satoshi Nakamura (2015) - Learning to Generate Pseudo-code from Source Code using Statistical Machine Translation
Tasks: automatically generate a Pseudo code written in natural language to aid the comprehension of source code in unfamiliar programming language
Solution: Statistical Machine Translation with Phrase-Based Machine Translation and Tree-to-string Machine Translation frameworks
Data: Python-to-English and Python-to-Japanese corpora written by a hired programmer
Evaluation: BLEU score, human evaluation on Acceptability and Code Understanding

#### Project change tracking

1. Laura Moreno, Gabriele Bavota, Massimiliano Di Penta, Rocco Oliveto, Andrian Marcus, Gerardo Canfora (2014) - Automatic Generation of Release Notes
Tasks: automatic generation of release notes
Solution: ARENA approach which consists of Change Extractor (srcML toolkit – building of XML representation of source code), Code Change Summarizer (returns a template according to a given artifact), Issue Extractor (parses the Issues section to decide why the changes were commited), Commit-Issue Linker (two approaches: regular expression with ID match or ReLink), Information Aggregator (builds hierarchical structure of changes)
Data: open-source projects: Apache Cayenne, Apache Commons Codec, Lucene, Jackson-Core, Janino, SMOS
Evaluation: subjective human-evaluation on Completeness and Importance of generated notes compared with the original ones
Links: http://www.cs.wayne.edu/~severe/fse2014/ - artifact packages

### Text-to-Code

#### Code retrieval 

1. Fei Lv, Hongyu Zhang, Jian-guang Lou, Shaowei Wang, Dongmei Zhang, Jianjun Zhao (2015) - CodeHow: Effective Code Search Based on API Understanding and Extended Boolean Model
Tasks: provide a source code search tool to help programmers reuse previously written code by performing free-text queries over a large-scale codebase
Solution: CodeHow, a code search technique that can recognize potential APIs a user query refers to. CodeHow expands the query with the APIs and performs code retrieval by applying the Extended Boolean model, which considers the impact of both text similarity and potential APIs on code search.
Data: C# and SQL posts from StackOverflow - only the title from the post and use the code snippet from those accepted answers that contain exactly one code snippet
Evaluation: Precision@k, Mean Reciprocal Rank
2. Daniel Tarlow, Andrew D. Gordon, Yi Wei (2015) - Bimodal Modelling of Source Code and Natural Language
Tasks: retrieving source code snippets given a natural language query, and retrieving natural language descriptions given a source code query (i.e., source code captioning)
Solution: parse tree with a directed model
Data: synthetic data is concerned with simple text operations that may be performed in strings
Evaluation: Mean Reciprocal Rank
3. Srinivasan Iyer, Ioannis Konstas, Alvin Cheung, Luke Zettlemoyer (2016) - Summarizing Source Code using a Neural Attention Model
Tasks: generating high level summaries of source code; code retrieval
Solution: CODE-NN model (built on Nematus) that uses Long Short Term Memory (LSTM) networks with attention
Data: C# and SQL posts from StackOverflow - only the title from the post and use the code snippet from those accepted answers that contain exactly one code snippet
Evaluation: METEOR, BLEU-4 scores and human evaluation + Mean Reciprocal Rank
4. Xiaodong Gu, Hongyu Zhang, and Sunghun Kim (2018) - Deep Code Search
Tasks: provide a code search tools
Solution: CODEnn (Code-Description Embedding Neural Network), which jointly embeds code snippets and natural language descriptions into a high-dimensional vector space, in such a way that code snippet and its corresponding description have similar v   ectors
Data: GitHub open-source Java projects; the method declaration as the code element and the first sentence of its documentation comment as its natural language description.
Evaluation: Rank, Success-Rate@k, Precision@k, and Mean Reciprocal Rank

#### Code embeddings

1. Uri Alon, Meital Zilberstein, Omer Levy, Eran Yahav (2019) - code2vec: Learning Distributed Representations of Code
Tasks: represent a code snippet as a single fixed-length code vector in order to predict semantic properties of the code snippet; Automatic code review; Retrieval and API discovery
Solution: a neural network with attention aggregating multiple contexts into a single vector
Data: 10,072 Java GitHub repositories, originally introduced in A General Path-Based Representation for Predicting Program Properties
Evaluation: precision, recall, and F1 score over sub-tokens
Links: https://github.com/tech-srl/code2vec - the code, data and trained models; http://code2vec.org/ - online demo
