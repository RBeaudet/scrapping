# Scraping for Insurance Corpus v2

## Installation 
Use a [pipenv](https://pipenv.pypa.io/en/latest/) for quick install of requirements enumerated in the Pipfile.

## Description of the resulting corpus (FR)

### Wikipedia source
We used Wikipedia hands-on API for retrieving text files of a given subject. We limited our keyword based research in Wikipedia's article titles.

<ul>
<li> <b> Keywords </b> : TODO
<li> <b> Size of the JSON file </b> : TODO
<li> <b> Number of scrapped articles </b> : TODO
</ul>

### Twitter Source 
 We used [Twint](https://github.com/twintproject/twint) to bypass Twitter developper authentification, scrap tweets from a profile using a keyword and retrieving profile informations. We used a list of starting user accounts, a few main French insurance companies. For each of these companies, we search for tweets containing a list of keywords and stored mentions (users direclty cited in a tweet by a '@'). For each verified mentioned accounts, we operated the same research. We may enlarge our search by using the top 10 most used hashtags in the scrapped tweets. 

<ul>
<li> <b> Starting accounts</b> : @AXA, @Groupama, @AG2RLAMONDIALE, @Matmut, @Groupe_VYV, @MAIF, @GroupeMacif, @MAAFAssurances, @MMAssurances, @hmutuelle, @CNP_Assurances
<li> <b> Keywords </b> : assurance, assureur, mutuelle, prévoyance, réassurance, réassureur, actuariat, actuaire
<li> <b> Size of the JSON file </b> : 3 MB
<li> <b> Number of scrapped tweets </b> : 1584
<li> <b> Number of scrapped accounts </b> : 109
<li> <b> Average tweet length </b> : 164 words
<li> <b> Top 5 leads from most used hashtags </b> : #complémentairesanté, #protectionsociale, #AssureurMutualiste, #habitation, #Mutualisme
</ul>

### Specialized and generalized newspapers
#### <b> Description by source </b>
| Newspaper                 | Keyword research | Restricted to title | Best matches | Premium option | All articles |
|---------------------------|:----------------:|:-------------------:|:------------:|:--------------:|:-----:|
| Assurland                 |                  |                     |              |                | :heavy_check_mark: |
| FFA                       |:heavy_check_mark:|                     |:heavy_check_mark:|                | |
| L'Agefi                   |:heavy_check_mark:|                     |              |                | |
| L'Obs                     |:heavy_check_mark:|                     |              |                | |
| L'opinion                 |:heavy_check_mark:|                     |:heavy_check_mark:|                | |
| Le Figaro                 |:heavy_check_mark:|                     |:heavy_check_mark:|:heavy_check_mark:| | 
| Le Monde                  |:heavy_check_mark:|                     |              |:heavy_check_mark:| |
| Marianne                  |:heavy_check_mark:|                     |              |                | |
| Ouest France              |:heavy_check_mark:|                     |              |:heavy_check_mark:| | 
| Risques                   |:heavy_check_mark:|                     |              |                | |
| Tribune de l'Assurance    |:heavy_check_mark:|                     |              |:heavy_check_mark:| | 
| Université de l'Assurance |:heavy_check_mark:|                     |              |                | |

*N.B. Best matches may include false positive because retrieved articles are based on the website internal search best match.*

#### <b>Dataset structure</b>

| Newspaper                 | Size of the JSON file (MB)| Number of scrapped articles | Average sequence length (words)| Maximum sequence length (words)| Minimum sequence length (words)| 
|---------------------------|:-------------------------:|:---------------------------:|:-----------------------:|:-----------------------:|:-----------------------:|
| Assurland                 |                           |                             |                         |                         |                         |
| FFA                       | 4.8                       |                             |                         |                         |                         |
| L'Agefi                   | 0.443                     | 181                         | 497                     | 1413                    | 50                      |
| L'Obs                     | 2.6                       | 522                         | 442                     | 17451                   | 2                       |
| L'opinion                 | 3.4                       | 636                         | 452                     | 2440                    | 10                      |
| Le Figaro                 | 0.316                     | 1698                        | 391                     | 1009                    | 3                       |
| Le Monde                  | 3.5                       | 828                         | 347                     | 3038                    | 3                       |
| Marianne                  | 0.239                     | 56                          | 668                     | 13494                   | 23                      |
| Ouest France              | 0.153                     | 561                         | 250                     | 2170                    | 8                       |
| Risques                   | 1.7                       | 252                         | 474                     | 5519                    | 2                       |
| Tribune de l'Assurance    | 0.024                     | 5                           | 431                     | 1455                    | 70                      |
| Université de l'Assurance | 0.092                     | 42                          | 331                     | 1475                    | 5                       |
| Total | | | | | |

<br>
</br>

#### <b>Topics by newspaper</b>


| Newspaper                 | assurance | assureur | réassurance | réassureur | mutuelle |
|---------------------------|:---------:|:--------:|:-----------:|:----------:|:--------:|
| FFA                       |           |          |             |            |          |
| L'Agefi                   | 144       | 94       | 52          | 170        | 99       |
| L'Obs                     | 3522      | 424      | 0           | 28         | 1193     |
| L'opinion                 | 1222      | 1208     | 1097        | 140        | 1253     |
| Le Figaro                 | 259       | 52       | 76          | 38         | 58       |
| Le Monde                  | 6360      | 0        | 0           | 0          | 778      |
| Marianne                  | 235       | 24       | 0           | 0          | 66       |
| Ouest France              | 726       | 0        | 0           | 0          | 0        |
| Risques                   | 3239      | 80       | 0           | 0          | 7        |
| Tribune de l'Assurance    | 43        | 0        | 0           | 0          | 0        |
| Université de l'Assurance | 249       | 6        | 0           | 0          | 0        |

| Newspaper                 | mutualité | prévoyance | actuariat | actuaire | axa |
|---------------------------|:---------:|:----------:|:---------:|:--------:|:---:|
| FFA                       |           |            |           |          |     |
| L'Agefi                   | 57        | 157        | 4         | 15       | 42  |
| L'Obs                     | 170       | 0          | 0         | 55       | 181 |
| L'opinion                 | 809       | 992        | 91        | 241      | 211 |
| Le Figaro                 | 101       | 0          | 32        | 115      | 16  |
| Le Monde                  | 0         | 0          | 0         | 1255     | 1006|
| Marianne                  | 19        | 11         | 0         | 0        | 0   |
| Ouest France              | 0         | 0          | 0         | 0        | 0   |
| Risques                   | 0         | 0          | 0         | 0        | 2   |
| Tribune de l'Assurance    | 0         | 8          | 0         | 0        | 0   |
| Université de l'Assurance | 0         | 0          | 0         | 0        | 0   |
