# COMP1001Sem12016Assignment2SpeechRecognition
Details of an assignment from an introductory Python course COMP1001 at the University of Melbourne. 

Below is a glossary of common terms which are used in the project description:

grapheme: an atomic unit in written language, i.e. a single character in the case of English

phoneme: an atomic sound unit in human speech, i.e. a sound which can't be broken down further into component sounds

n-gram: a contiguous sequence of n basic elements (i.e. a grapheme or phoneme)

bigram: a 2-gram, i.e. an n-gram made up of 2 elements

trigram: a 3-gram, i.e. an n-gram made up of 3 elements

training data: pre-aligned phoneme–grapheme pairs which the speech recognition system bases its predictions on

test data: phoneme strings (i.e. sound sequences) which the system needs to translate into grapheme strings (i.e. English words)

The basic task is to implement a speech recognition system, in the form of: (a) a grapheme—phoneme bigram model, and (b) a mixed phoneme/grapheme trigram model. Speech recognition is the task of converting a speech signal into text. For our purposes we assume the input is a single word, pre-segmented into phonemes, i.e. "sound segments", according to the CMU Pronouncing Dictionary phoneme set. We carry out speech recognition by analysing: (a) what character(s) are commonly associated with a given phoneme, and (b) what character sub-strings commonly occur in words. This analysis is carried out over a training set of aligned phoneme—grapheme pairs. For example, in the case of the phoneme—grapheme pair:

phoneme:	AH	B	AW	T

grapheme:	a	b	ou	t

the phoneme input is AH B AW T and the corresponding word about, in which a corresponds to AH, b to B, ou to AW, and t to T. Note that for readability, throughout the Project worksheet, all phoneme examples will be presented in ALL-CAPS and typewriter font, and all grapheme examples will be in lower-caps and italicised.

Your speech recognition system will operate in two phases: training and testing. In the training phase, the system works its way through the aligned phoneme—grapheme pairs in the training data and calculates probability estimates. In the test phase, these probabilities are then applied in predicting the most probable word hypothesis for each of a set of phoneme inputs.

Our speech recognition system is based on grapheme and phoneme n-grams, that is contiguous sequences of n graphemes and phonemes. Specifically, the phoneme bigram (=2-gram) model takes each phoneme in the input individually, and predicts the most probable corresponding grapheme(s) according to the grapheme(s) that are most commonly associated with that phoneme in the training data.

The set of phonemes our model operates over is taken from the CMU Pronouncing Dictionary, and consists of 39 items, as detailed in the table below. The set of graphemes is defined implicitly in the training data, in the alignment data. You may assume that this is an exhaustive listing of graphemes for the task.

We use the following resources/make the following assumptions in this project:

Training inputs: phoneme—phoneme pairs in North American English (encoded according to the CMU Pronouncing Dictionary phoneme set, stripped of stress = 39 phonemes)

Test inputs: phoneme-renderings of words in North American English (encoded according to the CMU Pronouncing Dictionary phoneme set, stripped of stress = 39 phonemes)

We will assume that all inputs correspond to single words

Outputs: English words (in lower-case ASCII, using only letters a—z and a NULL character (represented by an underscore, i.e. "_"), for a total of 27 graphemes. The NULL character ("_") occurs, e.g., in grapheme—phoneme strings such as BOX_, where the phoneme bigram K S maps onto the single grapheme X. It allows us to preserve a one-to-many phoneme-to-grapheme mapping.

Source of word transcriptions: CMU Pronouncing Dictionary v0.6

In our representation, we will assume a static training data set (i.e. we won't worry about updating our probability estimates)

We will not check to see if our word hypothesis is a valid word in English

Your code should not make any assumptions about the grapheme/phoneme inventory, and instead learn the alphabet size from the provided training data, so as to generalise to any new language/dataset
