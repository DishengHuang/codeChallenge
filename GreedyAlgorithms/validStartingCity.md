
# Valid Starting City

Imagine you have a set of cities that are laid out in a circle,
connected by a circular road that runs clockwise. Each city has
a gas station that provides gallons of fuel, and each city is some
distance away from the next city.

You have a car that can drive some number of miles per gallon of
fuel, and your goal is to pick a starting city such that you can 
fill up your car with that city's fuel, drive to the next city, refill
up your car with that city's fuel, drive to the next city, and so on
and so forth until you return back to the starting city with 0 or
more gallons of fuel left.

This city is called a valid starting city, and its guaranteed that 
there will be exactly one valid starting city.
### Sample Input

```python
distances = [5,25,15,10,15]
fuel = [1,2,1,0,3]
mpg = 10
```

### Sample Output

```python
4
```
### Solution 1 (Brute-Force Approach)
loop through the city one by one and then check whether any
mileage left.
```python
#Time O(n^2) / Space O(1)
def validStartingCity(distances, fuel, mpg):
	numberOfCities = len(distances)
	
	for startCity in range(numberOfCities):
		mileRemaining = 0
		
		for currentCity in range(startCity, startCity + numberOfCities):
			if mileRemaining < 0:
				continue
			
			currentCity = currentCity % numberOfCities
			
			fuelFromCurrentCity = fuel[currentCity]
			distanceToNext = distances[currentCity]
			mileRemaining += fuelFromCurrentCity*mpg - distanceToNext
			
		if mileRemaining >= 0:
			return startCity
		
	return -1
```

### Solution 2 (Minimum Mile Remaining)
find the city which contains the minimum mileage, and select that city as
the start city.
```python
#Time O(n) / Space O(1)
def validStartingCity(distances, fuel, mpg):
    miniMileRemaining = 0
	minimumCityIndex = 0
	mileRemaining = 0
	
	for index in range(1,len(distances)):
		prevFuel = fuel[index - 1]
		prevCityDistances = distances[index - 1]
		
		mileRemaining += prevFuel*mpg - prevCityDistances
		
		if mileRemaining < miniMileRemaining:
			miniMileRemaining = mileRemaining
			minimumCityIndex = index
	
    return minimumCityIndex
```