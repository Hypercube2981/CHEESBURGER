To upload a program to the CPU, you first need to write it. You can do this in notepad or word, but I actually recommend writing it in a python file. This way you don't need to keep pressing tab a bunch of times. Every line needs to be indented so you can place a label at the start of any line.
I actually recommend indenting 2 or 3 times to make room for longer labels. Here is a Fibonacci example program.

      CAL.fib
      HLT
.fib  LDI r3 0
      LDI r4 9
      LDI r1 1
      LDI r2 2
      ADD r1 r2 r1
      ADI r3 1
      SUB r3 r4 r0
      BIZ 13
      ADD r1 r2 r2
      ADI r3 1
      SUB r3 r4 r0
      BIZ 13
      JMP 4
      RTN


Save you're assembly program once you've written it.
Copy the file, run the assembler, and paste the file directory when it says to.
A machinecode.txt file will automatically be created if one doesn't already exist containing the machine code.
Now you can run the schematic generator, which will save your program to a .schem file which you can put in your schematics folder.
It saves it as just program.schem. Feel free to rename it to whatever you want.
Now you can load into the CPU world, go and stand on the white block on on the instruction memory and run
//schem load program
and then
//paste -a
You may want to run //paste -a a couple times just to be safe.

Between the instruction memory and the RAM, if you fly down, you will find the main clock, which is orange. <img width="2559" height="1365" alt="Screenshot 2026-11-04 210619" src="https://github.com/user-attachments/assets/f52a19ed-f2b1-45a8-8fa3-8b992b145775" />
You'll know when you find it because it has the only button in the entire CPU. before pressing it though. Make sure the program counter is set to 0.
To do this, just flick the lever on the write wool near the clock, leave it on for 5 or 6 seconds, and then turn it back off. Wait about 10 seconds and then press the button to start the clock.
If your program is bugged and you need to manually halt it, just break one of the dust in the clock, wait for the clock to stop and replace it.
You are definitely going to want to speed up the tick rate with the /tick command. If you are running a particularly hefty program, I recommend running it on MCHPRS.

I know I didn't exactly make it user friendly, but I am going to assume it is not a big deal because I doubt anyone who has already made it this far is not a comp sci nerd.

You will notice that I don't have any example programs, for example, those that I used in my showcase video, and well, what did you expect. I can't make it too easy for you to reap the rewards of my hard work. You gotta write your own programs!

Anyway, here is a link to the instruction set (google sheets) and the world download (google drive)

https://docs.google.com/spreadsheets/d/1CerGGBZtiVhNQj9SbhYAk6pjdfWSGLXxFflY5m38QGQ/edit?pli=1&gid=0#gid=0

https://drive.google.com/file/d/1IH2JYcOXePGWOcgDpfV0uX8qRNkSnIfP/view?usp=sharing
