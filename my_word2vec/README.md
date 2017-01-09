We used Blossom V (http://pub.ist.ac.at/~vnk/software.html) software package to implement best-matching on a general graph. What we modified (and what a user needs to check if he wants to improve the algorithm furthur) lies only in the my_word2vec.cpp, which is based on Mikolov's word2vec.

In my_word2vec.cpp, 2 kinds of word similarity knowledge can be utilized.
1. The first one is an ontology: if one knows some words have similar meaning, he can put it into a file, in which groups of synonyms are presented, and for each group, a number indicating the size of synonyms are given at first, then words in the group are listed, one word per row. See ../data/xin1991_level1.txt for an example.
2. The second one is a similarity matrix. The file consists of many lines, and in each line, 3 terms are given: <word1_id>, <word2_id>, <similarity_between_word1_and_word2>. The 3rd term is a float number ranges in [0, 1]. So in this usage, you need to have a vocabulary file in which word ids are specified. Look at ../data/wordlist-utf8.txt for an example. (In the first line, size of vocabulary is given. The second line is not used by our program. For the rest lines, only the first two terms-word_id and word_identity-are utilized.)


Usage:

You can use `make clean; make;` to generate `my_word2vec`. Then, to incorporate word similarity knowledge, the command is almost the same with the original word2vec, only with one or two more options.

For the first usage, you need to add a parameter `-ontology <ontology-file-name>`. For example, it could be:

./my_word2vec -train corpus.txt -output vec.txt -size 50 -window 5 -sample 1e-4 -negative 0 -hs 1 -binary 0 -cbow 1 -iter 3 -ontology ../data/xin1991_level1.txt


For the second usage, you need to specify `-sim <similarity_matrix_file_name> -wordlist <word_list_file_name>`. Say, it might be:

./my_word2vec -train corpus.txt -output vec.txt -size 50 -window 5 -sample 1e-5 -negative 0 -hs 1 -binary 0 -cbow 0 -iter 2 -threads 3 -sim sim_mat.txt -wordlist ../data/wordlist-utf8.txt
