# Semantic Consistency Checking of Automation Rules
This repository contains the supplementary material for the paper "A BERT-based Model for Semantic Consistency Checking of Automation Rules" submitted to the 29th International DMS Conference on Visualization and Visual Languages (DMSVIVA23).

This material comprises the dataset employed to train the classification model and the source code useful for the repeatability of the experiments.

# Introduction
According to the IFTTT creation paradigm, when a user creates a new applet, the creator must specify a natural language description that summarize how the applet works. By reading this field, a new user can more easily understand what an applet is for and decide whether or not to activate it on their device. However, on the part of IFTTT, there is no control over the content of the description entered by the user, so the creator could write anything, falsely describing the applet’s behavior. To this end, we developed a model that can check whether there is some semantic consistency between the trigger-action components of an applet and its natural language description provided by its creator. We fine-tuned a BERT-based classification model that takes as input a pattern derived from the applet components and the corresponding user-defined description and outputs a label ('entailment' or 'contradiction') and a similarity score for these two sentences.

# Creators
Bernardo Breve (bbreve@unisa.it), Gaetano Cimino (gcimino@unisa.it), Vincenzo Deufemia (deufemia@unisa.it), Annunziata Elefante (anelefante@unisa.it)

University of Salerno


# Dataset Information
In our study, we utilized the dataset proposed by Mi et al. [1] (<a href="https://www-users.cse.umn.edu/~fengqian/ifttt_measurement/">download</a>), which consists of a collection of IFTTT applets obtained from crawling the IFTTT.com site. This dataset includes crucial information such as a title (<i>Title</i>), a description explaining the applet behavior (<i>Desc</i>), the event triggering the applet (<i>TriggerTitle</i>) defined through a specific channel (<i>TriggerActionChannel</i>), the action to be performed (<i>ActionTitle</i>) selected from the corresponding channel (<i>ActionChannelTitle</i>), and the name of the applet creator (<i>Creator Name</i>).

We first defined a new pattern for <i>synthesizing</i> User-defined descriptions (UDDs) by carefully combining applet components, ensuring a coherent and accurate representation. Then, we conducted <i>dataset labeling</i>, a crucial process that involved assigning appropriate labels to the synthesized dataset, which enabled efficient categorization, organization, and analysis of the data. In particular, the pattern utilized for generating the synthesized UDD is as follows:

```
IF TriggerTitle (TriggerChannelTitle) THEN ActionTitle (ActionChannelTitle)
```

This standardized structure serves as a concise and comprehensive means of depicting the essential components and events associated with a specific applet. On the other hand, the UDD-pattern pairs were labeled according to the following similarity label values:

<ul>
  <li> <b> Entailment: </b> denotes consistency between the UDD and the synthesized pattern </li>
  <li> <b> Contradiction: </b> denotes inconsistency between the UDD and the synthesized pattern </li>
</ul>


An annotated sample is shown below.

```
{
    "Pattern": "IF Any new SMS received (Android SMS) THEN Send me an email (Email)",
    "Description": "A mail will be sent to yourself when you receive a sms",
    "Label": "Entailment"
}
```

# Relevant Papers

[1] Mi, X., Qian, F., Zhang, Y., Wang, X., 2017. An empirical characterization of IFTTT: ecosystem, usage, and performance, in: Proceedings of the Internet Measurement Conference, ACM. pp. 398–404

# Citation 

```
@article{brevebert,
  title={A BERT-based Model for Semantic Consistency Checking of Automation Rules},
  author={Breve, Bernardo and Cimino, Gaetano and Deufemia, Vincenzo and Elefante, Annunziata}
}
```
