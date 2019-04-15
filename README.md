# EllipsisDetection
This is my Master's thesis: Automatic Ellipsis Detection - Machine Learning vs. Rule-Based Approach

Ellipses (sentences with missing material) are difficult for machines to process. Where information is bound to emptiness, machines struggle to perform. This is why ellipses must be detected and resolved (the missing material has to be rebuilt into the gap) in order to be smoothly processed by computers. In my thesis, I concentrated on the detection of Sluices.
What are Sluices? A Sluice is an embedded question where all but the interrogative pronoun has been elided:
(1) I ate something, but I don't know what [I ate].
(2) Ed killed someone but he won't tell us who [Ed killed].
But Sluices are not the only sentences with a final wh-word, especially in German:
(3) He told me he is God knows who.
(4) Ich sag' dir mal was. (engl.: I'll tell you something.)
These sentences are not ellipses, there is no material missing and so no material can be rebuilt.
In my thesis, I pulled 479 sentences with a final wh-word from a German corpus. Then I developed a rule-based algorithm that can classify these sentences into Sluices and 'normal' sentences. A classic ML document classification algorithm was run on the data, too.
On unseen data, the rule-based algorithm yielded an F1-Score of around 95%. The ML algorithm got to around 91%.
The data (corpora) are provided in their POS-tagged version already, as the TreeTagger requires a somewhat complicated setup of Python, the TreeTagger itself and Ubuntu. This way, to run the code, you only need Python 3.7 and all the librabries; your operating system does not matter. I used Anaconda Spyder 3.3.2 and never had any issues.
How to run the code:
First, run the computational annotation (Step1_computational_annotation.py). It outputs the corpus needed.
Optional: Second, run the data investigation. It shows some nice facts and figures about our data.
Third, run the Step3_rule_based_doc_class.py - it classifies the data into Sluice and Non-Sluice.
Also third (or whenever you want), run the ML algorithm (ML_doc_class.py).
You can see both algorithm's performance in the print commands.

