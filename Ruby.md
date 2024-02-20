# Ruby

## Table of Contents:
- [Arrays](#arrays)

## Arrays

- ### Traversing
    ```ruby
        a = [1,2,3]
        a.each do |i|
            print i, " "
        end # 1 2 3
        for i in a
            print i, " "
        end # 1 2 3
        i = 0
        while i < a.length
            print a[i], " "
            i += 1
        end # 1 2 3
        i = 0
        until i === a.length
            print a[i], " "
            i += 1
        end # 1 2 3
        a.each_with_index do |element, index|
            print "#{index}: #{element} "
        end # 0: 1 1: 2 2: 3
        (0..a.length).step(2) do |i|
            print a[i], " "
        end # 1 3
        for i in (0...a.length).step(2)
            print a[i], " "
        end # 1 3
        a.length.times do |i|
            print a[i], " "
        end # 1 2 3
        0.upto(a.length - 1) do |i|
            print a[i], " "
        end # 1 2 3
    ```
- ### sum
    ```ruby
        [1,2,3].sum        # 6
        [1,2,3].inject(:+) # 6
        [1,2,3].reduce(:+) # 6
    ```
- ### max
    ```ruby
        [1,2,3].max # 3
    ```  
- ### min
    ```ruby
        [1,2,3].min # 1
    ```  
- ### create an array
    ```ruby
        (0..3).to_a       # [0, 1, 2, 3]
        (0..3).map{|i| i} # [0, 1, 2, 3]
    ```
- ### sort an array
    ```ruby
        [3,2,1].sort
        [3,2,1].sort!
    ```
- ### mutate
    ```ruby
        [1,2,3].map{ |i| i+1 }      # [2,3,4]
        [1,2,3].map(&->(n){ n+1 })  # [2,3,4]
        [1,2,3].collect { |i| i+1 } # [2,3,4]
    ```
    - `&`: `to_proc` operator that convert the lambda into a block that can be passed to the map method.
        - `->(n) { ... }`: **stabby lambda** that takes an argument
            - ⚠ _Lack of space is intentional_