import pandas as pd
import us
import pycountry
file_data = pd.read_csv("Data_earthquakes_2014.csv")

eqDF = pd.DataFrame(file_data)
print(eqDF)

#Print the columns
print(file_data[['time','place','type']])
print("-----------------------------------------------------------------------")
#Removing time column which includes date and time and adding two new columns date & time
date = []
time = []
for x in eqDF.time:
    d = x.split(" ")
    date.append(d[0])
    time.append(d[1])
del eqDF['time']
eqDF['date']=pd.Series(date)
eqDF['time']=pd.Series(time)
print(eqDF)
print("-----------------------------------------------------------------------")
#Setting the id colum as the index of the dataframe
eqDF = eqDF.set_index('id')
print("Information about DataFrame")
print(eqDF.info())
print("-----------------------------------------------------------------------")
#Basic Statistics of all columns
print("Discription about DataFrame ")
print(eqDF.describe())
print("-----------------------------------------------------------------------")
#Highest and Lowest Magnitude of earthquake
maxMagnitude = eqDF.mag.max()
minMagnitude = eqDF.mag.min()
print("Lowest Magnitude : ",minMagnitude)
print("Highest Magnitude : ",maxMagnitude)
print("-----------------------------------------------------------------------")
#Top 20 earthquake by Magnitude
sorteqDF = eqDF.sort_values(by=['mag'],ascending=False)
eqDFTop20 = sorteqDF.head(20)
print("Top 20 Earthquake by Magnitude ")
print(eqDFTop20.mag)
print("-----------------------------------------------------------------------")
#Seperating country from places and adding new colum country
country = []
placeLocation = []
us_states=[str(x) for x in us.STATES]
for x in eqDF.place:
        if x.find(",") != -1:
            token = x.split(",")
            if token[1].lstrip() in us_states:
                country.append("USA")
                placeLocation.append(token[0])
            else:
                country.append(token[1])
                placeLocation.append(token[0])
        else:
            country.append("NA")
            placeLocation.append(token)


del eqDF['place']
eqDF['Location']=placeLocation
eqDF['country']=country
print("Place column seperated into country and location ")
print(eqDF)
print("-----------------------------------------------------------------------")
