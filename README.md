# CSAW AI Hardware Challenge 2 Hard
## How AI was used in this challenge
The Claude Sonnet 4 Copilot in VS Code was used to complete this challenge. All the rtl files and the problem statement were uploaded to the AI chat and instructions to edit the files to implement the trojan were given to the Copilot. The Copilot the proceeded to iterate multiple times, editing the code and resolving any errors. It also created a test bench, quick_trojan_test.v, that can be used to show the working of the trojan.
## Testing the working of the trojan
In order to test the trojan the following command can be run in powershell:
''' powershell
iverilog -g2012 -o quick_test.vvp quick_trojan_test.v wbuart.v rxuart.v txuart.v ufifo.v; vvp quick_test.vvp
'''
This test bench will highlight the working of the trojan.
## Working of the trojan.
This is a covert channel trojan that leaks data by modulating the time taken in transferring data. Each '1' bit in the target takes 4 cycles to send, and '0' bits take 3 cycles to send. The trojan is triggered when the user sends the trigger sequence `0xDE 0xAD` followed by the target byte.