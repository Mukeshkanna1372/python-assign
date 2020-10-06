import os

import datetime

path= "/Users/adminn/Desktop/Mukeshkanna"

def get_files_with_extension():
    path = input("Enter your path: ")
    extension = input("Enter the file extension: ")
    for (root , directories , files) in os.walk(path):
        for file in files:
            if file.endswith(extension):
                print(os.path.join(root , file))

def get_files_created_september():
    start_date = today_date - datetime.timedelta(days=30)
    end_date = today_date
    get_files_between_range(start_date , end_date)

def get_files_between_range(start_date , end_date):
    path = input("Enter your path: ")
    for (root , directories , files) in os.walk(path):
        for file in files:
            file_path = os.path.join(root , file)
            created_date = get_created_date(file_path)
            if created_date >= start_date and created_date <= end_date:
                print(file_path , created_date)
def get_created_date(file_path):
    created_time = os.path.getctime(file_path)
    created_date = datetime.date.fromtimestamp(created_time)
    return created_date

today_date = datetime.date.today()
while True:
    print("What would you like to search ?")
    print("files with extension \n created september \n exit")
    user_input = input("Enter your option \n >>>")
    if user_input == "files with extension":
        get_files_with_extension()
    elif user_input == "created september":
        get_files_created_september()
    elif user_input == "exit":
        break
    else:
        print("Invalid inpiut")
