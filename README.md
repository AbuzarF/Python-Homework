from pathlib import Path
import csv

# Set the path using Pathlib
csvpath = Path('C:/Users/ABUZAR/FINTECHMAIN/UTOR-VIRT-FIN-PT-08-2022-U-LOLC-main/Homework/02-Python/Instructions/PyBank/Resources/budget_data.csv')

# Initialize Variables
line_num = 0

total_months = 0

month_list = []

total_revenue = 0

revenue_list = []

# Open the input path as a file object
with open(csvpath, 'r') as csvdata: 

  ## Pass in the csv file to csv.reader() function   
  ## (With ',' as the delimiter/separator) and return the csv object
    csvreader = csv.reader(csvdata, delimiter= ',')
     
  ## Go to the next row from the start of  the file
  ## Which is often the first row/header) and iterate line_num by 1
  
    header= next(csvreader)
    line_num+= 1
    
  ## Read each row after the header
    for row in csvreader:
        total_months+= 1 
        month_list.append(str(row[0]))
        
  ## Convert the number in the csv file from list to int 
  
        total_revenue= total_revenue + (int(row[1]))
        revenue_list.append(int(row[1]))
        
  ## Print out total_months and total_revenue
  
print(f"Total months: {total_months}")

print(f"Total revenue:$ {total_revenue}")
    

# Initialize matric variables
max_loss= 0

max_gain= 0

difference_total= 0

count= 0

difference_total_list= []


## Calculate the average change

for x in range(1,len(revenue_list)):

    difference_total_list.append(revenue_list[x]-revenue_list[x-1])    
    difference_total= difference_total+(revenue_list[x]-revenue_list[x-1]) 
    count= count+1     
print(f"Average change: $ {difference_total/count}")

# Initializing variable matrics
difference_total_dic= {}

month_index= 1

max_month=''

min_month=''

 ## Logic to determine max and min difference 
 
for difference in difference_total_list: 

    if max_loss== 0:
        max_loss= difference      
        max_month= month_list[month_index]      
    elif difference > max_gain:
        max_gain= difference    
        max_month= month_list[month_index]   
    elif difference < max_loss:  
        max_loss= difference    
        min_month= month_list[month_index]       
    month_index= month_index+ 1

print(f"Greatest increase,:{max_month} $ {max_gain}")

print(f"Greatest decrease,:{min_month} $ {max_loss}")


 
 
 
 # Result
 
 
   Total months: 86
   
Total revenue:$ 38382578

Average change: $ -2315.1176470588234

Greatest increase,:Feb-2012 $ (1926159)

Greatest decrease,:Sep-2013 $ (-2196167) 
      


    




    
    
    
    
