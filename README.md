# SQL-Swiggy_Restaurant_Analysis

# Create Database

Create Database Swiggy;

# Set the Databse to work on

Use Swiggy;

# Show All Record of Table

SELECT * FROM tbl_swiggy;

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/352818fa-b1e0-4804-b5d4-9308c8c404e7)
 

# Show All Record of Table

SELECT Count(*) Total_Data FROM tbl_swiggy;

 ![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/3be1603a-b27b-4ac3-a864-965b25054fb2)





# What is the most 2 common Cuisine Among the Restaurant in Dataset?

Select Count(*) as Total_Count,    cuisine
from tbl_Swiggy
Group by cuisine Order By Total_Count Desc Limit 2;
 
 
 ![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/7d7179ba-513e-4265-bbb3-28babf8272e6)


![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/38fc108d-6ef4-43d4-bb79-4301b862ff28)


 
# How many restaurant has rating greater than 4.5

select Count(distinct Restaurant_Name ) As Rating_Count 
from tbl_swiggy 
where rating > 4.5;

 
 ![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/a23c3669-790b-4f20-8de1-2bf2d70453e3)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/62d14b00-dbd5-4efb-a455-0659613267d8)

 
# Which is the top 1 City with Highest No of Restaurants ?

Select Count(distinct Restaurant_Name) Total,     City 
from tbl_swiggy
Group by City Order by Total Desc Limit 1;
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/98845dc9-45f2-4e98-87a2-073a3e0adea0)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/b5ca4f83-af3a-4c5c-9742-2e510f9f7580)
 
# How many Restaurant Have the word "PIZZA" in their name ?

Select Distinct Restaurant_Name from tbl_swiggy 
where Restaurant_Name like '%Pizza%';

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/35eae92b-eb70-4da9-92db-ffdcd8700745)
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/0b86c42c-c131-41d4-9045-99a0a8de8ae5)
 



# What is the average rating of restaurant in each city?

Select City,  avg(rating)  As Avg_Rating
 From tbl_Swiggy  Group By City,  Order by Avg_Rating DESC;
  
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/fa110685-b25b-4b63-9b92-95a317aa8f49)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/908cd9b0-8be0-4fde-bb93-a193e6da8f81)



# What is the Highest Price of Item Under the ‘Recommended’ Menu category for each Restaurant?

Select distinct Restaurant_Name, Menu_Category, Max(Price) As Highest_Price from tbl_Swiggy
Where Menu_Category = 'Recommended'
Group By Restaurant_Name, Menu_Category ;
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/9eb92876-d13e-40e9-85ce-059457d64bcc)
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/544fb3d9-d73d-4607-9cff-aff7d160cc25)


# Find the Top 5 Most Expensive Restaurants that offers Cuisine other than North India Cuisine?

Select 
	Distinct restaurant_name, cost_per_person 
from tbl_Swiggy 
where  cuisine != 'North Indian' 
Order By cost_per_person 
DESC Limit 5;

 ![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/77753297-5ee9-40c5-a613-88b129a6c51c)







# Find the Restaurant that Have an Average cost higher than the Total Average cost of all Restaurants  Together ?

Select 
	Distinct restaurant_name, cost_per_person
from tbl_Swiggy 
where cost_per_person > (
				Select avg(cost_per_person) from tbl_Swiggy
			        );
 
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/093b6fb8-3996-48bf-9a0a-d20a74e6801c)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/74483e32-369a-4b94-9c8b-b3c65d59346b)




# Retrieve detail of All restaurants that have the Same Name but located in Different cities ?

select 	t1.restaurant_name, t1.city, t2.city
from tbl_swiggy t1 inner Join tbl_swiggy t2
on 	t1.restaurant_name = t2.restaurant_name
and     t1.City <> t2.City;

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/59fb06f8-eb9f-47e2-b8bf-f669813a6641)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/9a1b2531-f09f-4c6c-b9a1-b8b7bc2a431d)
 
 
# which restaurants offers the Most No of Item In the 'Main Course' category

Select 
	Distinct restaurant_name, Count(Item) As Total_Item_Count
from tbl_Swiggy 
where menu_category = 'Main Course'
group By restaurant_name
Order By Total_Item_Count DESC;

 ![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/14e378af-147e-4b09-9765-f793c39f7ba7)

 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/0beb3208-e93f-4de7-adf2-ab87565cffa2)


# List The Restaurant providing the Lowest Average price for all Item?

Select Distinct Restaurant_Name, Avg(Price) as Avg_Price  from tbl_Swiggy
group by  Restaurant_Name
Order By Avg_Price ASC ;     
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/db77193a-34ba-4d1a-9195-3c3aed91745c)
   
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/b2866790-6bb4-4ebc-9fc7-62a75d0dc6c8)





# Which is the Top 5 Restaurant providing Number of Category?

Select 	Distinct Restaurant_Name, 
        count(Distinct Menu_Category) as Catefory_Count  
from tbl_Swiggy
group by  Restaurant_Name
Order By Catefory_Count Desc
Limit 5 ;              
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/f841de78-3c09-4573-a8fd-f528cb3a59dc)
 

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/46489998-0f96-4c12-998f-246fc3ea4488)



# List The all Menu Category

Select 	Distinct Menu_Category From tbl_swiggy ; 
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/9b56c09c-9ec1-4a9f-8ab5-cfa170938716)
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/632eba87-712a-4032-ac88-8ce44a455e51)

 
# Show Category Wise Total Item ?

Select 	Distinct Menu_Category,	Count(Distinct Item) as Total_Item
From tbl_swiggy
Group by Menu_Category
Order By Total_Item Desc ;    
 
![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/4751927a-ef87-4501-8256-d8164a60919f)

![image](https://github.com/Official-Vivek-Singh/SQL-Swiggy_Restaurant_Analysis/assets/129989230/149da2c5-c6dc-451d-9150-8c89784c5ff8)

 
Follow Me : https://www.linkedin.com/in/vivekvishwas/
