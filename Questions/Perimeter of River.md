## Finding the perimiter of a river
Suppose you're given a matrix of 1s and 0s that represents a map of rivers. You can assume that the grid cells in your map are only connected horizontally and vertically (e.g. no diagonal connections). You can assume that 1 represents water (your river) and 0 represents land/your river bank. Each cell has a length of 1 and is square in your map. Given this, write code to determine the perimeter of your river.


    
Examples:


    
    
Input: [[1,0]] 
    

Output: 4
    


    

Input:  [[1,0,1],  [1,1,1]] 
    

Output: 12


## Solution:


```python:
def parimeterofriver(arr):
  p=0
  for i in range(len(arr)):
    t=0
    for j in range(len(arr[0])):
      if arr[i][j]==1 :
        
        t=4
        if (i-1 >=0) and (i-1< len(arr)):
          if arr[i-1][j]==1:
            t=t-1
        if ((i+1) < len(arr)):    
          if arr[i+1][j]==1:
            t=t-1
        if (j-1 >=0) and (j-1< len(arr[0])):
          if arr[i][j-1]==1:

            t=t-1
        if ((j+1) < len(arr[0])):
          if arr[i][j+1]==1:
            
            t=t-1
        p=p+t


  print("perimeter=",p)
           
```
```python:
parimeterofriver([[1,1,1]])
```
