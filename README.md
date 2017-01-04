# jsPCB

Procedural PCB generation language compiler.

This is just an idea for now.

## language features

Nets are represented by ``$NetName``

Components are represented by ``#PartName``

## language example

```
#import('lib/arduino.jspcb')

def #Resistor(value) {
  size: (30, 10)
  silkscreen:
    top(value, 10, -10)
  pins:
    A - hole(10, 5, size=5, diameter=2)
    B - hole(20, 5, size=5, diameter=2)
}

def #Terminal() {
  size: (20, 40)
  pins:
    A - pad(10, 10, size=(5,5))
    B - pad(10, 20, size=(5,5))
}

board(200, 100) {
  #Resistor(20, 20, rotate=90°, ref=R1, value=500) {
    A - #Terminal.B [$GND]
    B - #Arduino.P1
  }

  #Resistor(20, 40, ref=R2, value=1K) {
    A - #Terminal.A [$VIN]
    B - #Arduino.P2
  }

  #Terminal(ref=PWR_IN) {
    A - [$VIN]
    B - [$GND]
  }

  #Arduino() {
    P1 -
    P2 -
  }
}
```
