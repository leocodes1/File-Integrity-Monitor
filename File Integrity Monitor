import os
import hashlib
import json
import time

def calculate_file_hash(file_path):
    #Calculates the hash of files
    sha256_hash = hashlib.sha256()
    with open(file_path, "rb") as f:
             while True:
                data = f.read(4096)
                if not data:
                    break
                sha256_hash.update(data)
    #Provies readable hash
    return sha256_hash.hexdigest()


def create_baseline(directory):
    
    baseline_of_files = {}
    
    for root, dirs, file_names in os.walk(directory):
        for file_name in file_names:
            file_path = os.path.join(root, file_name)
            calculated_hash = calculate_file_hash(file_path)
            if calculated_hash:
                baseline_of_files[file_path] = calculated_hash
    
    with open("baseline.json", "w") as f:
        json.dump(baseline_of_files, f)
    print("\nBaseline created.")

def monitor_files(directory):
    try:
        with open("baseline.json", "r") as f:
            baseline = json.load(f)
    except FileNotFoundError:
        print("Baseline not found. Please create a baseline.")
        return

    print("Currently Monitoring.")
    for root, dirs, files in os.walk(directory):
        for file in files:
            file_path = os.path.join(root, file)
            current_hash = calculate_file_hash(file_path)
            
            if file_path not in baseline:
                print(f"New file detected: {file_path}")
            elif baseline[file_path] != current_hash:
                print(f"File modified: {file_path}")
    
    for file_path in baseline:
        if not os.path.exists(file_path):
            print(f"File deleted: {file_path}")

if __name__ == "__main__":
    print(" FILE INTEGRITY MONITER")
    directory_chosen = input("Please enter the directory you would like to use: ")
    print("Directory: " + directory_chosen)

    while True:
        print("\nOptions:")
        print("1. Create a baseline")
        print("2. Monitor for changes")
        print("3. Exit")
        choice = input("Please enter 1, 2, or 3): ")

        if choice == '1':
            create_baseline(directory_chosen)
        elif choice == '2':
            while True:
                monitor_files(directory_chosen)
                time.sleep(5)  
        elif choice == '3':
            print("Exiting program.")
            break
        else:
            print("Invalid choice. Please select 1, 2, or 3.")
