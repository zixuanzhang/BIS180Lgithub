#### lab2 tutorial

* set a list
`set [var_name] name1 name2`
`echo $var_name`

* loop through each item in the list and list them out
`for [anyname] in $var_name`
`echo "$[anyname]"`
`end`

* add "s" to each term in the list
`for i in $fruits`
`echo {$fruit}s`
`end`

* interacting with files

mkdir for_example
cd for_example
echo "this" > file1.txt
echo "is" > file2.txt
echo "silly" > file3.txt

set myfiles (ls)
echo $myfiles

for file in $myfiles
cat $file
end

__exercise 3__

for file in (ls)
echo "file $file contains:" (cat $file)
end

* Creat new files

set newFiles one two three four  
echo $newFiles

for f in $newFiles
    touch {$f}.txt
end

ls  


__nested loop__  

set fruits banana apple orange grape plum pear durian pineapple

for fruit in $fruits   
    for number in 1 2 3 4 5 6 7 8 9 10  
        echo $fruit $number  
    end #ending the inside loop  
end #ending the outside loop
