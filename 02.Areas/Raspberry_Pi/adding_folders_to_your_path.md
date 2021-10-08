# How to Add Folders or Files to Your Path

Use this command:
```shell
 export PATH="<path to the folder>:$PATH"
 ```
 However this change is temporary abd is only valud in the current shell session. To make it permanent you will have to add the code to the .bashrc file.
 
 Example of the bottom of the .bashrc file:
 ```bash
  export PATH="/home/ruairidh/.local/bin:$PATH"
 ```