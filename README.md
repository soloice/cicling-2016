# cicling-2016
Source code for the CICLING 2016 paper "Optimize Hierarchical Softmax with Word Similarity Knowledge."

In this paper, we proved the legitimacy of using Huffman tree in hierarchical softmax.  Then, inspired by the plain thought that if the Huffman tree are organized with word similarity (i.e. There might exist many Huffman tree, we choose to put similar words closer.), it could produce better word embeddings. It turns out to become better.

Our algorithm is: Firstly, form an arbitrary Huffman tree. Then adjusting the tree bottom up layer by layer. Within each layer, using perfect match to pair similar nodes.  The effectiveness of the adjusting algorithm can be seen in the `/res` folder.
