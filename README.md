# SkipBranchingLogic

:::::::::::::::::::::::::::::::::::::::
Complex Skip Logic (CSL) plus Branching
:::::::::::::::::::::::::::::::::::::::

How to build branching/skip survey logic. Useful any user-driven content.


This project will be built using SQL, C# and Angular.  I'm sure there is a pattern for this, and I will identify it and update the
info here.  This pattern could be re-used for dynamically changing the value of Labels on UIs as well as other instances that 
I will explore further and update here.

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





