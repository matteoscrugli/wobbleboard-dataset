# wobbleboard-dataset
Collection of sensory data while performing physical exercises over a wobble board.

At the core of the tracking functionality we use two wireless sensor nodes, which are small battery-powered microcontroller-based devices that gather data from sensors and connect via Bluetooth low-energy to transmit/receive data from the rest of the system. The first sensor node, called hereafter *board* sensor node, is embedded in a custom wobble board. The sensor in the board tracks its movements and provides data on the user's performance.
The second sensor node, called hereafter *body* sensor node, is designed to be worn on the user's forearm. It tracks the user's movements during exercises like squats and push-ups, providing data on the number of repetitions and the quality of the exercise.

Our dataset includes 108 recordings that are generally one minute long but can vary between 30 seconds and 90 seconds. The exercises in question will be described in Table below.
| AI class symbol | AI class name | Sensor mode | Description |
|------------|-------------|-------------|-------------|
| B | Basic stance balance | board | Upright torso, neutral spine, board balancing. |
| S | Side tilt | board | Weight shift, left-right tilt, controlled movement. |
| FB | Forward/Backward | board | Front-back tilt, slow and controlled. |
| R | Two leg tilts | board | 360-degree rotation, alternating directions. |
| SQ | Squats | body | Involves bending the knees, lowering the torso with a straight back, and pushing the hips back before returning to a standing position. |
| P | Push-ups | body | Executed in the prone position, facing down, and entails raising and lowering the body by extending and flexing the arms. |
| G | Other | board & body | Unmatched actions or lack of movement. |

The data collected from the sensors is stored in a JSON format, which offers an organized and easily understandable structure. Each recording is saved in a separate file, and although the current neural network model doesn't utilize gyroscope data, it has been included in the recordings as a precautionary measure for potential future use.

The table below explains the JSON structure in which there are several keys that provide relevant information about the data.

| Keys       | Description                                                                                                                                   |
|------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| class      | The type of activity performed during the recording.                                                                                           |
| samples    | The total number of data points collected.                                                                                                     |
| frequency  | The rate at which the data was sampled.                                                                                                        |
| datetime   | The date and time of the recording.                                                                                                            |
| note       | An optional field for adding any extra comments or details about the recording.                                                                |
| data       | The actual sensor data, containing two sub-objects for the accelerometer and gyroscope, each with x, y, and z lists for their respective axes. If only one sub-object is present, the data refer to the accelerometer sensor. |
| events | Sample in which the midpoint of the exercise execution is approximately indicated. |

Finally, what the JSON structure looks like:

```json
{
	"class": "<class 'str'>",
	"samples": "<class 'int'>",
	"frequency": "<class 'int'>",
	"datetime": "<class 'str'>",
	"note": "<class 'str'>",
	"data": [
		{
			"x": "<class 'list'>",
			"y": "<class 'list'>",
			"z": "<class 'list'>"
		},
		{
			"x": "<class 'list'>",
			"y": "<class 'list'>",
			"z": "<class 'list'>"
		}
	]
}
```
