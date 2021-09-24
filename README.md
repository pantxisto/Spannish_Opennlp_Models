# Spannish Opennlp models generation

## Instructions for training models with Opennlp
  - Training: https://opennlp.apache.org/docs/1.9.3/manual/opennlp.html#tools.cli.lemmatizer.LemmatizerTrainerME
  - Testing: https://opennlp.apache.org/docs/1.9.3/manual/opennlp.html#tools.cli.lemmatizer.LemmatizerEvaluator

## Data for Lemmatizer Training and Testing
The Universal Dependencies Treebank (https://universaldependencies.org/) and the CoNLL 2009 datasets distribute training data for many languages.
Data repositories for training and testing models:
  - ANCORA: https://github.com/UniversalDependencies/UD_Spanish-AnCora/tree/master
  - GSD: https://github.com/UniversalDependencies/UD_Spanish-GSD/tree/master
  - PUD: https://github.com/UniversalDependencies/UD_Spanish-PUD/tree/master
Command to train:
  - opennlp LemmatizerTrainerME.conllu -params PerceptronTrainerParams.txt -lang es -model es-lemmatizer.bin -data es_ancora-ud-train.conllu -encoding UTF-8 
Command to evaluate:
  - opennlp LemmatizerEvaluator -model es-lemmatizer.bin -data es_ancora-ud-test.conllu -encoding utf-8
## Data for Sentence Training and Testing
Data repositories for training and testing models:
  - CORPUS WIKIPEDIA: https://corpora.uni-leipzig.de/es?corpusId=spa_wikipedia_2021

Command to train:
  - opennlp SentenceDetectorTrainer -model es-sent.bin -lang es -data spa_wikipedia_2021_1M-sentences-train.txt -encoding UTF-8 

Command to evaluate:
  - opennlp SentenceDetectorEvaluator -model en-sent.bin -data spa-wikipedia_2021_10K-sentences-test.txt -encoding UTF-8

## Data for Tokenizer Training
Data repositories for training and testing models:
  - CORPUS WIKIPEDIA: https://corpora.uni-leipzig.de/es?corpusId=spa_wikipedia_202

Command to train:
  - opennlp TokenizerTrainer -model es-token.bin -lang es -data spa_wikipedia_2021_300K-sentences-train.txt -encoding UTF-8 -params .\PerceptronTrainerParams.txt

 
## Acknowledgements

 * Taulé, M., M.A. Martí, M. Recasens (2008) 'Ancora: Multilevel Annotated Corpora for Catalan and Spanish',
   Proceedings of 6th International Conference on Language Resources and Evaluation. Marrakesh (Morocco).

In addition, the following paper must be cited if coreference information (attributes entity, coreftype,
corefsubtype, homophoricDD or entityref) is used:

 * Recasens, Marta, M. Antònia Martí (2010) ‘AnCora-CO: Coreferentially annotated corpora for Spanish and
   Catalan’. Language Resources and Evaluation, Springer Science.

Additionally, the following paper must be cited when argumental attributes in "sn" or "grup.nom"
(attributes func, arg, tem or lexicalid) are used:

 * Peris, Aina, Mariona Taulé, Horacio Rodríguez (2010) ‘Semantic Annotation of Deverbal Nominalizations in the
   Spanish AnCora corpus’. Treebanks and Linguistic Theories (TLT-2010), Estonia.


