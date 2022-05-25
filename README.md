**"Hey dude, are you gonna take one of those exams?": The Relationship Between Test-Taking Percentage and Benchmark Scores Percentage**

### Problem Statement
The percentage of 12th grade students from each California high school who take either the ACT or SAT varies widely between schools.   This project seeks to determine whether a relationship exists between the percentage of 12th grade students from each school who take either exam and the percentage of 12th grade students from each school whose scores meet the respective benchmarks.

### Data Dictionaries
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**school_code**|*float*|2019 ACT Scores in California by School|Official and unique identification code assigned to each California school| 
|**grade_12_total_enrollment**|*float*|2019 ACT Scores in California by School|The number of students enrolled in Grade 12 in each California high school during the 2018-2019 school year|
|**grade_12_test_takers**|*float*|2019 ACT Scores in California by School|The number of 12th Grade students from each California high school who took the ACT during the 2018-2019 school year|
|**percentage_test_takers_who_scored_at_least_21**|*float*|2019 ACT Scores in California by School|The percentage of 12th Grade students from each California high school who obtained an ACT score of at least 21 out of 36 during the 2018-2019 school year|
|**percentage_of_test_takers**|*float*|2019 ACT Scores in California by School|The percentage of 12th Grade students from each California high school who took the ACT during the 2018-2019 school year|

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**school_code**|*float*|2019 SAT Scores in California by School|Official and unique identification code assigned to each California school| 
|**grade_12_total_enrollment**|*float*|2019 SAT Scores in California by School|The number of students enrolled in Grade 12 in each California high school during the 2018-2019 school year|
|**grade_12_test_takers**|*float*|2019 SAT Scores in California by School|The number of 12th Grade students from each California high school who took the SAT during the 2018-2019 school year|
|**percentage_grade_12_test_takers_meeting_both_benchmarks**|*float*|2019 SAT Scores in California by School|The percentage of 12th Grade students from each California high school whose SAT scores met both the Evidence-Based Reading and Writing Benchmark and the Math Benchmark during the 2018-2019 school year|
|**percentage_of_test_takers**|*float*|2019 SAT Scores in California by School|The percentage of 12th Grade students from each California high school who took the SAT during the 2018-2019 school year|

### Outside Research
**College-Going Culture refers to the environment and attitudes present in a school that encourage students and their families to obtain the necessary tools for accessing a college degree. There are nine elements of a strong College-Going Culture, one of which is Testing and Curriculum.**
Source: https://cep.berkeley.edu/home/about-cep/college-going-culture

**The Testing and Curriculum element of a strong College-Going Culture refers to a student body that is knowledgeable about entrace exams like the ACT and SAT.  Schools with a strong College-Going Culture encourage lowerclassmen to take the PSAT and help upperclassmen register for the SAT.**
Source: https://k16.cuny.edu/wp-content/uploads/sites/16/2016/12/LH-College-Going-Culture-Principles-Chart-and-Rubric-8-15-2016.pdf

**Students who take the PSAT, as those in schools with a strong College-Going Culture often do, later obtain a higher average SAT score than those student who don't take the PSAT.**
Source: https://secure-media.collegeboard.org/digitalServices/pdf/research/2013/TotalGroup-2013.pdf


### Summary of Analysis

I decided to utilize the percentage of 12th Grade students from each Californoa high school who took the ACT/SAT during the 2018-2019 school year as a measure of that school's College Going Culture.  As such, I predicted that I would find a positive correlation between the percentage of test-takers at each school and the percentage of students who obtained benchmark scores.  

I utilized the act_2019_ca.csv dataset, which contains data about the number of 12th grade students at each California high school who took the ACT exam in the 2018-2019 school year, the number of 12th grade students enrolled in the 12th grade at each California high school, and the percentage of 12th grade test takers at each school whose ACT composite scores were at least 21 out of 36.

I also utilized the sat_2019_ca.csv dataset, which contains data about the number of 12th grade students at each California high school who took the SAT exam in the 2018-2019 school year, the number of students enrolled in the 12th grade at each California high school, and the percentage of students at each school whose scores met both the Math Benchmark score, which was 530 out of 800, and the Evidence-Based Reading and Writing score, which was 480 out of 800.  The College Board considers a student to be ready for college if their SAT scores meet both benchmarks.  

I began by importing the both datasets and printing the first 5 rows to get a feel for each dataset.  I then checked for any missing values which could alter the results of my Exploratory Data Analysis.  I proceeded to use the .describe() method, which allowed me to check for obvious errors.  After initially having a hard time believing that one school could have almost half a million 12th Grade students enrolled, I realized that this was the total number of 12th Grade students enrolled in the state of California during the school year in question.  I proceeded to fix the data types of the variables I would be using, and then displayed the data types in order to ensure that this change had been made.  I then renamed the columns so that they were more descriptive, contained only lowercase letters, and did not contain any spaces.  At this point I proceeded to save a "clean" copy of each of the datasets.  

Now that a clean copy of each of the datasets was saved in my repository, I felt comfortable making additional changes to the datasets.  I first dropped the columns I wouldn't be using from each one.  I was no ready to calcualte the percentage of 12th Grade Students at each school who took either test.  Each of these datasets included both the number of students enrolled in the 12th Grade and the number of 12th Grade students who took each test, which enabled me to calculate each school’s test-taking percentage for both the ACT and the SAT.  i had kept the 'school_code' column due to the fact that this served as a unique identifer for each school in the state.  There were, however, several rows which had a school code of 0.0, which was an error in the dataset that did not enable me to uniquely identify these schools.  In the ACT dataset, this error was present 59 times - once for the row which contained data for the entire state, and once for each of the 58 counties.  In the SAT dataset, this error was present in a couple hundred rows.  These rows all had to be removed from the dataset since I was calculating and comparing each school's unique percentages, and this identifer was necesssary in order to distinguish each school's data.  

I then dropped rows from both datasets in which the percentage of test-takers who obtained benchmark scores was over 100.00, since these were obviously erroneous data points.  I did the same for the rows in which the percentage of students in 12th grade enrollment who took either test was over 100.00, since thesewere also erroneous data points.  I proceeded to save this cleaned dataframe as a csv file.

I finished by running the .corr() method and generating a heat map, which allowed me to realize that both of these variables in the ACT and SAT datasets were not correlated in any way.  I finished by creating a scatterplot that displayed the non-existent relationship.

### Conclusions/Recommendations
After exploring the data, I came to the conclusion that there was no relationship between a school's percentage of 12th Grade Students who take the ACT and its percentage of students who obtain a composite score of at least 21 out of 36. No correlation existed between these two variables.

The same was true for the relatinoship between a school's percentage of 12th Grade Students who take the SAT and its percentage of students whose scores met both the Math and Evidence-Based Reading and Writing Benchmark scores on said exam. No correlation was found between these two variables either.

This suggests that schools with a large test-taking population do not tend see a higher percentage of students obtain benchmark scores, nor do schools with a small test-taking population tend to see a lower percentage of students obtain benchmark scores on either exam. A student's likelihood, therefore, of obtaining benchmark scores is not related to the percentage of his or her peers who also take either test.

### Citations
https://cep.berkeley.edu/home/about-cep/college-going-culture
https://k16.cuny.edu/wp-content/uploads/sites/16/2016/12/LH-College-Going-Culture-Principles-Chart-and-Rubric-8-15-2016.pdf
https://secure-media.collegeboard.org/digitalServices/pdf/research/2013/TotalGroup-2013.pdf

### Image Citations
california-graduation-cap.png
Source: https://i.pinimg.com/originals/fe/3f/cd/fe3fcd7142585b441e55bf22a1cac397.jpg
path-to-higher-education.jpeg
Source: https://dailyhousehold.com/wp-content/uploads/2014/08/path-to-higher-education.jpg
students-different-goals.jpeg
Source: https://media.istockphoto.com/vectors/people-climbing-on-book-stairs-for-diploma-scroll-education-knowledge-vector-id1063212874?k=6&m=1063212874&s=170667a&w=0&h=KWEzAXaO1vuFO4LjHF4ficOkc-IZL1JQ0mXYE2yX0RU=

