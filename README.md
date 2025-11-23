The Challenge
Most people don't know the exact carbon footprint of their daily travel. We use cars, buses, and trains without realizing how much CO2 is being released, which harms the environment.

Our Goal
We need a simple tool to make this impact visible.

What This Tool Does (The Solution)
The GREEN-MILES tracker solves this by:

Calculating the CO2 (carbon dioxide) produced by different travel methods (car, train, bike, etc.).
Showing you a clear, simple summary of your total environmental impact each day.
Encouraging you to choose zero-emission travel (like walking or biking) to become an "Eco-Friendly Hero."# 🌿 GREEN-MILES: 
Transport TrackerThis is a small Python program to help you track your daily travel and see how much carbon dioxide CO2 you're producing. The goal is to make you more aware of your impact and help you choose more sustainable ways to travel!

# How to Run the Program
You need Python installed on your computer.
Save the file: Save the code above as a file named code.py.
Open your terminal/command prompt.
Run the script: Type the following command and press Enter:
python code.py
Follow the steps: The program will ask you for your mode of transport and the distance traveled.
# vechile-polution
#project based on :transportion and sustinability.
import datetime  # Helps us add the current date to our log file

# This is a small helper function to get a valid mode from the user.
# It keeps asking until they enter something correct.
    
# How It Works 
1. Start Tracking: The program asks you to enter a Mode of Transport (like Car, Bus, Train, Bike, or Walk).
2. Enter Distance: You then enter the distance you traveled in kilometers (km).
3. Calculation: It uses a simple formula to figure out your emissions for that trip:
    {Emissions} = {Distance (km)} * {Emission Rate (kg }
4. Add More Trips: You can add as many trips as you want (e.g., "Walk 2km," then "Bus 10km").
5. See Summary: When you say "no" to adding more trips, it shows your Total Distance and Total Emissions.
6. Saves Everything: It saves your full trip history and summary into a file called travel_log.txt.

# Emission Rates Used
The program uses these values to calculate your carbon impact (in kg CO2 per km) : 
Mode of Transport,CO2​ Rate (kg/km)
Car,0.19
Bus,0.03
Train,0.04
Bike,0.00
Walk,0.00
