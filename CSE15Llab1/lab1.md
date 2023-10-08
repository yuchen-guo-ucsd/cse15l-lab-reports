# CSE 15L Lab Report 1
## Yuchen Guo
***
- **cd** w/ no argument: The current working directory is /home. The terminal return nothing but it's not an error because command cd is used to change directory but it is not given the path(no argument)
- ![Image](cd1.png)
- **ls** w/ no argument: The current working directory is /home. The return output lists all directories and files under the current working directory  because we did not put any arguments to give specific path. The output is not an error.
- ![Image](ls1.png)
- **cat** w/ no argument: The current working directory is /home. The return output is empty because cat command is used for showing the content of the file so it shows nothing since we did not put the filename. This might be an error. 
- ![Image](cat1.png)
- **cd** w/ path to a directory: The current working directory is /home, after execute the command, it changes to /home/lecture1. So, since we only change the working directory, there are no other outputs. And outputs have no errors.
- ![Image](cd2.png)
- **ls** w/ path to a directory: The current working directory is /home. The return output lists all directories and files under the directory called lecture1  The output is not an error.
- ![Image](ls2.png)
- **cat** w/ path to a directory: The current working directory is /home. The return output shows an error message because cat command is used for showing the content of the file instead of the directory. 
- ![Image](cat2.png)
- **cd** w/ path to a file: The current working directory is /home. The return output shows an error message because cd command is used for changing directory; however, we put a path to a file after it. So, the output shows the error.
- ![Image](cd3.png)
- **ls** w/ path to a file: The current working directory is /home. The return output shows the path to file Hello.java since it is the only file in the path that was given. The output is not an error.
- ![Image](ls3.png)
- **cat** w/ path to a file: The current working directory is /home. The return output shows the content of the Hello.java file. The output is not an error.
- ![Image](cat3.png)

