## 3

password: `aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG`

The password for the next level is stored in a hidden file in the **inhere** directory.

```bash
$ find / -type d -name "inhere" -exec sh -c ' 
    for file in "$1"/.*; do 
        if [ -f "$file" ]; then 
            echo "$file:" 
            cat "$file" 
        fi 
    done 
' _ {} \; 2>/dev/null

```

`2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe`

<br><br><br>

## 4

The password for the next level is stored in the only human-readable file in the **inhere** directory. Tip: if your terminal is messed up, try the “reset” command.

```bash
$ find / -type d -name "inhere" 2>/dev/null

$ find "/home/bandit4/inhere" -type f -exec sh -c '
  for file; do
    if file "$file" | grep -q "text"; then
      echo "File: $file"
      cat "$file"
      echo
    fi
  done
' sh {} +
```


`lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR`

<br>

## 5

The password for the next level is stored in a file somewhere under the **inhere** directory and has all of the following properties:

- human-readable
- 1033 bytes in size
- not executable

<br>


```bash
( find / -type d -regex '.*/inhere[^/]*$' \
    | xargs -I {} find {} -type f -size 1033c ! -executable \
    ) 2>/dev/null\
    | xargs -I {} sh -c '
        echo "File: {}"; cat {}'
```


```
P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU
```

<br><br><br>

## 6

The password for the next level is stored **somewhere on the server** and has all of the following properties:

- owned by user bandit7
- owned by group bandit6
- 33 bytes in size

<br>


```bash
find / \
    -user bandit7 \
    -group bandit6 \
    -size 33c \
    -type f \
    2>/dev/null | xargs cat
```

* here, the first slash indicates that the search is from the root directory onwards. 

```
z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S
```

<br>

## 7

The password for the next level is stored in the file **data.txt** next to the word **millionth**

```
ctrl + w
```

* deleted the focused word in the terminal



<br>

```bash
find / -type f -name "data.txt" \
    -exec grep "millionth" {} + \
    2>/dev/null
```

<br>

```
TESKZC0XvTetK0S9xNwm25STk5iWrBvP
```

<br><br><br>

## 8

The password for the next level is stored in the file **data.txt** and is the only line of text that occurs only once


```bash
cat $(find / -type f -name "data.txt" 2>/dev/null)
```

* huge file

<br>

```bash
sort $(find /home/bandit8 -type f -name "data.txt"\
    2>/dev/null)\
    | uniq -u
```


<br>

```
EN632PlfYiZbn3PhVK3XOGSlNInNE00t
```

<br><br><br>

## 9

The password for the next level is stored in the file **data.txt** in one of the few human-readable strings, preceded by several ‘=’ characters.

<br>

```bash
grep -a -oE '=.*' $(\
    find /home/bandit9 -type f -name "data.txt"\
    2>/dev/null)
```

<br>

```
G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
```

<br><br><br>

## 10

The password for the next level is stored in the file **data.txt**, which contains base64 encoded data

<br>

```
6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
```

<br><br><br>

## 11

The password for the next level is stored in the file **data.txt**, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

<br>

```bash
$ cat $(find /home/bandit11 -type f -name "data.txt" 2>/dev/null)\
    | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

<br>

```
JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
```
