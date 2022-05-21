# Welcome to MSR Commissioning Documents Program Project!

(MCDPP-Hoslab)

Hi! This project was started by me to create a small efficient method of programming and simulating MSR-electronik.de gas detection control logic on your desktop. The theory being, you may configure your system on the desktop before you go to site.

# Project Goals

1. Develop a program to format the CSV documents from Polygard 2 and Polygard 1 series of controllers into a readable Excel document.
   1.1 Use test based development to ensure any failure modes are caught early.
   1.2 Generate a more usable UI which shall require minimal clicking to create and generate programming files.
   1.3 Create a formatted excel / PDF output file to amplify the readability of the Controller programming. Similar to template file below:
   <img src=".\src\assets\Cause_and_Effect_Matrix.xlsx - Excel.png"  
        alt="cause and effect table"  
        style="float: left; margin-right: 10px;" />
2. Create a self generated cause and effect chart which will allow assignment of relay outputs to actions such as, AR1 = Strobe Alarm RM 123 . The goal is to create a formatted excel / pdf file which shall include multiplied relays and be used to perform final functional testing.
   2.1 Develop tests for the system logic prior to coding.
   2.2 Create a formatted output similar to template file below:
   <img src=".\src\assets\Cause_and_Effect_Matrix.xlsx - Excel.png"  
        alt="cause and effect table"  
        style="float: left; margin-right: 10px;" />
3. Using the functional cause and effect tool created in step 2 use automated logic to generate functional testing points and documentation for the project.
4. Create a graphical user interface to allow programming / generation of csv files to be input directly into the Polygard 2 & Polygard 1 controllers allowing instant programming and ability for engineers to configure systems ahead of time.
   4.1 Details to be added.

# Tech Stack

Svelte-TS & Tauri is being used for this project.
