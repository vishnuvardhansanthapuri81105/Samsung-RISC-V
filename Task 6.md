LED FADING PROGRAM FOR VSDSQUADRON MINI(RISC-V)

Description

This is a simple LED fading program for the CH32V00x microcontroller, written in C. The program initializes an LED connected to GPIOD and creates a fading effect using a software-based PWM approach.

CODE:

#include <ch32v00x.h>
#include <debug.h>

#define LED_PORT GPIOD
#define LED_PIN GPIO_Pin_6
#define LED_CLOCK_ENABLE RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE)

void setup() {
    SystemCoreClockUpdate();
    LED_CLOCK_ENABLE;

    GPIO_InitTypeDef GPIO_InitStructure = {0};
    GPIO_InitStructure.GPIO_Pin = LED_PIN;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(LED_PORT, &GPIO_InitStructure);
}

void loop() {
    // Fade in
    for (uint8_t i = 0; i < 255; i++) {
        GPIO_WriteBit(LED_PORT, LED_PIN, Bit_SET);
        delay(i);  // Increasing delay simulates PWM-like fade
        GPIO_WriteBit(LED_PORT, LED_PIN, Bit_RESET);
        delay(255 - i);
    }

    // Fade out
    for (uint8_t i = 255; i > 0; i--) {
        GPIO_WriteBit(LED_PORT, LED_PIN, Bit_SET);
        delay(i);
        GPIO_WriteBit(LED_PORT, LED_PIN, Bit_RESET);
        delay(255 - i);
    }
}

here's the video:


https://github.com/user-attachments/assets/4915866f-9100-4930-821a-8492cf17c1dc



Acknowledgment:
We would like to express our sincere gratitude to the VSD and RISC-V team for visiting our institution, organizing an amazing roadshow, and providing us with this internship opportunity. Their support and generosity in giving us RISC-V development boards have enabled us to learn and implement real-time projects.

Thank you,
Sairam..

