In order to create a CSV of all file names of a directory, navigate to it using 'cd' command. <br>
Useful when you are manipulating file names in a spreadsheet and you need to collect data.
```powershell
dir | Export-Csv MyFileList.csv
```
