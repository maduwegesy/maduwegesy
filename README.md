def days_to_birthday(date):
    '''
    Calculates the number of days that have passed since the 1st of January 
    to the given date.

    :param date: A date string in the format of yyyy-mm-dd
    :return: The number of days to the date from 1st of January 
             (eg: date->2021-01-01, return->1)
    '''

    # Convert the date string to a datetime object
    datetime_object = datetime.strptime(date, "%Y-%m-%d")

    # Extract only the date and remove the timestamp
    date = datetime_object.date()

    # Find the number of days since the begining of the year
    num_days = date.timetuple().tm_yday

    return num_days
file_name=input()
with open(file_name,"r") as x:
    information=x.readlines()
with open(file_name,"r") as out_file: 
    for line in information:
     information=out_file.split(" ")
     name =str(information[0])
     dob =str(information[1])
     gender =str(information[2])
     num_days = days_to_birthday(dob)
     y,m,d=map(str,dob.split("-"))
    
     if gender == "F":
         new_num_days=str(num_days)+500
     else:
        new_num_days = str(num_days)

def last_three_digits(year, counter={}):
    # Check if the birth year is already in the dictionary
    if year in counter:
        counter[year] += 1
    else:
        counter[year] = 1
    
    # Assign the next three digits based on the submission count
    assigned_digits = str(counter[year]).zfill(3)

    return assigned_digits
assigned_digits=last_three_digits(y)

x.close
out_file.close

print(name," ",y+new_num_days+assigned_digits)
