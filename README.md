# importing_data

import csv

maxTemp = 0 
minTemp = 0
averageMax = 0
averageMin = 0
totalData = 0
first = True

with open('Norman2016.csv', newline='') as csvfile:
    reader = csv.DictReader(csvfile)
    
    for row in reader:
        max = float(row['TMAX'])
        min = float(row['TMIN'])
        if max > 120 or min < -80:
            continue

        if first:
            maxTemp = max
            minTemp = min
            first = False

        if max > maxTemp:
            maxTemp = max
        if min < minTemp:
            minTemp = min

        averageMax += max
        averageMin += min
        totalData += 1

averageMax /= totalData
averageMin /= totalData

print(f"Highest temp: {round(maxTemp, 2)}")
print(f"Lowest temp: {round(minTemp, 2)}")
print(f"Avg highest temp: {round(averageMax, 2)}")
print(f"Lowest high temp: {round(averageMin, 2)}")
