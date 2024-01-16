# Niaz
# Staff attendance project
class Staff:
    def __init__(s, name, staff_id):
        s.name = name
        s.staff_id = staff_id
        s.attendance = [None] * 31  # Assuming a month has a maximum of 31 days

    def mark_attendance(s, day, present=True):
        if 1 <= day <= 31:
            s.attendance[day - 1] = present
        else:
            print(" 1 and 31.")

    def display_staff_info(s):
        print(f"Name: {s.name}")
        print(f"Staff ID: {s.staff_id}")
        print("Monthly Attendance:")
        for day, present in enumerate(s.attendance, start=1):
            status = "Present" if present else "Absent" if present is False else "Not marked"
            print(f"Day {day}: {status}")


def create_staff():
    name = input("Enter staff name: ")
    staff_id = input("Enter staff ID: ")
    return Staff(name, staff_id)


def mark_staff_attendance(staff):
    day = int(input("Enter day (1-31): "))
    present = input("Is the staff present? (yes/no): ").lower() == 'yes'
    staff.mark_attendance(day, present)
    print("Attendance marked successfully!")


def display_all_staff(staff_dict):
    if not staff_dict:
        print("No staff information available.")
    else:
        for staff_id, staff in staff_dict.items():
            staff.display_staff_info()


def main():
    staff_dict = {}

    while True:
        print("\n1. Add Staff\n2. Mark Attendance\n3. Display Staff Information")
        choice = input("Enter your choice (1-2-3): ")

        if choice == '1':
            staff = create_staff()
            staff_dict[staff.staff_id] = staff
            print("Staff added successfully!")

        elif choice == '2':
            if not staff_dict:
                print("No staff available. Please add staff first.")
            else:
                staff_id = input("Enter staff ID: ")
                staff = staff_dict.get(staff_id)
                if staff:
                    mark_staff_attendance(staff)
                else:
                    print("Staff not found.")

        elif choice == '3':
            display_all_staff(staff_dict)
        else:
            print("Invalid choice. Please enter 1, 2, 3.")
if __name__ == "__main__":
    main()
