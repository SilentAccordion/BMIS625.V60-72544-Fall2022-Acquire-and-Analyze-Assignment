# BMIS625.V60-72544-Fall2022-Acquire-and-Analyze-Assignment


## Background

Originally from Japan, Haikus are a type of short form poetry consisting of three lines that follow a '5-7-5' syllable pattern. In this assignment, we found an archive of over 20,000 'SPAM' themed haikus and looked to examine how many of these poems actually followed the traditional haiku structure.  We also analyzed other components such as most frequent non-'stop' words, which, not surprisingly, included a lot of SPAM synonyms.  

## Acquire

To begin our acquisition, we found a archive of over 20,000 potential haiku poems, based on a central theme. This archive can be found here: http://web.mit.edu/jync/www/spam/

We wrote a short python script to download the collection, with consideration for the bandwidth of the host and stored them into a local SQLite DB. To do this, we setup two different tables, one for the results of the scraping and the other for the extracted poems. We then used a regular expression to find all possible matches in the cached page content storing the matches into the poem table in the database.

## Analyze

Using the Python package syllapy, we did some statistical evaluation of the poem database, looking for valid ('5-7-5')haiku. First we set up the syllable counter and then counted the syllables line by line for each poem.  When analyzing the minimum number of syllables, we found '0' for each line, while the mean was very close to the '5-7-5' format.  We then ran an additional analysis on 'bad words' or those not recognized by the dictionary.  Examples included 'NC-17:', "'40s", and '8th.'

## Results

We found about 57% of poems in the collection could be evaluated as valid, based on the limitations of both the poets and sullapy. When we loosened up the definition of a haiku, to allow 4 to 6 syllables on the 1st and 3rd lines, and 6 to 8 on the 2nd line, we improved to 90% matches. Some of the most common filtered words included: spam, pink, meat, pig, and pork. 

## A Few Examples 

### Haiku One 

```
The Truth About Cats
and Dogs: It's simple. They were
all made into SPAM.
```
```
The(1) Truth(1) About(2) Cats(1) => 5
and(1) Dogs:(1) It's(1) simple.(2) They(1) were(1) => 7
all(1) made(1) into(2) SPAM.(1) => 5
```
*Valid Haiku*

### Haiku Two 

```
Dear Hormel people:
I'll blow up your factory!
--Teddy Kaczynski
```
```
Dear(1) Hormel(2) people:(2) => 5
I'll(1) blow(1) up(1) your(1) factory!(3) => 7
--Teddy(2) Kaczynski(3) => 5
```
*Valid Haiku*

### Haiku Three
```
Mona Lisa smiles
so peaceful and knowingly
she before SPAM's time
```
```
Mona(2) Lisa(2) smiles(2) => 6
so(1) peaceful(2) and(1) knowingly(3) => 7
she(1) before(2) SPAM's(1) time(1) => 5
```

*Semi Valid Haiku*

### Haiku Four
```
Fried, boiled, mashed, raw, Probed;
SPAM breakfast, lunch, snack, dinner:
Have I a tapeworm?
```
```
Fried,(1) boiled,(2) mashed,(2) raw,(1) Probed;(2) => 8
SPAM(1) breakfast,(2) lunch,(1) snack,(1) dinner:(2) => 7
Have(1) I(1) a(1) tapeworm?(3) => 6
```

*Invalid Haiku*

![d3c44fa80bbcb2bedafa2ed89105e4ad6177dee8-1](https://user-images.githubusercontent.com/35873877/206303963-b664bb1c-4849-4ec9-9d31-e85fd39925b8.jpeg)
