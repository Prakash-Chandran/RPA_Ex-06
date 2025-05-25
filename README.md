# RPA_Ex-06

# Exercise-6-Copy-and-Rename-Files
~~~
Name : PRAKASH.C
Reg.No : 212223240122
~~~
## Aim
To create a UiPath workflow that copies all files from a source folder to a destination folder and renames them by appending a timestamp to each file name.

## Materials Required
UiPath Studio (Community or Enterprise Edition)

Windows OS

Two folders on your system:

Source Folder (e.g., C:\Users\YourName\Documents\SourceFiles)

Destination Folder (e.g., C:\Users\YourName\Documents\RenamedFiles)

Basic understanding of file operations and string manipulation

## Procedure
### Step 1: Create a New Process
Open UiPath Studio and create a new process named CopyRenameFiles.

### Step 2: Create Input Variables
Create the following variables in the Variables panel:

Name : Type	Default Value (optional)
sourceFolder : String	"C:\Users\YourName\Documents\SourceFiles"
destFolder : String	"C:\Users\YourName\Documents\RenamedFiles"
files : String[]	(leave blank)

### Step 3 : Get All Files from Source Folder
Drag an Assign activity:
~~~
files = Directory.GetFiles(sourceFolder)
~~~

### Step 4: Use For Each to Loop Through Files
 i. Add a For Each activity.
 ii. ForEach item: file In files
 iii. Set TypeArgument to String.

### Step 5: Inside the Loop – Generate Timestamp
Add an Assign activity inside the loop:
~~~
timeStamp = Now.ToString("yyyyMMdd_HHmmss")
Create a timeStamp variable of type String.
~~~

### Step 6: Get File Name and Extension

Add two Assign activities:
fileName = Path.GetFileNameWithoutExtension(file)
extension = Path.GetExtension(file)
(Create fileName and extension variables of type String)

### Step 7: Build New File Name
Add Assign:
~~~
newFileName = fileName + "_" + timeStamp + extension
(Create newFileName as a String variable)
~~~
### Step 8: Copy File to Destination Folder
1. Add another Assign:
~~~
destPath = Path.Combine(destFolder, newFileName)
(Create destPath as a String variable)
~~~
2. Then use Copy File activity:
From: file
To: destPath

## OUTPUT:
After execution, every file in the source folder will be copied to the destination folder and renamed like:

![6-1](https://github.com/user-attachments/assets/325d414e-3b08-412b-88f4-800ea8acbfd0)

![6-2](https://github.com/user-attachments/assets/3fe8eb90-74f1-4391-b8d2-7fbd0d5bd3a0)

![6-3](https://github.com/user-attachments/assets/68e2cc7d-aa0e-4e31-b1e1-dc5ce6166233)

![6-4](https://github.com/user-attachments/assets/552ef5c3-2ff5-4e6e-87eb-f37ac9954c49)


## Result:
The UiPath workflow successfully reads all files from a source folder, appends a timestamp to each file name, and copies them to a new destination folder.
