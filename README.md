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
def get_transport_mode(emission_rates):
    print("\nAvailable Modes: Car, Bus, Train, Bike, Walk")
    while True:  # Loop until we get a good answer
        mode = input("Enter Mode of Transport: ").strip().capitalize()
        if mode in emission_rates:  # Check if it's a valid key in our dictionary
            return mode  # All good! Send it back to the main function
        print("-> Error: Invalid Mode. Please choose from the list.")

def get_distance(mode):
    while True:  # Loop until we get a good answer
        try:
            distance = float(input(f"Distance travelled by {mode} (km): ").strip())
            if distance > 0:  # Make sure it's positive (you can't travel negative km!)
                return distance
            else:
                print("-> Error: Distance must be greater than 0.")
        except ValueError:
            print("-> Error: Please enter a numeric distance.")

# Formula: emissions = distance * rate (from the dictionary)
def calculate_emissions(distance, mode, emission_rates):
    rate = emission_rates[mode]  # Get the emission rate for this mode
    emissions = distance * rate  # Simple math!
    return emissions

# This saves everything to a file so we don't lose our history.
def save_to_file(trip_log, total_co2, feedback):
    with open("travel_log.txt", "a") as file:  # "a" means append (add to end, don't overwrite)
        file.write(f"\nDate: {datetime.datetime.now()}\n")  # Add today's date
        for trip in trip_log:  # Loop through each trip and write it
            file.write(trip + "\n")
        file.write(f"TOTAL: {total_co2:.2f} kg CO2 | {feedback}\n")  # Write summary
        file.write("-" * 30 + "\n")  # Add a line separator
    print("\n-> Success: Travel history saved to 'travel_log.txt'")

# This is the main function that runs the whole program.
def main_system():
    print("==========================================")
    print(" GREEN-MILES: TRANSPORT TRACKER ")
    print("==========================================")
    print("Track your travel and check your carbon impact.\n")
    
    # Dictionary: Holds emission rates (kg CO2 per km) for each mode.
    # Keys are modes, values are rates. Easy to update!
    emission_rates = {
        "Car": 0.19,   # High emission
        "Bus": 0.03,   # Low emission (shared ride)
        "Bike": 0.00,  # Zero emission
        "Train": 0.04, # Low emission
        "Walk": 0.00   # Zero emission
    }
    
    # Start with empty totals and an empty list for trips.
    total_km = 0.0
    total_co2 = 0.0
    trip_log = []  # FIXED BUG: This is now an empty list to hold our trip details
    
    # 1. LOOP: Keep adding trips until the user says no.
    while True:
        mode = get_transport_mode(emission_rates)  # Get a valid mode
        distance = get_distance(mode)  # Get a valid distance
        
        # Calculate emissions for this trip
        emissions = calculate_emissions(distance, mode, emission_rates)
        
        # Add to our running totals (math: just add up!)
        total_km += distance
        total_co2 += emissions
        
        # Save trip details as a string in our list
        trip_detail = f"{mode}: {distance}km | Emissions: {emissions:.2f} kg CO2"
        trip_log.append(trip_detail)  # Now this works because trip_log is a list!
        
        print(f"-> Trip Added. Impact: {emissions:.2f} kg CO2")
        
        # Ask if they want to add more (simple check)
        more = input("Add another trip? (yes/no): ").strip().lower()
        if more.startswith('n'):  # If it starts with 'n' (like "no" or "nah")
            break  # Exit the loop
    
    # 2. ANALYSIS: Show summary and give feedback.
    print("\n==========================================")
    print(" DAILY SUMMARY ")
    print("==========================================")
    print(f"Total Distance: {total_km} km")
    print(f"Total Emissions: {total_co2:.2f} kg CO2")
    
    # Decision making: Use if/elif/else to give feedback based on totals
    if total_co2 > 5.0:
        feedback = "Status: HIGH CARBON IMPACT. Try taking a bus next time!"
    elif total_co2 > 0.0:
        feedback = "Status: MODERATE IMPACT. Good job."
    else:
        feedback = "Status: ECO-FRIENDLY HERO! Zero emissions."
    
    print(feedback)
    
    # 3. FILE I/O: Save the log to a file
    save_to_file(trip_log, total_co2, feedback)

# Run the program if this file is started directly
if __name__ == "__main__":

    main_system()
<img width="871" height="568" alt="Screenshot 2025-11-22 215457" src="https://github.com/user-attachments/assets/b19204e1-a444-4cf8-af2e-8c5fae7604b6" />

    
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
