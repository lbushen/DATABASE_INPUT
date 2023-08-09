#####ask user for input into database####

#!/usr/bin/python

import mariadb
import sys

# connect to the database
try:
		conn = mariadb.connect(
			user="lee",
			password="mypassword",
			database="MY_KIDS")

except mariadb.Error as e:
		print(f"Error connecting to MariaDB Platform: {e}")
		sys.exit(1)

#get cursor
cur = conn.cursor()

try:
		cur.execute("use MY_KIDS;")

except mariadb.Error as e:
		print(f"Error: {e}")

x = 0
# ask for user input
while x == 0:

	name = input("Add name: ")

	while True:
		try:
			gender = input("Please enter gender: ")
			if gender == "male" or gender == "female":
				break;
			else:
				print("Please enter either 'male' or 'female'")
		except:
			continue;

	while True:
		try:
			age = int(input("Add age: "))
		except ValueError:
			print("Sorry, I didn't understand that.")
			continue;
		else:
			break;
			
	# add user input to database table
	add_data = f"INSERT INTO Kids  (name, gender, age) VALUES ('{name}', '{gender}', '{age}')"

	cur.execute(add_data)	

##### ask user if there more entries.  If yes, rerun script, if no, close
	while True:
		try:
			ask = input("If more entries press (Y), if not press (N): ")
			if ask == "Y" or ask == "y":
				break;
			if ask == "N" or ask == "n":
				x = 1
				break;
			else:
				print("Invalid entry. Press (Y) for yes or press (N) for no: ")
			
		except:
			continue;


conn.commit()
cur.close()
conn.close()
