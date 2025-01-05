# Decompiled Game Project - Survive Game 

## Project Overview
The **SURVIVE GAME** project involves decompiling an existing Android game and implementing various modifications to improve its functionality and enhance the user experience.

## Game Description:
The game consists of a menu screen where the player enters their personal ID. After entering the ID, the player proceeds to the game screen, which presents four directional arrows (left, right, up, down). The player must press the arrows in the correct sequence based on the digits of their ID modulo 4.

### Direction Mapping:
Each digit of the ID corresponds to a specific direction:

- **0** = Left
- **1** = Right
- **2** = Up
- **3** = Down

The player must follow the sequence of their ID to advance through the game. If they press the wrong arrow, they fail. If they correctly complete the sequence, they "survive" and a success message is displayed. The goal is to match the sequence of directions based on the ID.

## Modifications

### 1. **Update Website URL**
   - Updated the URL to ensure the game connects to the correct web resource.

### 2. **Update Toast message**

#### Before:
```java
if (this.goodToGo) {
            Toast.makeText(this, "Survived in " + state, 1).show();
        } else {
            Toast.makeText(this, "You Failed ", 1).show();
        }
```

#### After:
```java
if (this.goodToGo) {
            Toast.makeText(this, "Survived in " + state, Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(this, "You Failed ", Toast.LENGTH_SHORT).show();
        }
```

### 3. **Update Integer Parsing**

#### Before:
```java
                iArr[i] = Integer.valueOf(String.valueOf(id.charAt(i))).intValue() % 4;
```

#### After:
```java
                iArr[i] = Character.getNumericValue(id.charAt(i)) % 4;
```

## Validation:
### Example ID: "269863708"

#### Derived Steps:
The steps array will be derived as follows:

- Character at index 0 ('2') -> 2 % 4 = **2** (Up)
- Character at index 1 ('6') -> 6 % 4 = **2** (Up)
- Character at index 2 ('9') -> 9 % 4 = **1** (Right)
- Character at index 3 ('8') -> 8 % 4 = **0** (Left)
- Character at index 4 ('6') -> 6 % 4 = **2** (Up)
- Character at index 5 ('3') -> 3 % 4 = **3** (Down)
- Character at index 6 ('7') -> 7 % 4 = **3** (Down)
- Character at index 7 ('0') -> 0 % 4 = **0** (Left)
- Character at index 8 ('8') -> 8 % 4 = **0** (Left)

#### Follow the steps:
Press the buttons in the correct order as derived from the ID:

1. **Up**
2. **Up**
3. **Right**
4. **Left**
5. **Up**
6. **Down**
7. **Down**
8. **Left**
9. **Left**

#### Final State:
  The state should be **Survived in California**.

## Video:

https://github.com/user-attachments/assets/dcc6341b-dbbf-4713-b40b-f45f79a2c8a7


