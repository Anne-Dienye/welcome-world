# welcome-worldimport math
import statistics

# Constants
NUM_MARKS = 5  # Number of marks (can be changed easily)
MIN_MARK = 0   # Minimum valid mark
MAX_MARK = 100 # Maximum valid mark

def get_marks():
    marks = []
    print(f"Enter up to {NUM_MARKS} marks (0-100). Press Enter to finish early.")
    
    while len(marks) < NUM_MARKS:
        mark_input = input(f"Enter mark {len(marks) + 1}: ").strip()
        if mark_input == "":
            break  # Terminate if the user presses Enter
        try:
            mark = float(mark_input)
            if MIN_MARK <= mark <= MAX_MARK:
                marks.append(mark)
            else:
                print(f"Mark must be between {MIN_MARK} and {MAX_MARK}. Try again.")
        except ValueError:
            print("Invalid input. Please enter a number.")
    
    return marks

def calculate_statistics(marks):
    if not marks:
        return None
    
    # Basic statistics
    highest = max(marks)
    lowest = min(marks)
    mean = statistics.mean(marks)
    
    # Bonus: Median and standard deviation
    median = statistics.median(marks)
    stdev = statistics.stdev(marks) if len(marks) > 1 else 0
    
    return {
        "highest": highest,
        "lowest": lowest,
        "mean": mean,
        "median": median,
        "stdev": stdev
    }

def main():
    marks = get_marks()
    if not marks:
        print("No marks entered. Exiting.")
        return
    
    stats = calculate_statistics(marks)
    
    print("\nResults:")
    print(f"Highest mark: {stats['highest']}")
    print(f"Lowest mark: {stats['lowest']}")
    print(f"Mean mark: {stats['mean']:.2f}")
    print(f"Median mark: {stats['median']}")
    print(f"Standard deviation: {stats['stdev']:.2f}")

if __name__ == "__main__":
    main()
