
project_title = input("COM103-MIDTERM-EXAM: ")
group_name = input("SQUAD ZERO: ")

# STEP 2: Task types (hardcoded)
tasks = [
    "Program Logic / Coding",
    "UI / Output Formatting",
    "Testing & Debugging",
    "Documentation / README",
    "Presentation Slides"
]

hours = [6, 3, 2, 2, 2]

print("\nTASK TYPES:")
for i in range(5):
    print(f"{i+1}. {tasks[i]} - {hours[i]}h")

# STEP 3 & 4: Assignments
assignments = []

for i in range(4):
    print(f"\nAssignment {i+1}")
    task_num = int(input("Task number (1-5, 0 to skip): "))

    if task_num == 0:
        continue

    if 1 <= task_num <= 5:
        member = input("Member name: ")
        status = input("Status (done/pending): ").lower()

        if status != "done":
            status = "pending"

        # STEP 5: Points
        points = 2 if status == "done" else 1

        assignments.append({
            "task": tasks[task_num - 1],
            "hours": hours[task_num - 1],
            "member": member,
            "status": status,
            "points": points
        })

# STEP 6: Computations
total_points = sum(a["points"] for a in assignments)
max_points = len(assignments) * 2
progress = int((total_points / max_points) * 100) if max_points > 0 else 0

# STEP 7: Status label
if progress >= 75:
    project_status = "PROJECT READY!"
elif progress >= 50:
    project_status = "ON TRACK."
else:
    project_status = "NEEDS MORE WORK!"

# STEP 8: Output board
print("\n" + "=" * 60)
print(f"PROJECT TITLE: {project_title}")
print(f"GROUP NAME   : {group_name}")
print("=" * 60)
print(f"{'No.':<4}{'Task':<30}{'Hrs':<5}{'Member':<15}{'Status':<10}{'Pts':<5}")
print("-" * 60)

for i, a in enumerate(assignments, 1):
    print(f"{i:<4}{a['task']:<30}{a['hours']:<5}{a['member']:<15}{a['status']:<10}{a['points']:<5}")

print("-" * 60)
print(f"Total Points : {total_points}")
print(f"Progress     : {progress}%")
print(f"Status       : {project_status}")
print("=" * 60)
