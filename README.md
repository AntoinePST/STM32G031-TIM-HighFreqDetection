# STM32G031-TIM-HighFreqDetection
Example demonstrates how to measure high frequency signal with timer input on a STM32GO31 microcontroller.

By using TIM1 and TIM17, this project is able to detect a signal up to 150MHz, with 1MHz uncertainty.

- TIM1 is configured in gated mode, with ETR2 (=signal to be detected) as clock source, and ITR3 (=TIM17 output) as trigger source.
- TIM17 is configured in OC mode.
TIM1 is used as the counter, and TIM17 as the measurement window. With this configuration, TIM1 counts as long as TIM17 output is high.

On a software point of view, the current solution is to read TIM1 counter at each TIM17 interrupts, which occurs on both rising and falling edges of TIM17 output.
