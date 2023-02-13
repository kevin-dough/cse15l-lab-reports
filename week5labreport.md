## Week 5 Lab Report
> By Kevin Do

## Using the less command in bash

The `less` command shows a file's contents page by page.

```bash
less [options] filepath
```

### Showing Line Numbers

To show line numbers when viewing file contents, use the option `-N` when executing the command. Showing line numbers is useful for locating a specific line in code reviews, etc.

```bash
less -N filepath
```

![image](https://user-images.githubusercontent.com/54718041/218557507-cbfa4c25-b748-45a9-84fa-0bdce5c282cd.png)
![image](https://user-images.githubusercontent.com/54718041/218558069-ef07d12d-cb86-459b-ae34-b1bbf613148f.png)

While viewing the file, you can also turn on the line numbers by typing `-N` and pressing return. To turn off the line numbers, type `-n` and return.

![image](https://user-images.githubusercontent.com/54718041/218557596-9d119cd8-4aa0-4ceb-bb08-f61c50be382b.png)
> after typing `-n`

![image](https://user-images.githubusercontent.com/54718041/218557833-cff6b1e3-c26b-4b1d-861a-df3e289a269b.png)
> Turning the line numbers back on

citation: [`https://phoenixnap.com/kb/less-command-in-linux`](https://phoenixnap.com/kb/less-command-in-linux)

### Searching the file for a string

Once you have opened the file with `less`, use a `/` and type the string to execute a forward search. To do a backward search use a `?`. After searching, you can navigate to the next or previous search in the file by using `n` to go forward and `N` to go backward. This command is useful for finding a certain section of a text file or your code. It makes navigating easier.

```bash
/text-to-search
```

```bash
?text-to-search
```

![image](https://user-images.githubusercontent.com/54718041/218558618-55243e8e-6b92-4e75-acce-e4b44c9d8ed2.png)

![image](https://user-images.githubusercontent.com/54718041/218558635-54a1c6e1-5927-4476-a79e-5a7f50adf2a5.png)

![image](https://user-images.githubusercontent.com/54718041/218558704-d29a0e08-a7b3-4ff2-be5e-4f122aa39dc5.png)
> after pressing `n` the next lines that contain "the" will be shown

![image](https://user-images.githubusercontent.com/54718041/218558787-a0e9a51b-6a63-4faa-8509-92fddf5fa8f5.png)
> after pressing `N` the previous lines that contain "the" will be shown

citation: [`https://phoenixnap.com/kb/less-command-in-linux`](https://phoenixnap.com/kb/less-command-in-linux)

### Opening a file to a specified pattern

Use the option `-p` to open the file on the page that contains the pattern listed after the `-p`. For example, `-pTEST` will open the file to the page that contains the string `TEST`. This would be faster than opening a file and then searching for a specific key phrase.

```bash
less -pPATTERN filename
```

![image](https://user-images.githubusercontent.com/54718041/218580246-145dd66e-ee74-4c89-b7ef-c90a8052798e.png)

![image](https://user-images.githubusercontent.com/54718041/218580231-54d0c157-051c-43ff-ae83-277ccf49398f.png)

If the pattern is not found, the terminal will display that it was not found and will open the file to view afterwards.

![image](https://user-images.githubusercontent.com/54718041/218580586-cbbe1556-a841-4075-8ffd-f41cbd137b70.png)

![image](https://user-images.githubusercontent.com/54718041/218580557-5bb1de97-ab07-4d3e-9e6b-a42e59a4028a.png)

citation: [`https://phoenixnap.com/kb/less-command-in-linux`](https://phoenixnap.com/kb/less-command-in-linux)

### Keeping file contents in terminal after exiting

By default, the contents of the file will dissapear after exiting the viewer. To keep the contents in the terminal, use the option `-X`. This is useful because the contents of the file could be used for other commands that you may want to execute afterwards. You may want to reference the text in the file and it would be helpful to see it in the history.

```bash
less -X filename
```

![image](https://user-images.githubusercontent.com/54718041/218581509-1d1b4324-deaa-4d43-bd06-3ecaf6356286.png)

![image](https://user-images.githubusercontent.com/54718041/218581453-db7d4967-ad76-444c-b800-ef7cd6be5774.png)
> If you have text highlighted from searching or marking, the text will still be highlighted after exiting.

citation: [`https://phoenixnap.com/kb/less-command-in-linux`](https://phoenixnap.com/kb/less-command-in-linux)
