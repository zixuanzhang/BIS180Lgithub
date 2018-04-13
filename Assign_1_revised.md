#### Assignment revised

# Template for Assignment1: Unix, git, and Sequence Alignment Assignments (20 pts possible)

__Full Name: Zixuan(Eleanor) Zhang__

__Student ID: 999622926__

*_Any code should be formatted as such_*

## Markdown

Paste the bio of your the student you interviewed here:

##### Biography of Lab Partner  
Her name: ruihan zhang  
Her major: __Biotechnology__  
Her year: _Senior_  

Table of living places:

| start year | end year | location|  
| :------------:| :-----------:| :---------:|  
| 1995|  2014  |  Beijing  |  
|2014 |  2018 | Davis |  

List of likes:  
* watch movies
* shopping
* study for bioinformatics

For more informatin about Ruihan, check out her [facebook webpage](/home/ubuntu/Assignment_2_Zhang.Eleanor/lab2_notebook.md)  

## Unix

Paste the `date` command that you used for exercise one here: _date "+%Y-%m-%d %A %H:%M:%S"_

## Git

Paste the URL for the shared github repository that you created with your lab partners here.  Use proper markdown formatting:

[Github repository](https://github.com/zixuanzhang/ruihan)


## Sequence Alignment

*_Please answer the following questions Be clear and concise with any written answers._*

** Unless otherwise noted we are not requiring you to include your code here.  However, I advise that you record it in a separate Markdown file for your reference.  That way if you need it again (e.g. for the midterm) you have a record of what you did**

__1.__ Paste in the result of the `ls -lR Data` command.  
```
Data:
total 8
drwxrwxr-x 4 ubuntu ubuntu 4096 Apr  6 14:33 Sequences
drwxrwxr-x 5 ubuntu ubuntu 4096 Apr  6 08:57 Species

Data/Sequences:
total 8
drwxrwxr-x 2 ubuntu ubuntu 4096 Apr  7 17:31 Genome
drwxrwxr-x 2 ubuntu ubuntu 4096 Apr  6 15:27 Proteome

Data/Sequences/Genome:
total 386328
-r--r--r-- 1 ubuntu ubuntu 121183082 Apr  6 14:59 A.thaliana.fa
-r--r--r-- 1 ubuntu ubuntu 102292161 Apr  6 15:05 C.elegans.fa
-r--r--r-- 1 ubuntu ubuntu 172113892 Apr  7 17:01 D.melanogaster.fa

Data/Sequences/Proteome:
total 66228
-r--r--r-- 1 ubuntu ubuntu 20006289 Apr  6 15:22 A.thaliana.fa
-r--r--r-- 1 ubuntu ubuntu 14931762 Apr  6 15:23 C.elegans.fa
-r--r--r-- 1 ubuntu ubuntu 32872415 Apr  6 15:24 D.melanogaster.fa

Data/Species:
total 12
drwxrwxr-x 2 ubuntu ubuntu 4096 Apr  7 17:33 A.thaliana
drwxrwxr-x 2 ubuntu ubuntu 4096 Apr  7 17:34 C.elegans
drwxrwxr-x 2 ubuntu ubuntu 4096 Apr  7 17:35 D.melanogaster

Data/Species/A.thaliana:
total 0
lrwxrwxrwx 1 ubuntu ubuntu 30 Apr  7 17:27 genome.fa -> Sequences/Genome/A.thaliana.fa
lrwxrwxrwx 1 ubuntu ubuntu 32 Apr  7 17:33 protein.fa -> Sequences/Proteome/A.thaliana.fa

Data/Species/C.elegans:
total 0
lrwxrwxrwx 1 ubuntu ubuntu 29 Apr  7 17:33 genome.fa -> Sequences/Genome/C.elegans.fa
lrwxrwxrwx 1 ubuntu ubuntu 31 Apr  7 17:34 protein.fa -> Sequences/Proteome/C.elegans.fa

Data/Species/D.melanogaster:
total 0
lrwxrwxrwx 1 ubuntu ubuntu 34 Apr  7 17:34 genome.fa -> Sequences/Genome/D.melanogaster.fa
lrwxrwxrwx 1 ubuntu ubuntu 36 Apr  7 17:35 protein.fa -> Sequences/Proteome/D.melanogaster.fa
```
__2.__ Paste in the markdown table from the lab manual that includes for each genome:

* Size of the file
* Number of chromosomes
* Size of the genome in bp
* Number of protein-coding genes
* Average protein length

|Species | size of file | Number of chromosomes | size of genome(bp) | number of protein-coding genes | Average protein length (aa.)|  
|:---------:|:------:|:-------:|:---------:|:--------:|:-------:|  
|A.thaliana| 121183082  | 5 | 121182529 | 35386 | 414|
|C.elegans| 102292161  | 6 |102292126  | 26769 | 452|
|D.melanogaster| 172113892 | 4 | 172111263 |30307| 672|

__size of file__  
_ls -l A.thaliana.fa_

__Number of chromosomes__  
_grep ">" A.thaliana_  

__Size of the genome in bp__   
*_grep ">" A.thaliana > At.header_*  
_wc -m A.thaliana_  
_wc -m At.header_  
_wc -l At.header_  

__Number of protein coding genes__  
*_grep ">" A.thaliana.fa | wc -l_*  

__Average protein length__  
*grep ">" A.thaliana.fa > At_P_header.fa*  
*wc -m A.thaliana.fa*  
*wc -m At_P_header.fa*  
*wc -l At_P_header.fa* 


For _ONE_ of the files, provide the code that you used to answer these questions.

__3.__ How do you know that when you use `shuffleseq` that the sequences have the same exact composition? 
 
```
We can firstly use `compseq`command to extract the word composition of original proteome sequence file.      
then use `compseq` again to extract the word composition of shuffled sequence file;    
Then use `diff` command to detect if there is any different in the word composition.    
If there is no output after this command executed, it means the shuffled sequence is exactly the same as the original file in respect to amino acids compositions.
```

__4.__ Create a text based "histogram" as described in the lab manual
that shows the distribution of scores when aligning shuffled sequences.  
```
7 26.0  
15 27.0  
43 28.0  
61 29.0  
95 30.0  
116 31.0  
99 32.0  
105 33.0  
85 34.0  
69 35.0  
75 36.0  
58 37.0  
37 38.0  
24 39.0  
33 40.0  
19 41.0  
15 42.0  
10 43.0  
5 44.0  
5 45.0  
11 46.0  
4 47.0  
3 48.0  
3 49.0  
1 50.0  
1 51.0  
1 53.0  
```

__5.__ Is the shape of the curve normal? Do you expect it to be normal?  
```
No, it is not normal.  
Maybe our sample size of 1000 is still small relative to the total number of possibility of shuffling a sequence.  
```

__6.__ Do you expect all protein comparisons to have the same distribution?
```
No. For proteins with high degree of similarities,   
the distribution will tend to have more higher alignment scores.  
```

__7.__ How would protein composition and length affect the scores?  
```
For a given score matrix we utilize, it prioritize certain type of amino acid substitution over others and thus assign higher score to them.   
So if the protein has relatively more of those types of amino acids,   
then the overall score will be higher.  
```

__8.__ How would the scoring matrix and gap penalties affect the scores?  
```
There are different scoring matrices which could fit for different types of alignments.   
For alignments among proteins with high degree similarities, we usually use Matrix 62.   
For distantly related organisms, we usually choose Matrix 45 to allow more divergent alignments.  
Gap penalty will significantly impact the alignment score because introducing any gap into the alignment will cut down the score by certain value we decide beforehand.  
```

__9.__ How many amino acids can be aligned per second?  How many amino acids need to be aligned for the experiment?  How long would it take to compare the two proteomes?  
```
346/0.01s = 34600 aa./s
When we align protein vs. protein, about 34600 amino acids can be aligned per second.  
For the experiment, the length of query is about 346 aa, while the length of whole proteome of A.thaliana is around 14649804 aa.   
So it take about 14649804/34600 = 423s to compare two proteomes
```

__10.__ Starting with the C. elegans B0213.10 protein, find the best
match in the A. thaliana and D. melanogaster proteomes with `water`.
Record their alignment scores, percent identities, and protein names
here.  (Use a markdown table!)  

|categories |  A.thaliana | D.melanogaster |
|: -----:| : ------: | : -------:|
|best match score | 337| 333|
|percent identities| 28.2% | 26.3% |
|protein name| AT2G23190.1 |FBpp0074380; FBpp0074381|

__11.__ What is the expected (average) score of each pairwise alignment
at random? (Perform some shuffled alignments to get an idea of what the
random expectation is).  
```
Shuffled B0213 with A.thailia  
median:  35

Shuffled B0213 with D.M  
Median: 35
```

__12.__ How many Z-scores away from the mean is the best alignment?  
```
The best alignment should have a very large Z score with extremely small p value,   
such that this best alignment will have very small e value.
```

__13.__ Briefly discuss the statistical and biological significance of your results.  
``` 
