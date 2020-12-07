
# Task - Run Sparta Sample Node App on EC2
1. Create an instance in AWS.
2. Connect to the instance
3. Use scp to copy the provisioning file into the virtual machine.
```bash
scp -i ~/.ssh/keyname.pem filename ubuntu@ip:~/location
```
4. Assign execute permissions to the provisioning file by running `chmod +x filename`
5. Use scp to copy the app and environment folders to the virtual machine.
```bash
scp -i ~/.ssh/keyname.pem -r foldername ubuntu@ip:~/location
```
6. Amend the provisioning file, if necessary, to reflect any changes in paths which may have resulted from copying the files.
7. Run the provisioning file.
8. Navigate to the public ip address of the instance. The following page should be displayed on
  * **port 3000**        
  * **and port 80**         

9. As an added test, run the following command to display the html webpage within the terminal.
```bash
curl privateip:3000
```    
