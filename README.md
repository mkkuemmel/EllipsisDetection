# EllipsisDetection
**This is my Master's thesis: Automatic Ellipsis Detection - Machine Learning vs. Rule-Based Document Classification**


Please cite
Kümmel, Miriam. 2019. Automatic Ellipsis Detection - Machine Learning vs. Rule-Based Document Classification. Master Thesis. University of Konstanz - Germany


***Only here for the corpus? Look at the end of this readme!***<br/><br/>

**Code readme**<br/>
Ellipses (sentences with missing material) are difficult for machines to process. Where information is bound to emptiness, machines struggle to perform. This is why ellipses must be detected and resolved (the missing material has to be rebuilt into the gap) in order to be smoothly processed by computers. In my thesis, I concentrated on the detection of Sluices. <br/> <br/>
What are Sluices? A Sluice is an embedded question where all but the interrogative pronoun has been elided: <br/>
(1) I ate something, but I don't know what [I ate]. <br/>
(2) Ed killed someone but he won't tell us who [Ed killed]. <br/> <br/>
But Sluices are not the only sentences with a final wh-word, especially in German: <br/>
(3) He told me he is God knows who. <br/>
(4) Ich sag' dir mal was. (engl.: I'll tell you something.) <br/> <br/>
These sentences are not ellipses, there is no material missing and so no material can be rebuilt.
In my thesis, I pulled 479 sentences with a final wh-word from a German corpus. Then I developed a rule-based algorithm that can classify these sentences into Sluices and 'normal' sentences. A classic ML document classification algorithm was run on the data, too. <br/>
On unseen data, the rule-based algorithm yielded an F1-Score of around 95%. The ML algorithm got to around 91%. <br/>
The data (corpora) are provided in their POS-tagged version already, as the TreeTagger requires a somewhat complicated setup of Python, the TreeTagger itself and Ubuntu. This way, to run the code, you only need Python 3.7 and all the librabries; your operating system does not matter. I used Anaconda Spyder 3.3.2 and never had any issues. <br/> <br/>
How to run the code: <br/>
First, run the computational annotation (Step1_computational_annotation.py). It outputs the corpus needed.
Optional: Second, run the data investigation. It shows some nice facts and figures about our data.
Third, run the Step3_rule_based_doc_class.py - it classifies the data into Sluice and Non-Sluice.
Also third (or whenever you want), run the ML algorithm (ML_doc_class.py). <br/> <br/>
You can see both algorithm's performance in the print commands.<br/><br/><br/>




**WhFinCor: Wh-finals corpus readme**<br/>

36 search queries containing 36 german wh-phrases were run on the two source corpora (https://www.dwds.de/r)<br/>
Result: 479 german sentences with a final wh-word and period.<br/>
The corpus is in csv-format and can easily be browsed and manipulated (e.g. only show sluices) in Excel.<br/>

DATA:<br/>
- Genre (column A): contains the Genre of the document the hit is taken from
- Bibl (column B): bibliographic details about the document
- ContextBefore, Hit, and ContextAfter (columns C-E): one sentence before the hit, the actual wh-final
	sentence, and one sentence after the hit

MANUAL DATA ANNOTATION: <br/>
- Sluice or Non-Sluice (column G): The sentences in the corpus were annotated as sluice (‘y’) or non-sluice (‘n’)
- What Non-Sluice (column H): Non-Sluices were divided in four groups. Indefinite pronouns, elisions, interjections, 
	and frozen expressions.
- Embedding Verb and its Position (columns I and J): If a sentence turned out to be a sluice, the embedding verb 
	was annotated into column I. In the same step, the position of the embedding verb was annotated in column J: 
	if the embed-ding verb was the last verbal element before the final wh-phrase, column J contains ‘-1’, 
	if it was the penultimate verb, it contains ‘-2’ etc.
- Merger or Sprouting (column K): the sluices in the corpus were annotated with an ‘s’ in column K if they were 
	sprouting sluices and an ‘m’ for ‘merger’ if they had an overt antecedent. ‘bef’ was added if the antecedent 
	was found in the context before the hit.
- Negation (column L): Both, sluices and non-sluices were annotated with the information if the clause the 
	wh-word is related to, is negated (‘y’) or not (‘n’). If it is negated, the negating phrase was annotated in 
	the same column (e.g. ‘y, indefpron’ or ‘y, ohne’ (Engl.: without)).
	
COMPUTATIONAL DATA ANNOTATION: <br/>
- POS-tagged Hit and Context_before (columns N and O): Every Hit and the sentence before in the corpus were tagged
	by the TreeTagger.
- wh-Phrase and POS of wh-Phrase (columns F and P): The tagged material was subsequently used to fill column F with 
	the wh-phrase used in the sentence. The POS of the wh-phrase was put into column P.
- Sentence Length (column M)
- Last Verbal Element and Comparison to Embedding Verb (column Q and R): the last verbal element before the wh-remnant 
	was extracted and assigned to column P. If no verb could be found in the hit itself, the loop went through the 
	tagged sentence before the hit (‘ContextBefore’, column C). If it still could not find a verb, one exception 
	was hard coded: if the sequence ‘keine Ahnung’ (Engl.: no idea) was in the hit, the program ascribed ‘keine Ahnung 
	haben’ to the last verbal element. If that was not the case either, ‘\<none\>’ was put into the column. Subsequently, 
	the last verbal element was compared to the manually annotated embedding verb (column I) to see if they are the 
	same (‘y’/’n’).
- Prediction (column S): A specifically built Sluice-detector can make predictions about a sentence being a sluice 
	or not. (see readme above)




