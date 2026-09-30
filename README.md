# PID-temperature-controller
# PID Temperature Controller

Kp = 2.0
Ki = 0.5
Kd = 0.1

set_temperature = 100.0
actual_temperature = 70.0

integral = 0
previous_error = 0

print("PID TEMPERATURE CONTROLLER")
print("--------------------------")

for i in range(1, 21):

    # Calculate error
    error = set_temperature - actual_temperature

    # PID terms
    integral = integral + error
    derivative = error - previous_error

    # PID control signal
    control = (Kp * error) + (Ki * integral) + (Kd * derivative)

    # Limit control signal
    if control > 100:
        control = 100
    elif control < 0:
        control = 0

    # Simulate temperature response
    actual_temperature = actual_temperature + control * 0.05

    previous_error = error

    print(f"Step {i}")
    print(f"Set Temperature    : {set_temperature:.2f} °C")
    print(f"Actual Temperature : {actual_temperature:.2f} °C")
    print(f"Heater Output      : {control:.2f}%")
    print("--------------------------")
