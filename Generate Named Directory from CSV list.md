# Lets say your company has been working with physical papers for many years. Soon, you realized you're running out of space and you need to find a solution.
# You decided to scan and digitalize them all into a storage. 
# However, you first will need to create templates of folders and have them organized and named so your staff members know where to store the files after they scan them.

# Here's how you can automate that procedure:

## 1) Create the template folder with all the skeleton folders and place it on your Desktop.

## 2) Run this code in COMMAND PROMPT, this assumes your folder you want x copied is called 'Template Folder'. If you want 3 folders, keep it (1, 1, 3). If you want 10, change it to (1, 1, 10). Change it accordingly.
## Inside Template folder is how you want it copied exactly, aka with Passport folder, Document folder, Photo folder, etc.
```cmd
for /l %A in (1, 1, 3) do @xcopy /E "%USERPROFILE%\Desktop\Template Folder" "%USERPROFILE%\Desktop\Copies\%A" /i
```

## 3) Now create a CSV called 'Data' with column A 1 to x, and column B next to it with what you want them renamed. Have the header name, newname.
## EXAMPLE:
## name,newname
## 1,Johnson Ton 1502519
## 2,Amy Nguyen 1502520
## 3,Randy Phan 1502521


## 4) Run this code in POWERSHELL.
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
