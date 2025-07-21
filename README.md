# BASH2

 String Manipulation

    ${var:start:length} → Get a substring

    ${var/match/replace} → Replace first match

    ${var//match/replace} → Replace all matches

➕ Math in Bash

Use $(()) for arithmetic:

echo $((4+2))   # 6 (addition)  
echo $((4-2))   # 2 (subtraction)  
echo $((4*2))   # 8 (multiplication)  
echo $((4/2))   # 2 (division)  
echo $((4%2))   # 0 (modulo)  
echo $((4**2))  # 16 (exponent)

🎲 Random Numbers

$RANDOM → random number
Set range:

echo $(($RANDOM % 10 + 1))    # 1–10  
echo $(($RANDOM % 11 + 10))   # 10–20

📦 Arrays in Bash

Declare:

declare -a arrayName=(item1 item2 item3)
arrayName=(item1 item2 item3)
arrayName[0]=item1

Access:

${arrayName[0]}    # First element  
${arrayName[@]}    # All elements (preserve quoting if in "")  
"${arrayName[@]}"  # “One Item” “Two Item”  
"${arrayName[*]}"  # “One Item Two Item” (as 1 string)  
${#arrayName[@]}   # Length of array

🧪 Input Redirection from Variables

value="welcome"
cat <<< $value     # Output: welcome

📋 Heredoc Syntax

Redirect multi-line input without a file:

sftp user@server.com <<EOF
put file.txt
dir
EOF

With variables:

file=file.txt
sftp user@server.com <<EOF
put $file
dir
EOF

Send literal variable name (no expansion):

ssh user@server.com <<'EOF'
echo $USER
EOF

🎨 Bash Formatting (Text/Color)

    Requires terminal support

    Escape character: \033 (or \e)

    Formatting stays active until reset

Bold text:

echo -e "\033[1m Test \033[0m"

Change color:

echo -e "\033[32m"    # Green

Reset formatting:

\033[0m
