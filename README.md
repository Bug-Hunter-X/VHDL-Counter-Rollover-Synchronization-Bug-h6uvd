# VHDL Counter Rollover Synchronization Bug

This repository demonstrates a common but subtle bug in VHDL counter designs related to rollover and clock synchronization.  The `buggy_counter.vhd` file contains a counter that might produce incorrect results due to a lack of careful handling of the rollover condition.

The `fixed_counter.vhd` file provides a corrected version of the counter, addressing the potential synchronization issues.

## Bug Description

The original counter's rollover condition (when `internal_count` reaches 15) is not precisely synchronized with the clock's rising edge. This can lead to glitches or metastable states that result in the counter showing incorrect values under certain clock speeds or operating conditions.

## Solution

The fix involves ensuring that the rollover action is atomic; the counter's reset value should be assigned in the same clock edge when the maximum count is reached.