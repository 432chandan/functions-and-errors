# functions-and-errors
# SpeedDetection Smart Contract

## Overview

The `SpeedDetection` smart contract is designed to assess fines and determine whether to seize a bike based on the speed of a vehicle. This contract allows an organizer to permit drivers and monitor overspeeding incidents.

## Features

- **Driver Management**: Organizer can allow drivers.
- **Speed Assessment**: Assess fines based on speed.
- **Bike Seizure Decision**: Determine if a bike should be seized based on speed.

## Smart Contract Details

### State Variables

- **`organizer`**: The address of the contract organizer.
- **`isDriverAllowed`**: A mapping to check if a driver is allowed.

### Events

- **`DriverAllowed(address indexed driver)`**: Emitted when a driver is allowed.
- **`OverspeedDetected(address indexed driver)`**: Emitted when overspeeding is detected.

### Constructor

- **`constructor()`**: Sets the contract deployer as the organizer.

### Functions

- **`assessFine(uint256 speed) external pure returns (uint256 fine)`**:
  - Uses `assert()` to ensure the speed is between 10 and 140 km/h.
  - Uses `require()` to apply a fine if the speed is between 50 and 110 km/h.
  - Returns a fine of 200 if the speed is within the applicable range.

- **`shouldSeizeBike(uint256 speed) external pure returns (bool seizeBike)`**:
  - Uses `revert()` to handle cases where the speed exceeds 110 km/h.
  - Returns `false` if the speed is within the allowable range.
