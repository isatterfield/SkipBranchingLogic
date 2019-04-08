# SkipBranchingLogic

:::::::::::::::::::::::::::::::::::::::
Complex Skip Logic (CSL) plus Branching
:::::::::::::::::::::::::::::::::::::::

How to build branching/skip survey logic. Useful for many user-driven content scenarios.

This project will be built using SQL, C# and Angular.  I'm sure there is a pattern for this, and I will identify it and update the
info here.  This pattern could be re-used for dynamically changing the value of Labels on UIs as well as other instances that 
I will explore further and update here.


There are two distinct paths the user can be directed: sequentially-driven or context-driven.

Sequentially Driven
-------------------
It is fairly straight-forward to set-up and manage sequentially driven logic and its data.  Select the branch, i.e. a grouping mechanism to be presented in the workflow, then track which question should be present. 	Ex:

✔    select * from table where QOrder = @tmpCounter+1 and BranchMstrKey=<<guid>>

Beginner Note: To retrieve the proper branch key, valid date ranges could be used or a simple on/off bit.  More than likely, the BranchMstrKey guid will need to be stored in a subject-specific table.  In other words, if I have launched a survey from an email sent out, I would include the BranchMstrKey in the link or I could store the key with another datasource and have it returned with that data query to start the related questionnaire.  
  

--for sequential driven questions
select Question from A where AnswerGroupKey = 788 and QLvl = counter+1


============================ E N D ====================================================

## next section begins notes, not yet ready for reference ##







 


/*
there are two paths - either answer driven or sequential
to determine if the path is answer driven:
if (answer == typeof(guid) and QLvl is Null)//find next question based on answer
	select * from table where AnswerGroupKey = tmpGuid
else//follow the sequential driven path
	select * from table where QLvl = tempCounter+1 and AnswerGroupKey=blah


*/	


--we must always start with our branch of questions key and QLvl = 0
select * from Q WHERE QLvl = 0 and branchkey = '2BECA2BC-6731-427D-91F8-944B44A67FBC'
-- this will return the first question to begin the specific branch of questions


If we are about to begin a context-driven questionnaire, the query begins:
  select * from questions where BranchMstrKey = '9f534b31-f454-4f8e-bc7c-9c80b5ef763d'

Once this is performed, the questions and answers table will drive the context.


------------ D A T A B A S E   D E S I G N ----------------------------------------------------------------------------------

The database design will be imperative to making user-driven content fast and easy for end-users to manager thru
a UI, as well as developers to innately understand and support.

While sql scripts will be included for your use, we begin here:

Branches are used to manage the top-most level of grouping questions and answers together.  The BranchMstr provides
the GUID and description.  


SEQUENTIAL Question/Answer
By using both the BranchMstrKey and the QKey when selecting answers, answers can be re-used for different branch/questions.
Store the Answer.
Select the next QLvl of questions for this branch.
...repeat





