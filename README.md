
# Math Test Performance Analytics Dashboard

### Snapshot of Students Data and Final Excel Dashboard:

![Image](https://github.com/user-attachments/assets/d5c1044b-c109-4e74-a5b7-0a601ee4efe3)

## Project Description:

This dashboard analyzes the performance of 30 grade 5 students on recent math tests. It includes key metrics such as final grades, past failures, attendance, study time, and health. Users can sort and filter students by academic and multiplke lifestyle factors to identify patterns in performance.



## Key Features

- Interactive sorting and filtering by absences, study time, health, family size, travel time, final grade
- Color-coded final grades (A–F) with visual markers to flag students at risk
- Line charts showing trends in each student's last three math test scores
- Slicers for dynamic selection of sorting fields (e.g., failures, attendance)
- Visual indicators for health (heart icons), attendance (bar fill), and travel time (clock icons)
- Structured Excel table and chart layout for fast interpretation of student-level data


## Use Cases

- Teachers: can spot students who are falling behind and need extra help early
- Academic counselors: Track risk factors like poor health and frequent absences to guide interventions
- School leaders: Evaluate overall grade 5 math performance and common student challenges
- School administrators can track trends in student performance
- Tutoring programs can focus on students who miss class or study less
- Parents can use visual data to understand student habits and outcomes
- Data teams: can follow key factors using basic and academic outcomes using simple Excel functions



The dashboard helps highlight students at risk, track academic trends, and helping teachers identify struggling students early and decide who needs extra help based on real data.


## Technical Details
- Tool: Microsoft Excel



## Step-by-Step Data Analysis & Visualization Process in Microsoft Excel

### 1.  Data Cleaning & Preparation
Checked for missing values, fixed data entry errors, and ensured consistent formats across all columns. This step made the dataset reliable for analysis.


![Image](https://github.com/user-attachments/assets/c1936607-fd5c-45b4-8d7c-68e8e3f86e51)

### 2. Slicers

I Build a Dynamic Filter & Slicer for Key Performance Factors

![Image](https://github.com/user-attachments/assets/6aafd82f-b390-4d18-bb23-8d1d8f8acbc2)


To make this work, I create:
- A dummy table listing key performance factors
- A dynamic array to switch between ascending and descending sorting
- Converted both dummy tables into pivot tables
- Added slicers to control sorting and filtering
- Linked the slicers to the main dashboard view to allow users to select perfomance fators dynamicly 

![Image](https://github.com/user-attachments/assets/785f2a32-ac03-4ea5-aa02-5df518e33100)

This made the dashboard fully interactive and user-friendly.


### 3. SORTBY Dynamic Array Student ID Column
I used SORTBY Formula to create a dynamic array that sort the Student ID column by different performance factors

            SORTBY(StudentData12[Student ID],INDEX(StudentData12,,MATCH ('Working-Marwahs'!D3,StudentData12[#Headers],0)),'WorkingSheet-Marwahs'!F15)


### 4.  INDEX & MATCH Gender Column
I used Index and Match Functions to return all gender values based on Student ID column.

        INDEX(StudentData12[gender],MATCH(A5#,StudentData12[Student ID],0))

### Student ID, Gender Columns (Snapshot)

![Image](https://github.com/user-attachments/assets/3c7608ba-4dd4-47d2-936d-d828756e53e7)


### 5. Symbols for grades
 I used Index and Match Functions to return all Color-coded final grades (A–F) values based on Student ID column  dot symbol to flag students at risk by using IF Function

Example: 
          IF($C$5#=D4,$B$1,"")
            If final Grade column = F then return Dot symbol, if not return  nothing " "


![Image](https://github.com/user-attachments/assets/5ec93135-24a3-4e5c-8eb7-b8728aa5b7f0)

### 6. Sparklines 
I used Sparklines to show how each student’s math scores changed from Test 1 to Test 3, making it easy to spot improvement or decline

![Image](https://github.com/user-attachments/assets/e2d0c38b-a259-4a2e-9557-327a9db9e335)

I write a formula to return all three test scores columns using INDEX function and match it to the Student ID column then turn it into Dynamic Named Range. 

         INDEX(StudentData12[[1st Score]:[Final Score]],MATCH(A5,StudentData12[Student ID],0),0)

Go to Formula tab, Click Define Name, give the range name and paste the formula in Refer to field

![Image](https://github.com/user-attachments/assets/e2d0c38b-a259-4a2e-9557-327a9db9e335)

Create the Sparklines

![Image](https://github.com/user-attachments/assets/c9cca7c3-63b8-41f7-a2a6-15e44e80b061)

### 7. Failures column & Custom Number Format
Failures column & Custom Number Format, Return all the values based on Student ID using the same previous function then Apply custom format to present positive and negetive values only

         INDEX(StudentData12[failures],MATCH(A5#,StudentData12[Student ID],0))
![Image](https://github.com/user-attachments/assets/000d9d50-e6c4-43ae-88cd-2be4c7ac948d)

![Image](https://github.com/user-attachments/assets/7cbbcf5c-9502-478a-bc87-2fc5dae7824a)

Failures Factor Legend

![Image](https://github.com/user-attachments/assets/e00741dc-225c-44aa-9ae0-fc446de5e010)


### 8. Study Time & In-cell chart column
I used the INDEX and MATCH functions to return study time values for each student:

      INDEX(StudentData12[study time],MATCH(A5#,StudentData12[Student ID],0)

![Image](https://github.com/user-attachments/assets/600390e1-8727-4d51-ac4b-bf690a5c2e85)


To visualize study hours, I created an in-cell bar using the REPT function.
I wrapped the INDEX formula inside REPT to repeat dashes based on the study time value. The lowercase "l" at the end helps mark the end of the bar.
This creates a consistent visual scale to compare how much time each student spent studying.

       REPT("---",INDEX(StudentData12[study time],MATCH(A5#,StudentData12[Student ID],0)))&"l"

![Image](https://github.com/user-attachments/assets/24db75a9-8f84-4fca-91bc-cfaf35fc4ab4)

#### Study Time Legend (Snapshot)
![Image](https://github.com/user-attachments/assets/65082dea-7398-448f-83a5-9ca5da7f35ed)



### 9. Absent time & conditional Formatting Bars
I used the INDEX and MATCH functions to return each student's number of absences. Then I applied Data Bars using Conditional Formatting to visualize absence levels directly in the cell. Format the Number to present positive values
This made it easy to compare how much class time each student missed.


      INDEX(StudentData12[absences],MATCH(A5#,StudentData12[Student ID],0))

![Image](https://github.com/user-attachments/assets/ba6be0f8-266b-42df-9ee5-8c12fd6b4e8a)

### 10. Time Travel & conditional Formatting Icon

         INDEX(StudentData12[travel time],MATCH(A5#,StudentData12[Student ID],0))

I used the INDEX and MATCH functions to return travel time values for each student
Then I applied Conditional Formatting using an Icon Set and Chose the Clock icon style.
Customized the settings to represent travel time ranges:
-	1 = 15 minutes
-	2 = 30 minutes
-	3 = 45 minutes
-    4 = 60+ minutes
This visual approach helps compare student commute times quickly.


![Image](https://github.com/user-attachments/assets/63518863-a621-428e-b381-7b7233b6916d)

### 10. Family Size Column
         =INDEX(StudentData12[Family Size],MATCH(A5#,StudentData12[Student ID],0))
![Image](https://github.com/user-attachments/assets/02902fd2-2338-4762-9d41-2a172cacfd03)


### 11. Health & Emoju Chart

I used the INDEX and MATCH functions to return each student’s health score (from 1 to 5):
-	1 = Poor
-	5 = Excellent

To visualize the health level, I used the REPT function with a heart emoji.
Each heart represents one point on the health scale, making it easy to compare student well-being at a glance.

        REPT("🤍",INDEX(StudentData12[health],MATCH(A5#,StudentData12[Student ID],0)))

![Image](https://github.com/user-attachments/assets/046cb49c-83d7-4748-b2d4-aacd0503cea2)

### 12. Line Chart – Average Score Trend

I created a line chart to show the overall average score trend across the three math tests.
     AVERAGE(StudentData12[1st Score])
![Image](https://github.com/user-attachments/assets/9c62efca-538a-4846-ad03-7e2cc51ff03e)

- Calculated the average score for each test (Test 1, Test 2, Test 3) in a separate table


![Image](https://github.com/user-attachments/assets/b5310a16-36ed-41d7-bd13-6ca10b32751c)

- Inserted a line chart to display how class performance changed over time
- Applied formatting to highlight the line and make data labels easy to read
    
This chart helps visualize whether student performance is improving, stable, or declining across tests.

![Image](https://github.com/user-attachments/assets/b27460c5-466c-4cbd-ac14-c4beceb3be96)









