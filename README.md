#!/bin/bash
# git clone https://github.com/YousfiSouheib/collgen.git
# y. Accéder et puis on fait make
# Create prefix #
echo "kaity codes" >> prefix.txt

# Generate MD5 Collision #
md5collgen -p prefix.txt -o out1.bin out2.bin

# Compare binary files #
echo -e "Do the generated binaries differ?\n"

diff out1.bin out2.bin

# Check MD5 Hashes #
md5sum out1.bin ; md5sum out2.bin

# Understand bin file contents #
echo -e "Identify the separate parts of bin files (prefix + [padding] + P)\n"

xxd out1.bin

# Compare difference when prefix is mult. of 64 #
echo "$(python -c 'print("A"*63)')" >> prefix_64.txt
echo "Generating MD5 Collision...\n"
md5collgen -p prefix_64.txt -o out1_64.bin out2_64.bin

echo "What is different (apart from the prefixes)?"

xxd out1.bin ; xxd out1_64.bin ou bien avec l'outil bless

