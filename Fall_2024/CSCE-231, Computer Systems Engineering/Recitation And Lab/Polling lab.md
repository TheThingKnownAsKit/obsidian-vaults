Plug board in
Open polling lab
Click robot alien face -> pick folder -> go INTO THE POLLING LAB FOLDER, dont just click on it. Should initialize pico stuff and get the build commands on the bottom left

Don't press the upload use the reset bootstrap drag and drop firmware.uf2 thing

<mark style="background: #ADCCFFA6;">Note: for buttons 0 is pressed and 1 is not pressed, and for switches 0 is left and 1 is right</mark>

ioport is what you use to communicate with the board. Each bit position is some information so you can't mess with the whole structure. Don't forget to specify if it's input or output

Basically this entire lab is just replacing built in functions with bitmasks so we do it the hard and manual way

Note: Getting started is all given code to help explain how this all works. Section 4 and 5 can be completed in any order

Anyone who says you HAVE to reupload the code every time is wrong, just hold RESET for a while unless the pdf tells you otherwise
## Getting Started
Given by TAs

Populate keys with:
```C
{0x1, 0x2, 0x3, 0xA},
{0x4, 0x5, 0x6, 0xB},
{0x7, 0x8, 0x9, 0xC},
{0xF, 0x0, 0xE, 0xD}
```

Uncomment these and change the addresses to:
```C
ioport = (cowpi_ioport_t *) (0xD0000000);
timer = (cowpi_timer_t *) (0x40054000);
```

Remember that the bits are BIT POSITIONS, not bit values. So you can just make a bit mask. Consult [table 22](https://cow-pi.readthedocs.io/en/latest/CowPi_rp2040/io_registers.html#tablerp2040mapdevicestostruct) to see that the num pad column bits occupy spaces 10-14, so you just need to know if any bits 10-13 have been pressed (which you can do it with 0xF << 10 since pressed is 0)
```C
bool key_is_pressed = (ioport->input & (0xF << 10)) != (0xF << 10);
```

Set ioport to output. Remember you CANNOT MESS WITH THE OTHER BITS IN IOPORT, so you have to or it with 1 shifted 21 spaces (because the left led is at bit 21 from the sheet)
```C
if (turn_on) {
        (ioport->output |= (1<<21));
    } else {
        (ioport->output &= (1<<21));
    }
```

## Section 4
### 4.1
Literally just return the lower raw word, it is one line of code and it straight up tells you what to do

### 4.2
Left button is at bit 2
Right at bit 3
Remember pressed is 0 and not pressed is 1

Left switch at 14
Right switch at 15
Remember left is 0 and right is 1

THIS USES OUTPUT
right led is at 20

From the docs
```Pseudocode
for each ROW do
    set output pin for each row to 1
    set output pin for ROW to 0
    wait at least one microsecond
    for each COLUMN do
        column_bit := the value on input pin for COLUMN
        if (column_bit = 0) then
            key_pressed := keys(ROW,COLUMN)
set output pins for each row to 0       (* to detect the next keypress *)
```

## Section 5
