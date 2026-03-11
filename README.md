<p align="center">
  <a href="https://www.cambridge.org/">
    <img src="https://www.rainbowschoolparis.com/uploads/1/2/9/7/129767513/cambridge-assesment_orig.png" alt="Cambridge Assessment" width="150">
  </a>
</p>

# Cambridge Computer Science 15-Mark Solution
## (0478/22, Paper 2 – Algorithms, Programming and Logic, Feb/Mar 2025)
### Solved by Rayan Sajid

---

## Question:

A sports club uses a six-character alphanumeric membership code to identify each member of the club. 

The one-dimensional (1D) array `MemberID[]` is used to store the unique membership codes for club members. 

The two-dimensional (2D) array `Name[]` is used to store the names of the club members. The first and last name of each member will be stored in separate array elements. 

The system can store details for a maximum of 1000 members. 

The position of any member’s data is the same in both arrays. For example, the data in index 2 of `MemberID[]` belongs to the member in index 2 of `Name[]`. 

The variable `NewID` is used to input a new membership code. 

Write a program that meets the following requirements: 

• Provide a menu that offers the choices: inputting a new member, outputting a list of membership codes and first and last names, or stopping.  

• Input and validate a response to the menu.  

• When inputting a new member, input a new membership code and check that it contains six characters:  

○ If the new code is six characters, check it against all the previously stored membership codes to make sure it is unique.  

○ If the code is not unique, a new code must be entered and checked.  

○ If the code is unique, it is stored in the first available space in the appropriate array and the new member is required to enter their first name and last name, which are also stored in the corresponding location of the appropriate array.  

• When outputting a list of membership codes and names, output for each member: their membership code, first name and last name.  

• The program will continue until the stop option on the menu is selected.  

You must use pseudocode or program code and add comments to explain how your code works.  

You do not need to declare any arrays, variables or constants; assume this has already been done.  

You do not need to initialise the data in the arrays.  

You do need to initialise any variables or constants used if appropriate.  

All inputs and outputs must contain suitable messages.

---

## Pseudocode Solution

```pseudocode
REPEAT
    Stop <-- FALSE
	OUTPUT "Choose 1 for inputting member, 2 for outputting all the members and 3 to STOP"
	INPUT Choice
	CASE OF Choice
		1: // Doing input of customer details and Validation
			REPEAT
			    OUTPUT "Enter new membership code"
			    INPUT NewID
				
    			WHILE LENGTH(NewID) <> 6
	    			OUTPUT "Enter membership code, 6 digits only"
	    			INPUT NewID
		    	ENDWHILE
	   			Count <-- 1 
	     		Found <-- FALSE
		   		REPEAT
		    	    IF MemberID[Count] = ""
			          Found <-- TRUE
    			    ELSE
	   			      Count <-- Count + 1
	    		     ENDIF
	    		UNTIL Found
		    	UNIQUE <-- TRUE
    			FOR i <-- 1 TO Count
    			    IF MemberID[i] = NewID
	   			      Unique <-- FALSE
    			     ENDIF
	   			NEXT i
	    		IF Unique = FALSE
			   	  OUTPUT "Not unique, pls retry"
	    		ENDIF
	   		UNTIL Unique
	    	OUTPUT "Input first name"
	   		INPUT Name[Count,1]
	   		OUTPUT "Input last name"
	   		INPUT Name[Count,2]
	   	2: // Output all details of all customers
	   	        // Find index of the first empty space
	   	    Count <-- 1 
	        Found <-- FALSE
		   	REPEAT
		        IF MemberID[Count] = ""
		          Found <-- TRUE
    		    ELSE
	   		      Count <-- Count + 1
	   		     ENDIF
	   		UNTIL Found
	   		// Output the ID, first and last name
	   		FOR j <-- 1 TO Count
	   		    OUTPUT MemberID[j]
    		    OUTPUT Name[j,1]
	   		    OUTPUT Name[j,2]
    		NEXT j
    	3: Stop <-- TRUE
    	// Validation for input of choice
    	OTHERWISE OUTPUT "Invalid Choice"
    ENDCASE
UNTIL Stop
