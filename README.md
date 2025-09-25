<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name :PRIYADHARSHINI R </h3>
<h3>Register Number1 :212224210017</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>
```
import random
import time

class MedicinePrescribingAgent:
    def _init_(self):
        self.performance = 0
        self.current_room = "Room1"
        # Randomly decide patient room and temperature
        self.patient_room = random.choice(["Room1", "Room2"])
        self.patient_temp = round(random.uniform(97.0, 102.0), 1)  # temperature in °F

    def sense_temperature(self):
        """Sense temperature only if patient is in the same room."""
        if self.current_room == self.patient_room:
            return self.patient_temp
        else:
            return None   # No patient in this room

    def prescribe_medicine(self):
        print(f"Patient found in {self.current_room} with temperature {self.patient_temp}°F.")
        if self.patient_temp > 98.5:
            print("⚕  Patient has fever. Prescribing medicine...")
            self.performance += 1
        else:
            print("✅ Patient is healthy. No medicine required.")
        print()

    def move_to_other_room(self):
        self.current_room = "Room2" if self.current_room == "Room1" else "Room1"
        self.performance -= 0.5
        print(f"Agent moved to {self.current_room}. (Performance -0.5)\n")

    def run(self):
        print("---- Medicine Prescribing Agent Started ----\n")
        # The agent will keep checking both rooms twice for demo
        for i in range(4):  # check 4 times (2 full cycles)
            print(f"Checking {self.current_room}...")
            temp = self.sense_temperature()
            if temp is not None:
                self.prescribe_medicine()
            else:
                print("No patient in this room.\n")

            # Move to the other room for next check
            self.move_to_other_room()
            time.sleep(1)

        print(f"Final Performance Score: {self.performance}")
if _name_ == "_main_":
    agent = MedicinePrescribingAgent()
    agent.run()
    ```
    # OUTPUT 
    <img width="655" height="490" alt="Screenshot 2025-09-25 234347" src="https://github.com/user-attachments/assets/f4a6ad79-96fe-4509-a246-0421782c7039" />
    <img width="601" height="218" alt="Screenshot 2025-09-25 234359" src="https://github.com/user-attachments/assets/b2b0167e-95ff-4048-b5d8-8148d5e9d7e2" />


