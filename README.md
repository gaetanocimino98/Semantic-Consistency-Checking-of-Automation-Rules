# Semantic-Consistency-Checking-of-IFTTT-applets
In this paper, we propose a BERT (Bidirectional Encoder Representations from Transformers)-based model for semantic consistency checking of IFTTT applets. Our model uses pre-trained language representations to learn the semantics of applet components and identifies inconsistencies within the user-defined descriptions associated with applets.


# Introduction
According to the IFTTT creation paradigm, when a user creates a new applet, the creator must specify a natural language description that summarize how the applet works. By reading this field, a new user can more easily understand what an applet is for and decide whether or not to activate it on their device. However, on the part of IFTTT, there is no control over the content of the description entered by the user, so the creator could write anything, falsely describing the applet’s behavior. To this end, we developed a model that can check whether there is some semantic consistency between the trigger-action components of an applet and its natural language description provided by its creator. We fine-tuned a BERT-based classification model that takes as input a pattern derived from the applet components and the corresponding user-defined description and outputs a label ('entailment' or 'contradiction') and a similarity score for these two sentences.

### References
* ["An empirical characterization of IFTTT: ecosystem, usage, and performance"](https://doi.org/10.1145/3131365.3131369)


# Creators
Bernardo Breve (bbreve@unisa.it), Gaetano Cimino (gcimino@unisa.it), Vincenzo Deufemia (deufemia@unisa.it), Annunziata Elefante (anelefante@unisa.it)

University of Salerno


# Dataset Information
Overview:

* pattern: IF Any new SMS received (Android SMS) THEN Send me an email (Email).
* description: A mail will be sent to yourself when you receive a sms.
* similarity: This is the label chosen by the majority of annotators.

The applets were labeled according to the following similarity label values:

* Contradiction: indicates inconsistency between the description of the creator and the description synthesized.
* Entailment: denotes consistency between the description of the creator and the description synthesized.


# Setup the project
```
import numpy as np
import pandas as pd
import tensorflow as tf
import transformers
```
**Note**: install HuggingFace `transformers` via `pip install transformers` (version >= 2.11.0)
