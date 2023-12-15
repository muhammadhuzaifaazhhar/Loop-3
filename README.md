# Loop-3
def determine_bonus_rate(salary):
    if salary <= 50000:
        return 0.02
    elif 50000 < salary <= 100000:
        return 0.015
    else:
        return 0.01

def main():
    file_path = "employee_data.txt"  # Replace with the actual path to your text file

    try:
        with open(file_path, "r") as file:
            total_bonuses = 0.0

            print("\nEmployee | Salary | Bonus")
            print("---------------------------")

            for line in file:
                # Parse employee data from each line
                last_name, salary = line.strip().split(", ")
                salary = float(salary)

                # Determine the bonus rate and calculate bonus
                bonus_rate = determine_bonus_rate(salary)
                bonus = bonus_rate * salary

                # Display employee information and bonus
                print(f"{last_name:8} | ${salary:,.2f} | ${bonus:,.2f}")

                # Update the total bonuses
                total_bonuses += bonus

            # Display the sum of all bonuses
            print("\nTotal Bonuses Paid Out: ${:,.2f}".format(total_bonuses))

    except FileNotFoundError:
        print(f"Error: File '{file_path}' not found.")

if __name__ == "__main__":
    main()
