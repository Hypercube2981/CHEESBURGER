# CHEESBURGER II Schematic Generator
#
# Reads machinecode.txt and generates a WorldEdit schematic.
#
# Requires:
#     pip install mcschematic

import mcschematic
import os

# Configuration

# Paste file directory in the quotations on the INPUT_FILE line
INPUT_FILE = ""

OUTPUT_FOLDER = "output"
OUTPUT_NAME = "program"

BLOCK_ZERO = "minecraft:lime_wool"
BLOCK_ONE = "minecraft:repeater[facing=east]"

MC_VERSION = mcschematic.Version.JE_1_21_1

# ------------------------------------------------------------

schem = mcschematic.MCSchematic()

instruction_count = 0
ones = 0
zeros = 0


def place_byte(byte_string, x, z, start_y):
    """
    Places one byte vertically.

    Bit 0 (MSB) is at the top.
    """

    global ones
    global zeros

    for bit in range(8):

        y = start_y - bit * 2

        if byte_string[bit] == "1":
            schem.setBlock((x, y, z), BLOCK_ONE)
            ones += 1
        else:
            schem.setBlock((x, y, z), BLOCK_ZERO)
            zeros += 1


with open(INPUT_FILE) as f:

    for line_number, line in enumerate(f, start=1):

        instruction = line.strip()

        if instruction == "":
            continue

        # Validation

        if len(instruction) != 16:
            raise Exception(
                f"Line {line_number}: "
                f"Expected 16 bits, got {len(instruction)}."
            )

        if any(c not in "01" for c in instruction):
            raise Exception(
                f"Line {line_number}: "
                "Instruction contains characters other than 0 and 1."
            )

        # Compute instruction position

        column = instruction_count % 16
        bank = instruction_count // 16

        south_offset = 0

        if 256 <= instruction_count < 512 or 768 <= instruction_count < 1024:
            south_offset = 4 if column % 2 == 0 else 2

        x = -7 * column
        z = bank * 2 + (column % 2) + south_offset

        # Split into bytes

        byte1 = instruction[:8]
        byte2 = instruction[8:]

        # Place bytes

        place_byte(byte1, x, z, -2)
        place_byte(byte2, x, z, -20)

        instruction_count += 1


# Save schematic

os.makedirs(OUTPUT_FOLDER, exist_ok=True)

schem.save(
    OUTPUT_FOLDER,
    OUTPUT_NAME,
    MC_VERSION
)

print("--------------------------------------")
print("CHEESBURGER II Schematic Generator")
print("--------------------------------------")
print(f"Instructions : {instruction_count}")
print(f"Repeaters    : {ones}")
print(f"Lime Wool     : {zeros}")
print()
print(f"Saved to: {OUTPUT_FOLDER}/{OUTPUT_NAME}.schem")
