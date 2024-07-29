- The first line in shell script is shebang.
    
    #!/bin/bash   << shebang
    
- Shebang is the interpreter, the commands written inside shell script are interpreted and executed by this shebang.
- like bash shell, we have other shells like zshell, cshell etc..But bash shell has all the latest and advanced features which other shells doesn’t have.
- Below is the sample hello-world shell script:
    
    #!/bin/bash
    
    echo "Hello, I am learning DevOps"
    
- **Variables:**
    - variables hold some values.
    - if you change the variable value, it will be automatically reflected everywhere it is referred/called.
    - Variable name is case sensitive and can consist of a combination of letters and the underscore "_". Value assignment is done using the "=" sign.
    - Note that no space permitted on either side of = sign when initializing variables.
    - A backslash "\" is used to escape special character meaning
    - Encapsulating the variable name with **""** will preserve any white space values
    
    ```bash
    greeting='Hello        world!'
    echo $greeting" now with spaces: $greeting"
    
    ```
    
    ### Below is the plane script which doesn’t has any variables declared.
    
    — 
    
    #!/bin/bash
    
    echo "Ramesh: Hello Suresh, How are you?"
    echo "Suresh: Hi Ramesh, I am fine. How are you?"
    echo "Ramesh: I am fine too. how is your work?"
    echo "Suresh: not bad. I am thinking to upgrade to DevOps"
    
    — 
    
    Below is the script we modified from above one and declared variables inside it.
    
    — 
    
    #!/bin/bash
    
    #declaring of varible                    << this is the # commented line and it will be ignored by the script.
    **PERSON1**=Sachin #no space between = and value
    **PERSON2**=Rahul
    
    #referring variable
    echo "**$PERSON1**:: Hello **$PERSON2**, How are you?"
    echo "${PERSON2}:: Hi $PERSON1, I am fine. How are you?"
    echo "$PERSON1:: I am fine too. how is your work?"
    echo "$PERSON2:: not bad. I am thinking to upgrade to DevOps"
    
    — 
    
    - In above script,
        
        **PERSON1** - It is a variable and holds the value “Sachin”
        
        **PERSON2** - It is a variable and holds the value “Rahul”
        
    - we are calling these 2 variables inside the script by using **$** symbol.
        
        echo "**$PERSON1**:: Hello **$PERSON2**, How are you?"
        echo "**${PERSON2}**:: Hi **$PERSON1**, I am fine. How are you?"
        
    - There are 2 ways for calling a variable inside the script, both of them does the same Job.
        1. **$PERSON1**
        2. **${PERSON1}**
    
    - **Below is an additional method of declaring the variables from outside the script, from the command line itself:**
    
    — 
    
    #!/bin/bash
    
    #declaring of varible
    PERSON1=**$1**
    PERSON2=**$2**
    
    #referring variable
    echo "$PERSON1:: Hello $PERSON2, How are you?"
    echo "$PERSON2:: Hi $PERSON1, I am fine. How are you?"
    echo "$PERSON1:: I am fine too. how is your work?"
    echo "$PERSON2:: not bad. I am thinking to upgrade to DevOps"
    
    — 
    
    - Here we have declared as $1 and $2 as a variable value in above one.
    - So, while executing the script from the terminal itself we can give those variable values like below.
        
        #**sh [test-script.sh](http://test-script.sh) Ramesh Suresh**
        
        - Ramesh will be considered as variable value of **$1.**
        - Suresh will be considered as variable value of **$2.**
    
    ### Reading the variable value from command line:
    
    - In below script we are giving username and password in command line, so the script is reading and storing that username and password as a variable value.
        
        — 
        
        #!/bin/bash
        
        echo "Please enter username::"
        
        read -s USERNAME                     #here USERNAME is variable
        
        echo "Please enter password::"
        
        read -s PASSWORD
        
        echo "Username is: $USERNAME, Password is: $PASSWORD"
        
        — 
        
        - **`-s` Option:** The `-s` option (short for "silent") prevents the input from being displayed on the screen as the user types. This is commonly used for password prompts to keep the input hidden for security reasons.
- **Arguments:**
    - Arguments can be passed to the script when it is being executed, by writing
     them as a space-delimited list following the script file name.
    - Inside the script, the $1 variable references the first argument in the command line, $2 the second argument and so forth.
    - The variable $0 references to the current script. In the following example, the script name is followed by 6 arguments.
    
    ## Example
    
    my_shopping.sh file contains below code.
    
    **bash my_shopping.sh apple 5 banana 8 "Fruit Basket" 15**
    
    bash <script name>        1        2       3       4             5             6            << representing 6 variables.
    
    ```bash
    #!/bin/bash
    echo "File name is "$0 # holds the current script
    echo $3 # $3 holds banana
    Data=$5
    echo "A $Data costs just $6."
    echo $#
    
    ```
    
    Executing the script on terminal as,
    
    **bash my_shopping.sh apple 5 banana 8 "Fruit Basket" 15**
    
    bash <script name>        1        2       3       4             5             6            << representing 6 variables.
    
    output is
    
    **File name is my_shopping.sh**
    
    **banana**
    
    **A Fruit Basket costs just 15**
    
    **6**
    
    - The variable $# holds the number of arguments passed to the script
    - The variable $@ holds a space delimited string of all arguments passed to the script
- **Array:**
    - An array is called list of values.
    - An array can hold several values under one name. Array naming is the same as variables naming. An array is initialized by assign space-delimited values enclosed in ()
    - An array is a variable containing multiple values. Any variable may be used as an array. There is no maximum limit to the size of an array, nor any requirement that member variables be indexed or assigned contiguously. Arrays are zero-based: the first element is indexed with the number 0.
        
        ```bash
        my_array=(apple banana "Fruit Basket" orange)
        new_array[2]=apricot
        ```
        
    - The total number of elements in the array is referenced by **${#arrayname[@]}**
        
        ```bash
        my_array=(apple banana "Fruit Basket" orange)
        echo  ${#my_array[@]}                   # 4
        ```
        
    - If you define a variable as array, it can hold list of values.
        
        $**VARIBALE**
        ${**VARIBALE**}
        
    
    Example:
    
    ```jsx
    #!/bin/bash
    
    MOVIES=("RRR" "DjTillu" "murari") 
    
    indexes:        0           1            2      
    
    size of above array is 3.
    
    index are 0,1,2
    
    list always starts with 0.
    
    echo "First Movie is: ${MOVIES[0]}"
    echo "Second Movie is: ${MOVIES[1]}"
    echo "All Movies are: ${MOVIES[@]}"
    ```
    
    - **MOVIES** - Is an array
    - **RRR DJTillu Murari** - are the list of values inside an array
    - The size of an array is 3 (RRR DJTillu Murari)
    - The indexes are 0, 1, 2 (RRR DJTillu Murari), because list is always starts with 0.
    - **${MOVIES[0]}** - declaring the **first** value from list of an array
    - **${MOVIES[1]}** - declaring the **second** value from list of an array
    - **${MOVIES[@]}** - declaring **all values** from list of an array
    
- **Special Variables: Important:**
    - $@ - All variables or All arguments passed to script or function
    - $*- All arguments passed to script or function.
    - $# - Number of variables or parameters passed
    - $0 - The filename of the current script
    - $PWD - current working directory
    - $HOME - Home directory of the current user
    - $USER - Which user is running the script
    - $HOSTNAME - Hostname
    - $$ - Process ID of the current shell script
    - $! - Process ID of the last background command
    - **$? - exit status of a previous command**
        - 0 = success
        - 1 -127 = failed (other than 0, any exit code is failure)
    
    - Below is the sample script which will show the outputs of all these special variables.
        
        — 
        
        ```jsx
        #!/bin/bash
        
        echo "All variables: $@"
        echo "Number of variables passed: $#"
        echo "Script Name: $0"
        echo "Current working directory: $PWD"
        echo "Home directory of current user: $HOME"
        echo "Which user is running this script: $USER"
        echo "Hostname: $HOSTNAME"
        echo "Process ID of the current shell script: $$"
        sleep 60 &                  #given sleep 60 to check the process ID of above command.
        echo "Process ID of last background command: $!"
        ```
        
        — 
        
- **Conditions:**
    - We use conditions when you want to take a decision.
    - whenever there is an “If” in the requirement or scenario then conditions will comes into picture.
    - Ex: check if 10 is > 10, or < 10, or =10, high low etc.. certain conditions.
        
        Example:
        
    
    — 
    
    ```jsx
    #!/bin/bash
    
    NUMBER=$1
    
    if [ $NUMBER -gt 10 ]
    then
        echo "Given number $NUMBER is greater than 10"
    else
        echo "Given number $NUMBER is less than 10"
    fi
    ```
    
    - -gt >> greaterthan
    - -lt >> lessthan
    - -eq >> equalsto
    - -ge >> grearthan or equals to
    - -le >> lessthan or equals to
    - -ne >> Not equals to
    - **Types of numeric comparisons:**
    
    ```bash
    comparison    Evaluated to true when
    $a -lt $b    $a < $b
    $a -gt $b    $a > $b
    $a -le $b    $a <= $b
    $a -ge $b    $a >= $b
    $a -eq $b    $a is equal to $b
    $a -ne $b    $a is not equal to $b
    ```
    
    - **Types of string comparisons:**
    
    ```bash
    comparison    Evaluated to true when
    "$a" = "$b"     $a is the same as $b
    "$a" == "$b"    $a is the same as $b
    "$a" != "$b"    $a is different from OR not equal to $b
    -z "$a"         $a is empty
    ```
    
    - **note1**: whitespace around = is required
    - **note2**: use "" around string variables to avoid shell expansion of special characters as *
    - Below are some of the examples:
    - The basic conditional decision making construct is:
        
        **if [ expression ]; then**
        
        code if 'expression' is true
        
        **fi**
        
    
    ```bash
    NAME="John"
    if [ "$NAME" = "John" ]; then
      echo "True - my name is indeed John"
    fi
    
    ```
    
    It can be expanded with 'else'
    
    ```bash
    NAME="Bill"
    if [ "$NAME" = "John" ]; then
      echo "True - my name is indeed John"
    else
      echo "False"
      echo "You must mistaken me for $NAME"
    fi
    
    ```
    
    It can be expanded with 'elif' (else-if)
    
    ```bash
    NAME="George"
    if [ "$NAME" = "John" ]; then
      echo "John Lennon"
    elif [ "$NAME" = "George" ]; then
      echo "George Harrison"
    else
      echo "This leaves us with Paul and Ringo"
    fi
    
    ```
    
- **Loops:**
    - bash for loop
    
    ```bash
    # basic construct
    for arg in [list]
    do
     command(s)...
    done
    ```
    
    - For each pass through the loop, arg takes on the value of each successive value in the list. Then the command(s) are executed.
    
    ```bash
    # loop on array member
    NAMES=(Joe Jenny Sara Tony)
    for N in ${NAMES[@]} ; do
      echo "My name is $N"
    done
    
    # loop on command output results
    for f in $( ls prog.sh /etc/localtime ) ; do
      echo "File is: $f"
    done
    
    ```
    
    - bash while loop
    
    ```bash
    # basic construct
    while [ condition ]
    do
     command(s)...
    done
    
    ```
    
    - The while construct tests for a condition, and if true, executes commands. It keeps looping as long as the condition is true.
    
    ```bash
    COUNT=4
    while [ $COUNT -gt 0 ]; do
      echo "Value of count is: $COUNT"
      COUNT=$(($COUNT - 1))done
    
    ```
    
    - bash until loop
    
    ```bash
    # basic construct
    until [ condition ]
    do
     command(s)...
    done
    
    ```
    
    - The until construct tests for a condition, and if false, executes 
    commands. It keeps looping as long as the condition is false (opposite 
    of while construct)
    
    ```bash
    COUNT=1
    until [ $COUNT -gt 5 ]; do
      echo "Value of count is: $COUNT"
      COUNT=$(($COUNT + 1))done
    
    ```
    
    - **"break" and "continue" statements**
        
        break and continue can be used to control the loop execution of for, while and until constructs. continue is used to skip the rest of a particular loop iteration, whereas break is used to skip the entire rest of loop. A few examples:
        
    
    ```bash
    # Prints out 0,1,2,3,4
    
    COUNT=0
    while [ $COUNT -ge 0 ]; do
      echo "Value of COUNT is: $COUNT"
      COUNT=$((COUNT+1))if [ $COUNT -ge 5 ] ; then
        break
      fi
    done
    
    # Prints out only odd numbers - 1,3,5,7,9
    COUNT=0
    while [ $COUNT -lt 10 ]; do
      COUNT=$((COUNT+1))# Check if COUNT is even
      if [ $(($COUNT % 2)) = 0 ] ; then
        continue
      fi
      echo $COUNT
    done;
    ```
    
    - **Example Exercise:**
        - In this exercise, you will need to loop through and print out all even numbers from the numbers list in the same order they are received. Don't print any numbers that come after 237 in the sequence.
        - **Solution:**
            
            #!/bin/bash
            NUMBERS=(951 402 984 651 360 69 408 319 601 485 980 507 725 547 544 615 83 165 141 501 263 617 865 575 219 390 237 412 566 826 248 866 950 626 949 687 217 815 67 104 58 512 24 892 894 767 553 81 379 843 831 445 742 717 958 609 842 451 688 753 854 685 93 857 440 380 126 721 328 753 470 743 527)
            
            write your code here:
            
            ```
            
            for gg in ${NUMBERS[@]}; do
            if [ $gg == 237 ]; then
            	break;
            elif [ $(($gg % 2)) == 0 ]; then
            	echo $gg
            fi
            done
            ```
            
- **Datatypes:**
    
    ```jsx
    #!/bin/bash
    
    NO1=$1
    NO2=$2
    
    SUM=$(($NO1+$NO2))
    
    echo "Total of $NO1 and $NO2 is: $SUM"
    ```
    
- **Functions:**
    - whenever there is a repeated code, we can use functions to mitigate the repeated code.
    - It is a block of code that can do some work, and it accepts inputs too.
    - If any value keeps repeating inside code, we can declare it as variable. Using variables is a best practice even if its repeated for 1 time also.
    
    Example:
    
    — 
    
    ```jsx
    #!/bin/bash
    
    USERID=$(id -u)                                   #Giving id -u command output as a value to the USERID variable.
    TIMESTAMP=$(date +%F-%H-%M-%S)
    SCRIPT_NAME=$(echo $0 | cut -d "." -f1)    # $0 is meant for script name as part of special variables. 
    LOGFILE=/tmp/$SCRIPT_NAME-$TIMESTAMP.log
    
    VALIDATE(){          #VALIDATE is the function name
    if [ $1 -ne 0 ]         # Here $1 and $2 values are comes from below 
    then
    echo "$2...FAILURE"
    exit 1
    else
    echo "$2...SUCCESS"
    fi
    }
    
    if [ $USERID -ne 0 ]
    then
    echo "Please run this script with root access."
    exit 1 # manually exit if error comes.
    else
    echo "You are super user."
    fi
    
    dnf install mysql -y &>>$LOGFILE
    VALIDATE $? "Installing MySQL"
    
    dnf install git -y &>>$LOGFILE
    VALIDATE $? "Installing Git"
    ```
    
    — 
    
    - SCRIPT_NAME=$(echo $0 | cut -d "." -f1)
    - $0 - is meant for script name
    - cut -d “.” -f1
        - for example if the script name is “[**01-shell-script.sh**](http://01-shell-script.sh) “
        - Then it will separate the name with . and take the first one. that means **01-shell-script**
        - if we separate it with “-” then it will take only “01”
        - Here we are just fragmenting the script name.
    - Explanation of declaring functions:
        
        ```jsx
        dnf install mysql -y &>>$LOGFILE
        VALIDATE $? "Installing MySQL"      \\$? = $1 - exit status, it can be 0 or 1  and Installing MySQL = $2..  it will just display it.
        
        dnf install git -y &>>$LOGFILE
        VALIDATE $? "Installing Git"            \\$? = $1 - exit status, it can be 0 or 1  and Installing Git= $2 .. it will just display it.
        ```
        
    - **Example Function:**
        - In this exercise, you will need to write a function called ENGLISH_CALC which can process sentences such as:
            
            '3 plus 5', '5 minus 1' or '4 times 6' and print the results as: '3 + 5 = 8', '5 - 1 = 4' or '4 * 6 = 24' respectively.
            
            **Solution:**
            
            #!/bin/bash
            
            //enter your function code here
            
            function ENGLISH_CALC {
            a=$1
            b=$3
            signn=$2
            if [ $signn == "plus" ]; then
            echo "$a + $b = $(($a+$b))"
            elif [ $signn == "minus" ]; then
            echo "$a - $b = $(($a-$b))"
            elif [ $signn == "times" ]; then
            echo "$a * $b = $(($a*$b))"
            fi
            }
            
            //testing code
            
            ENGLISH_CALC 3 plus 5
            ENGLISH_CALC 5 minus 1
            ENGLISH_CALC 4 times 6
            
- **Commands/Parameters with Explanation and Examples:**
    
    ### ### Read command/parameter:
    
    - ‘read’ parameter in shell script is used to read the input from the user and store it in a variable.
        1. read -p “Enter your name: ” name
            - here, -p —> for prompting a message before reading it.
            - name —> is the variable and it holds the value which user will input from the command line
        2. echo “Enter your name: “
            
            read name
            
            - here again the ‘name’ is a variable. both 1 and 2 serve the same purpose.
    - **Few other options while using read:**
        - -r — Prevents backslashes from being interpreted as escape characters. Useful when reading file paths.
            
            read -r path
            
        - -a — Read into an array
            
            read -a array_name
            
        - -t — Specifies a timeout in seconds for the read operation
            
            read -n 3 variable_name
            
        - -n — Specifies the number of characters to read.
            
             read -n 3 variable_name
            
        
        - -s — Silent mode. Input will not be displayed on the screen while typing.
            
            read -s password
            
            **Basic Examples:**
            
            1. 
                
                echo "What's your name?"
                read name
                echo "Hello, $name!"
                
            2. **Using -p Option**:
                
                read -p "Enter your age: " age
                echo "You are $age years old."
                
            3. **Reading into an Array**:
                
                echo "Enter three fruits: "
                read -a fruits
                echo "You entered: ${fruits[0]}, ${fruits[1]}, and ${fruits[2]}."
                
            4. **Reading Password in Silent Mode**:
                
                read -s -p "Enter your password: " password
                echo "Password entered."
                
    
    ### **### Sample script examples:**
    
    - **To check if any file or directory is exists or not:**
        
        if [ -e "$FILE" ]; then      --> **If a file or directory exists or not ?**
        if [ -f "$FILE" ]; then  --> **if Above file exists, then what it is readable/executable/writable ?**
        echo "$FILE is a regular file."
        fi
        if [ -d "$FILE" ]; then
        echo "$FILE is a directory."
        fi
        if [ -r "$FILE" ]; then
        echo "$FILE is readable."
        fi
        if [ -w "$FILE" ]; then
        echo "$FILE is writable."
        fi
        if [ -x "$FILE" ]; then
        echo "$FILE is executable/searchable."
        
        - **use "-e" to test if file exist**
            
            ```bash
            #!/bin/bash
            filename="sample.md"
            if [ -e "$filename" ]; then
                echo "$filename exists as a file"
            fi
            ```
            
        - **use "-d" to test if directory exists**
        
        ```bash
        #!/bin/bash
        directory_name="test_directory"
        if [ -d "$directory_name" ]; then
            echo "$directory_name exists as a directory"
        fi
        
        ```
        
        - **use "-r" to test if file has read permission for the user running the script/test**
        
        ```bash
        #!/bin/bash
        filename="sample.md"
        if [ ! -f "$filename" ]; then
            touch "$filename"
        fi
        if [ -r "$filename" ]; then
            echo "you are allowed to read $filename"
        else
            echo "you are not allowed to read $filename"
        fi
        ```
        
    - Imagine you want to store logs of an application into a file and at the same time print it on the console. A very handy command for that is `tee`.
    
    ```bash
    echo "Hello, world!" | tee /tmp/hello.txt
    ```
