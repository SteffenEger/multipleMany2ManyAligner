# multipleMany2ManyAligner (MM2M)

This program aligns multiple sequences in a monotone many-to-many manner. 
Programs have been tested on Ubuntu 12.04. They require Python 2.7x.

There are two aligners:

  (1) *multipleAlign_aligner.py*: Slow (allows to align 4 or fewer strings in reasonable time) but more accurate

  (2) *multipleAlign_segmenter.py*: Faster but less accurate


## REQUIREMENTS

  A bi-aligner, that is, an aligner that aligns pairs of strings/sequences. (In actuality, you only need bi-aligned training data.)

  Good bi-aligners can be found from e.g.:

  https://code.google.com/p/m2m-aligner/, M2M aligner

  http://de.osdn.jp/projects/mpaligner/, Mpaligner

  https://code.google.com/p/phonetisaurus/, Phonetisaurus aligner

## DATA FORMAT

  * (1) multipleAlign_aligner.py

    If you want to align N+1 sequences, you must have N bialigned files, each of the form 

    segmented-X-string   segmented-Y-string

    segmented-X-strings should always be from the same alphabet (e.g. letter words) in all N files
    segmented-Y-strings may be different (e.g. phonetic) representations of the X strings
    Sequences must be separated by a tab symbol.

    More precisely: if you want to align sequences of the form X Y_1 Y_2 ... Y_N
    then the N files must be as follows: 

    File 1: Sequences of type X and Y_1 are bi-aligned

    File 2: Sequences of type X and Y_2 are bi-aligned

    ...

    File N: Sequences of type X and Y_N are bi.aligned

    Have a look at e.g. sampleData/wiki_ga.bialigned 

    The N different files do NOT need to have identical (number of) X-strings.

    Segment separators are, by default, "-". 
    Character separators are, by default, "|". 

    INPUT DATA: 
    	  See e.g. sampleData/matchedup_3.data 
	  Note: Input sequences must be separated by a tab symbol.

  * (2) multipleAlign_aligner_segmenter.py

    If you want to align N sequences, you must have N bialigned files, each of the form as above. 
    The first one contains segmented input strings in its second column (it may be the reverse of one of the N-1 other files). 
  

## RUNNING

  * (1) multipleAlign_aligner.py:

  Sample run is e.g.

        python multipleAlign_aligner.py sampleData/wiki_ga.bialigned sampleData/wiki_rp.bialigned <  sampleData/matchedup_3.data

  or 

        python multipleAlign_aligner.py sampleData/wiki_ga.bialigned sampleData/wiki_rp.bialigned sampleData/pte_ga.bialigned < sampleData/matchedup.data 

  If you want to modify settings, you can do so in settings.txt


  * (2) multipleAlign_segmenter.py: 

        python multipleAlign_segmenter.py sampleData/wiki_ga.bialigned.rev sampleData/wiki_ga.bialigned sampleData/wiki_rp.bialigned sampleData/pte_ga.bialigned < sampleData/matchedup.data

  
## REFERENCES

  If you use this, please cite the following papers:

  Eger, Steffen
  Multiple Many-To-Many Sequence Alignment For Combining String-Valued Variables: A G2P Experiment
  In: ACL, Association for Computational Linguistics, 2015. Accepted 


  Eger, Steffen
  Improving G2P from Wiktionary and other (web) resources.
  Interspeech 2015. Accepted.


Have fun!
Steffen Eger, 07/04/2015

steffen.eger@yahoo.com

