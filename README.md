# doortuning-example
A sample resource for doortuning within FiveM

## Explanation

### gta5.meta
This file defines where certain necessary singleton files are located. It is necessary for this to be replaced to define where the doortuning file should be retrieved from.

#### What needs to change?
In `gta5.meta` search for "DOOR_TUNING_FILE"; it should be close to the end of the file. The only thing that you should need to edit is changing `doortuning-example` to whatever you name your doortuning resource.

### doortuning.ymt
This file defines door behaviors and links specific door models to the desired door behavior. 

NOTE: Do not try to export / import the doortuning.ymt with codewalker. Just leave it in an XML format under the .ymt extension and everything will work as it should.

#### NamedTuningArray
This section is where door behaviors are defined. These definitions can be used across multiple doors without needing to redefine the same parameters.

- \<Item\>
  - \<Name\>
    - The name that will be used to reference the following set of parameters for a door
  - \<Tuning\>
    - \<AutoOpenVolumeOffset x="0" y="0" z="0"\>
      - Offset from the center of the door that the auto open volume should be placed to start looking for a reason to auto-open
    - \<Flags\>
      - Optional flags that you want to apply to the door that can specificy specific behaviors
      - Potential Flags
        - AutoOpensForAllVehicles
        - AutoOpensForLawEnforcement
        - AutoOpensForMPPlayerPedsOnly
        - AutoOpensForMPVehicleWithPedsOnly
        - AutoOpensForSPPlayerPedsOnly
        - AutoOpensForSPVehicleWithPedsOnly
        - DelayDoorClosingForPlayer
        - DontCloseWhenTouched
        - IgnoreOpenDoorTaskEdgeLerp
    - \<AutoOpenRadiusModifier value="0"\>
      - How much to multiply the radius for the auto open volume to check for reasons to auto-open
    - \<AutoOpenRate value="1.0"\>
      - How fast the door will auto-open once a check condition succeeds
    - \<AutoOpenCosineAngleBetweenThreshold value="-1"\>
      - Unknown
    - \<AutoOpenCloseRateTaper value="true"\>
      - Unknown
    - \<UseAutoOpenTriggerBox value="true"\>
      - Whether or not to utilize auto-open feature
    - \<CustomTriggerBox value="true"\>
      - Whether or not to use a custom sized auto-open trigger box defined by \<TriggerBoxMinMax\>
    - \<TriggerBoxMinMax\>
      - \<min x="-1.0" y= "-1.0" z="-1.0"\>
      - \<max x="1.0" y="1.0" z="1.0"\>
    - \<BreakableByVehicle value="true"\>
      - Whether or not a vehicle could break the door and therefore the auto-open function
    - \<BreakingImpulse value="0"\>
      - Magnitude of a physics impulse to set off when the door is broken
    - \<ShouldLatchShut value="true"\>
      - Whether or not a swinging door immediate "latches" shut when it returns to it's original resting position
    - \<MassMultiplier value="0.01"\>
      - How much to multiply the base door's mass by
    - \<WeaponImpulseModifier value="1"\>
      - How much to multiply the physics impulse that the door receives from weapons
    - \<RotationLimitAngle value="0"\>
      - What angle from original resting position a door should be able to rotate
    - \<TorqueAngularVelocityLimit value="5"\>
      - Max angular velocity a door is allowed to travel at (?)
    - \<StdDoorRotDir\>
      - Potential Flags
        - StdDoorOpenBothDir
        - StdDoorOpenNegDir
        - StdDoorOpenPosDir (?)

#### ModelToTuneMapping
This section is where specific door models are linked with a defined Named Tuning (defined above)

- \<Item\>
  - \<ModelName\>
    - Name of a given door model
  - \<TuningName\>
    - The \<Name\> of a NamedTuning that you want the specified door model to inherits its behavior from

###
