FULL ADDER IMPLEMENTATION USING VSDSQUADRON MINI:

![image](https://github.com/user-attachments/assets/3cedab0a-9a26-4fbc-97aa-f8d762bf0aea)



Overview
This project demonstrates the implementation of a Full Adder using the VSDSquadron Mini, a RISC-V based SoC development kit. The Full Adder is an essential combinational circuit used in digital electronics for performing binary addition. This project utilizes **GPIO pins** to read inputs and display outputs using **LEDs**.

---

 Components Required
- VSDSquadron Mini (RISC-V SoC development kit)
- Push Buttons (for binary input)
- 2 LEDs (for output display)
- Breadboard
- Jumper Wires
- VS Code (for software development)
- PlatformIO IDE (for compiling and debugging)

---

 Truth Table for Full Adder

| A | B | Cin | Sum | Carry |
|---|---|----|-----|-------|
| 0 | 0 |  0 |  0  |   0   |
| 0 | 0 |  1 |  1  |   0   |
| 0 | 1 |  0 |  1  |   0   |
| 0 | 1 |  1 |  0  |   1   |
| 1 | 0 |  0 |  1  |   0   |
| 1 | 0 |  1 |  0  |   1   |
| 1 | 1 |  0 |  0  |   1   |
| 1 | 1 |  1 |  1  |   1   |



Hardware Connections
- Input: The three binary inputs (A, B, Cin) are connected to the GPIO pins of VSDSquadron Mini via push buttons.
- Output:Two LEDs are connected to GPIO output pins to display Sum and Carry.
- GPIO Configuration: The GPIO pins are set up according to the Reference Manual to ensure the correct flow of signals.



Code Implementation

```c
// Full Adder Implementation using VSDSquadron Mini

#include <stdio.h>
#include <ch32v00x.h>


int AND_Gate(int x, int y) {
    return x & y;
}

int OR_Gate(int x, int y) {
    return x | y;
}

int XOR_Gate(int x, int y) {
    return x ^ y;
}


void Configure_GPIO() {
    GPIO_InitTypeDef GPIO_Setup = {0};
    
  
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOD, ENABLE);
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC, ENABLE);
    
  
    GPIO_Setup.GPIO_Pin = GPIO_Pin_1 | GPIO_Pin_2 | GPIO_Pin_3;
    GPIO_Setup.GPIO_Mode = GPIO_Mode_IPU; // Input Pull-Up
    GPIO_Init(GPIOD, &GPIO_Setup);
    
    GPIO_Setup.GPIO_Pin = GPIO_Pin_4 | GPIO_Pin_5;
    GPIO_Setup.GPIO_Mode = GPIO_Mode_Out_PP; // Push-Pull Output
    GPIO_Setup.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOC, &GPIO_Setup);
}


int main() {
    uint8_t A, B, Cin, Sum, Carry;
    uint8_t temp1, temp2, temp3, temp4, temp5;
    
  
    NVIC_PriorityGroupConfig(NVIC_PriorityGroup_2);
    SystemCoreClockUpdate();
    Delay_Init();
    Configure_GPIO();
    
    while (1) {
        
        A = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_1);
        B = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_2);
        Cin = GPIO_ReadInputDataBit(GPIOD, GPIO_Pin_3);
        
      
        temp1 = XOR_Gate(A, B);
        Sum = XOR_Gate(Cin, temp1);
        temp2 = AND_Gate(A, B);
        temp3 = AND_Gate(B, Cin);
        temp4 = AND_Gate(Cin, A);
        temp5 = OR_Gate(temp2, temp3);
        Carry = OR_Gate(temp4, temp5);
        
      
        GPIO_WriteBit(GPIOC, GPIO_Pin_4, (Sum == 0) ? SET : RESET);
        GPIO_WriteBit(GPIOC, GPIO_Pin_5, (Carry == 0) ? SET : RESET);
    }
}
