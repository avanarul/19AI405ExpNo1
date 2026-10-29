# Experiment No. 1: Developing AI Agent with PEAS Description

## AIM
To find the PEAS description for the given AI problem and develop an AI agent using Python.

## THEORY
### Medicine Prescribing Agent

A medicine prescribing agent identifies unhealthy patients based on their body temperature. In this experiment, a temperature greater than 98.5°F is considered unhealthy. The environment consists of two hospital rooms, and the agent moves between the rooms to check and treat patients.

The agent's performance increases when it treats an unhealthy patient and decreases when it moves between rooms. The agent uses the patient's temperature and room location to determine its actions.

## PEAS Description

- **P – Performance Measure:** Increase the score for treating patients and decrease the score for movement between rooms.
- **E – Environment:** Two hospital rooms, Room A and Room B, containing patients.
- **A – Actuators:** Move left, move right, and prescribe medicine.
- **S – Sensors:** Patient temperature input and current room location.

## DESIGN STEPS

1. **Identifying the Input:** Temperature of patients and room location.
2. **Identifying the Output:** Prescribe medicine if a patient has a fever.
3. **Developing the PEAS Description:** Define the performance measure, environment, actuators, and sensors.
4. **Implementing the AI Agent:** Check patients in both rooms and treat unhealthy patients.
5. **Measuring Performance:** Increase performance for each treatment and decrease performance for each movement.

## PROGRAM

```python
class MedicineAgent:
    def __init__(self):
        self.location = "Room A"
        self.performance = 0

    def act(self, environment):
        temp = environment[self.location]["temperature"]

        if temp > 98.5:
            print(f"Patient in {self.location} has fever ({temp}°F). Giving medicine.")
            self.performance += 10
            environment[self.location]["temperature"] = 98.0
        else:
            print(f"Patient in {self.location} is healthy ({temp}°F).")

        if self.location == "Room A":
            self.location = "Room B"
        else:
            self.location = "Room A"

        self.performance -= 1

    def print_status(self):
        print("Current Location:", self.location)
        print("Performance:", self.performance)


environment = {
    "Room A": {"temperature": 101.0},
    "Room B": {"temperature": 98.0}
}

agent = MedicineAgent()

for _ in range(4):
    agent.act(environment)
    agent.print_status()
```

## OUTPUT

~~~
<img width="632" height="535" alt="Screenshot 2026-10-29 102108" src="https://github.com/user-attachments/assets/9f124584-d929-4586-9724-5d8b6d9f2d26" />

~~~

## RESULT

Thus, the AI agent was developed using the PEAS description and implemented successfully using Python.
