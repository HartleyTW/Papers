## Title
Interpreting Deep Visual Representations via Network Dissection


## Authors
Bolei Zhou, David Bau, Aude Oliva, and Antonio Torralba


## Link
https://arxiv.org/pdf/1711.05611.pdf
http://netdissect.csail.mit.edu

## Published
CVPR 2017


## Date Read
18th October 2018


## Summary
This paper proposes a technique to apply a semantic concept (i.e. a label) to
the individual filters in a network, this allows the interpretability of a
network to be quantified. The core mechanism for labeling filters is through the
use of a new dataset they introduce called Broden (Broadly and Densely Labeled
Dataset).

Broden is an amalgamation of a number of different datasets, each representing
one of the following categories of label: Scene, Object, Part, Material, Texture
and Colour. Apart from the textures and scenes, these are segmented down to the
pixel level. Each image from the dataset is passed through the pretrained
network and the masked activation is then compared with the known segmented
areas in the broden dataset. An activation is only chosen for further comparison
if its value is in the top 0.5% of activation values. I imagine this is to
separate filters that activate with low values so as to keep them from being
used to label the filters. The filter interpretability is then scored using the
intersection over union score.

The experiments are numerous, especially in this extended version of the paper:
- Human Evaluation of Interpretations: A mechanical turk task was performed to
compare human interpretation of filters against the network dissection results.
It seems that humans and network dissection both find the task of labeling the
higher level filters easier than lower level ones.

- Measurement of Axis-aligned Interpretability: I failed to grasp what this was
initially, and it was only after discussions that we understood it was the
rotation of feature-space. This still hasn't quite clicked for me, but they
suggest that their hypothesis: "Interpretable alignments are unusual, and
interpretable units emerge because learning converges to a special basis that
aligns explanatory factors with individual units" explains the emergence of
interpretability.

- Network Architectures with Supervised Learning: Experiments condcted to
understand how interpretability varies across different architectures. In this
case interpretability is measured as the number of unique detectors in the final
convolution layer. They found that in general the deeper the architecture, the
greater the number of unique detectors (ResNet > DenseNet > VGG > GoogLeNet > AlexNet).


- Representations from Self-supervised Learning: Main takeaway from this for me
was that in self-supervised tasks the networks general don't learn many concepts
related to objects, rather they create more texture based filters. The filters
are also unique to the type of task i.e a network trained on black and white
images learns no colour filters.

- Representations from Captioning Images: Just showing how the network works
with CNN+LSTM and captioning images. Lots of object detectors occur.

- Training Conditions: Showing how different architecture elements (Dropout,
BatchNorm) effect the interpretability of the network. Of note is that the use
of BatchNorm reduces the interpretability of the network.

- Transfer Learning between Places and ImageNet: Two experiments run, finetuning
places to imagenet, and imagenet to places and seeing how the filters evolve
over
time. They have some nice results showing how a filter used for a waterfall
morphs into a filter for identifying dogs for example.

- Layer Width vs. Interpretability: This experiment explores how the width of a
layer (i.e the number of filters in it) affects the interpretability. Do more
filters allow for a greate number of concepts to be represented? Using AlexNet
they increased the number of filters in the final layer and found that whilst
accuracy remained consistent, more unique concepts were represented. They was a
limit however as to how many filters you could add before no more benefit was
found.

- Discrimination vs. Interpretability: This experiment attempts to disentangle
the idea of a networks discrimination powers against its interpretability. The
paper shows that even though a network may produce more unique object detectors,
it's overall accuracy can be less than a network with fewer unique object
detectors. They hypothesize that the networks that preform better with fewer
unique detectors, actually have filters that better capture the characteristics
of the data being passed through.

- Explaining the Predictions for the Deep Features: This shows how the network
disection technique can be used to visualise how regions of an image are being
labeled by the network for use in its decision making process.


## Takeaways

Impressed with breadth and depth of the experiments. I can see why it was
accepted to CVPR.

For me it feels like the paper is trying to force high level labels (i.e dog,
person, book store) on filters that don't represent such an abstract concept.
For example in a lot of cases a more general label would better encapsulate what
the filter is doing, so rather than 'grass', we might have 'green and textured'.

It would also be interesting to understand the distribution of classes in the
underlying dataset, would showing more classes of a certain type push the
labeling mechanism into biasing that dataset. For example there are a lot of
filters labeled 'dog' that could easily, and potentially more accurately just be
labeled face.

