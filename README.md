prereq: gensim, numpy.

#for data
uploaded here:
https://drive.google.com/file/d/0B6UrE1zfRs68Rm9kM2ZyOFBkbEk/view?usp=sharing
has a "docdict.pickle" stores a dictonary mapping from document_ids to documents
and tag-data.xml

#for running LDA
1. Download the data from http://nlp.uned.es/social-tagging/wiki10+/. Download both the files: wiki10+_tag-data.tar.gz and wiki10+_documents.tar.bz2 and extract both.
2. Create a file containing docuemnt texts in format "docID: text" using all the docs in wiki10+_documents.tar.bz2. Name it as "docText". Create a mapping doc to tag and save it in "doctag.txt".
3. Run "python tag_extractor.py". Copy the top 25 tags from output to a file "topcategories". Now run "python transformTopCateg.py".
4. Now run "python createXML.py" and compress the output file "new.xml" in bz2 format. Name it as "wiki.tar.bz2".
5. Install gensim from https://radimrehurek.com/gensim/install.html and run script "python -m gensim.scripts.make_wiki wiki.tar.bz2 wiki_en"
6. Extract the contents of file "wiki_en_wordids.text.bz2". Now run "python lda.py". It'll generate all the topics in file "topics". Open the file and remove all other logs except the topics.
7. Run "python createQueryFile.py"
8. Run "python "docTopicDistribution.py"
9. Run "python mapcateg.py".
10. Now open "queries" file and "topictag" file. Manually check which topic is matched to which query and keep on the best category in "topictag" file for that paricular topic. Remove others.
11. Run "python ldaTest.py" to check the accuracy of learnt model.
12. To test any random text. Write it in file "test" and run "python testRandom.py".
