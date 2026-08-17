A company has been storing physical documents for many years and is running out of storage space. <br>
To solve this, the company decides to scan and digitize the documents and store them electronically. <br>
<br>
Before scanning begins, a standardized folder structure needs to be created for each client so that scanned documents can be organized consistently. <br>
Instead of manually creating hundreds or thousands of identical folder structures and naming each one individually, PowerShell and Command Prompt can be used to automate the process using names provided in a CSV file. <br>

Here's how to automate that procedure:<br>

Here's how you can automate that procedure:<br>

1) Create the template folder with all the skeleton folders and place it on your Desktop.<br>

2) Run this code in COMMAND PROMPT, this assumes your folder you want x copied is called 'Template Folder'. If you want 3 folders, keep it (1, 1, 3). If you want 10, change it to (1, 1, 10). Change it accordingly.<br>
Inside Template folder is how you want it copied exactly, aka with Passport folder, Document folder, Photo folder, etc.<br>
```cmd
for /l %A in (1, 1, 3) do @xcopy /E "%USERPROFILE%\Desktop\Template Folder" "%USERPROFILE%\Desktop\Copies\%A" /i
```

3) Now create a CSV called 'Data' with column A 1 to x, and column B next to it with what you want them renamed. Have the header name, newname.<br>
EXAMPLE:<br>
name,newname<br>
1,Johnson Ton 1502519<br>
2,Amy Nguyen 1502520<br>
3,Randy Phan 1502521<br>


4) Run this code in POWERSHELL.
```powershell
$csv = Import-Csv "$env:USERPROFILE\Desktop\Data.csv"
$files = get-childitem "$env:USERPROFILE\Desktop\Copies"

foreach($item in $CSV){
    foreach($file in $files){
        if($item.name -eq $file.basename){
            rename-item $file.fullname -NewName "$($item.newname).$($file.extension)" -Verbose
        }
    }
}
```
