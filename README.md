# tempo_pypack

![PyPI](https://img.shields.io/pypi/v/tempo-pypack)
![GitHub](https://img.shields.io/github/license/bl1nk18two/tempo_pypack)
![Python](https://img.shields.io/pypi/pyversions/tempo-pypack)

A Python library for obtaining runtime estimates for loop-based applications and creating countdown timers.

## Installation

```bash
pip install tempo-pypack
```

## Features

This package offers two main components:

1. **LoopTimer** - Calculates and displays estimated completion times for processing loops, including:
   - Current progress (with progress bar)
   - Elapsed time
   - Estimated time remaining
   - Expected completion time
   - Average processing speed

2. **timer** - A simple countdown function to display a timer in the terminal

## Usage Examples

### LoopTimer

```python
import time
from tempo_pypack import LoopTimer

# Initialize a LoopTimer with the total number of records
tempo = LoopTimer(records_total_number=10)

# Start the timer indicating the initial index
tempo.start(2)

# Simulate processing records
for i in range(10):
    if i < 2:
        continue
    time.sleep(1)
    # Update the timer with the current index
    tempo.update_loop(i + 1)
    # Display the current summary
    print(tempo)

# Finalize and display the final summary
print(tempo.stop())
```

Example output:
```
Progress: |█████████████████████████--------------------------| 52.0% Complete
Elapsed time (session): 00:00:26 
Remaining time: 00:00:24 
Expected end time: 11:45:50 
Average speed (records/s): 1.92 records per second
```

### timer Function

```python
from tempo_pypack import timer

# Basic 5-second countdown
timer(5, prefix='Remaining', suffix='seconds', separator=' ', close=False, text='Timer finished!')
```

Example output:
```
Remaining 5 seconds
Remaining 4 seconds
Remaining 3 seconds
Remaining 2 seconds
Remaining 1 seconds
Remaining 0 seconds
Timer finished!
```

## API Details

### LoopTimer

#### Main Methods

- **`__init__(records_total_number=None)`** - Initializes the timer with the total number of records
- **`start(init_index=0)`** - Starts the timer from a specific index
- **`update_loop(processed_records)`** - Updates the counter of processed records
- **`stop(return_summary=True)`** - Finalizes the timer and returns an execution summary

#### Display Methods

- **`progress()`** - Returns the current progress, with progress bar option
- **`session_time()`** - Returns the elapsed time since start
- **`time_left()`** - Returns the estimated time remaining
- **`expected_end()`** - Returns the expected completion time
- **`average_speed_session()`** - Returns the average processing speed
- **`summary()`** - Returns a complete summary of current progress

### timer Function

**`timer(number, prefix='', suffix='', separator='', close=False, text=None)`**

Parameters:
- **number** (int): Initial number for the countdown
- **prefix** (str): Text to display before the countdown number
- **suffix** (str): Text to display after the countdown number
- **separator** (str): Separator between prefix, number, and suffix
- **close** (bool): If True, exits the program after the countdown
- **text** (str): Message to display after countdown completion

## Requirements

- Python 3.6+

## Links

- [GitHub](https://github.com/bl1nk18two/tempo_pypack)
- [PyPI](https://pypi.org/project/tempo-pypack/)

## License

This project is licensed under the terms of the MIT license.
