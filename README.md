<h1>Use Linux Commands to Manage File permissions</h1>

 

<h2>Description</h2>
 The research team at my organization needs to review and oversee the permissions of certain files and directories within the projects directory. This is to ensure that the team users are granted with the appropriate authorization. The permissions do not currently reflect the level of authorization that should be given. Checking and updating these permissions will ensure that their system remains secure.

<br />


<h2>Languages and Utilities Used</h2>

- <b>Bourne-Again Shell</b> 


<h2>Environment Used </h2>

- <b>Linux OS</b> 

<h2>Project walk-through:</h2>
<h3>Check file and directory details</h3>
<p>
  The ls -la command displays permissions for files and directories, including hidden files. When we execute this command within the projects directory we obtain the following result : 
 <br/>
 <br/>
<img src="https://i.imgur.com/KOehoSH.png" height="70%" width="70%" alt="ls -la command"/>
<br />
<br />
  The output of my command shows that there is one directory named drafts, as well as four files and one hidden file named .project_x.txt. The 10-character string in the first column represents the permissions set on each file or directory.
 <br/>
</p>
<h3>Describe the permissions string</h3>
<p>
  The 10 character string begins each entry and indicates how the permissions on the file or the directory are set. For instance, a directory with full permissions for all owner types would be drwxrwxrwx .
  <ul>
    <li>The 1st character indicates the file type. The d indicates it’s a directory. When this character is a hyphen (-), it's a regular file.</li>
    <li>The 2nd-4th characters indicate the read (r), write (w), and execute (x) permissions for the user. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted to the user.</li>
    <li>The 5th-7th characters indicate the read (r), write (w), and execute (x) permissions for the group. When one of these characters is a hyphen (-) instead, it indicates that this permission is not granted for the group.</li>
    <li>The 8th-10th characters indicate the read (r), write (w), and execute (x) permissions for the owner type of other. This owner type consists of all other users on the system apart from the user and the group. When one of these characters is a hyphen (-) instead, that indicates that this permission is not granted for the owner type : other.</li>
  </ul>
  For example, the project_k.txt is a file because the first character is (-). It has read and write permissions for the user, the group and "other".
</p>
<h3>Change file permissions</h3>
<p>
  According to the organization policy the owner type other should not have write permission on any file. The previous command indicates that he has this permission on the project_k.txt file. We are going to use the chmod command to remove unauthorized access. 
<br/>
<br />
<img src="https://i.imgur.com/3PoLIzJ.png" height="70%" width="70%" alt="change file permissions"/>
<br />
<br />
 The chmod command changes permissions on files and directories. The first argument indicates what permissions should be changed, and the second argument specifies the file or directory. The output of ls -la indicates that the owner type : "other" no longer has write permission.
 The file project_m.txt is a restricted file. Hence, it should not be readable or writable by the group or the other. Using the chmod command we are going to fix this issue.
<br />
<br />
<img src="https://i.imgur.com/vlOSvw1.png" height="70%" width="70%" alt="change file permissions"/>
<br />
<br />
The output of ls -la command demonstrates that neither the group nor the other has read and write permissions on the project_m.txt file. 
 <br/>
<p/>
<h3>Change file permissions on a hidden file</h3> 
<p>
 The file .project_x.txt is a hidden file that has been archived and should not be written to by anyone but the user and the group should still be able to read the file. The ls -la command indicates that the user has read and write permissions and the group has write permission. To fix this issue we are going to use the chmod command as demonstrated in the following image.
<br />
<br />
<img src="https://i.imgur.com/5TMR08l.png" height="70%" width="70%" alt="Hidden file permissions"/>
<br />
<br />
The output of ls -la command displays that the permissions were successfully updated according to the organization policy.
<br/>
</p>
<h3>Change directory permissions</h3>
<p>
 In the directory drafts under the projects directory, only the user should be able to access the directory and its content, which means we need to remove the execute permission from the group.
<br />
<br />
<img src="https://i.imgur.com/gsr519r.png" height="80%" width="80%" alt="Directory permnissions"/>
<br />
<br />
</p>
<h3>Summary</h3>
<p>
  I changed multiple permissions to match the level of authorization my organization wanted for files and directories in the projects directory. The first step in this was using ls -la to check the permissions for the directory. This informed my decisions in the following steps. I then used the chmod command multiple times to change the permissions on files and directories.

</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
