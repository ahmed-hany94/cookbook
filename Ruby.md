# Ruby

## Table of Contents:
- [Types](#types)
- [Type Conversions](#type-conversions)
- [Array](#array)
- [Hash](#hash)
- [Class](#class)

## Types
- Numeric Types:
    - **Integer**: Represents whole numbers (e.g., 1, 42).
    - **Float**: Represents floating-point numbers with decimal parts (e.g., 3.14).
- String Type:
    - **String**: Represents sequences of characters (e.g., "hello").
- Symbol Type:
    - **Symbol**: Represents names and strings in an immutable form (e.g., :symbol).
- Boolean Type:
    - **true** and **false**: Represent boolean values.
- Array Type:
    - **Array**: Represents an ordered collection of elements.
- Hash Type:
    - **Hash**: Represents an unordered collection of key-value pairs.
- Nil Type:
    - **nil**: Represents the absence of a value or a null value.
- Range Type:
    - **Range**: Represents a range of values (e.g., 1..5 or 'a'..'z').
- Regexp Type:
    - **Regexp**: Represents regular expressions.
- Class Type:
    - **Class**: Represents a class in Ruby.
- Module Type:
    - **Module**: Represents a module in Ruby.
- Object Type:
    - **Object**: The base class for all Ruby objects.
- Proc and Lambda Types:
    - **Proc** and **Lambda**: Represent blocks of code that can be stored in variables.
- File Type:
    - **File**: Represents files and file operations.

## Type Conversions
```ruby
    1.to_s                   # "1"
    5.to_s(2)                # "101"
    15.to_s(16)              # "f"
    "1".to_i                 # 1
    "A".chr                  # 65
    255.chr(Encoding::UTF_8) # "ÿ"
    1.to_f                   # 1.0
    {key: 'value'}.to_a      # [[:key, "value"]]
    [[:key, 'value']].to_h   # {:key=>"value"}
    "1".to_sym               # :"1"
    "1".intern               # :"1"
    1.to_r                   # (1/1)
    1.to_c                   # (1+0i)
```

## Array
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
        (0..3).to_a                             # [0,1,2,3]
        (0..3).map{|i| i}                       # [0,1,2,3]
        Array.new(3, 0)                         # [0,0,0]
        Array.new(2){Array.new(2,0)}            # [[0, 0], [0, 0]]
        (Array.new(2){Array.new(2,0)}).flatten  # [0, 0, 0, 0]
        (Array.new(2){Array.new(2,0)}).flatten! # [0, 0, 0, 0]
    ```
- ### sort an array
    ```ruby
        [3,2,1].sort          # [1,2,3]
        [3,2,1].sort!         # [1,2,3]
        [1,2,3].sort.reverse  # [3,2,1]
        [1,2,3].sort!.reverse # [3,2,1]
    ```
- ### unique
    ```ruby
        [3,2,1].uniq
        [3,2,1].uniq!
    ```
- ### concat
    ```ruby
        [1,2,3] << 4    # [1,2,3,4]
        [1,2,3] << "4"  # [1,2,3,"4"]
        [1,2,3] << true # [1,2,3,true]
        [1,2,3]+[4,5,6] # [1,2,3,4,5,6]
    ```
- ### slicing
    ```ruby
        [1,2,3,4,5,6].take(3)      # [1,2,3]
        [1,2,3,4,5,6].drop(3)      # [4,5,6]
        [1,2,3,4,5,6].slice(2, 3)  # [3,4,5]
        [1,2,3,4,5,6].slice(4, 3)  # [5,6]
    ```
- ### filtering
    ```ruby
        [1,2,3,4,5,6].select{|i| i.even?}    # [2,4,6]
        [1,2,3,4,5,6].select(&:even?)        # [2,4,6]
        [1,2,3,4,5,6].reject{|i| i.odd?}     # [2,4,6]
        [1,2,3,4,5,6].keep_if{|i| i.even?}   # [2,4,6]
        [1,2,3,4,5,6].delete_if{|i| i.even?} # [2,4,6]
    ```
- ### algebriac operations
    ```ruby
        [1,2,3].intersect?([1,2,4])               # true
        [1,2,3].intersection([1,2,4])             # [1,2]
        [1,2,3].union([1,2,4])                    # [1,2,3,4]
        [1,2,3].difference([1,2,4])               # [3]
        [1,2,3] - [1,2,4]                         # [3]
        ([1,2,3] - [1,2,4]) + ([1,2,4] - [1,2,3]) # [3,4]
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

## Hash
### Sort
```ruby
    {"b"=> 3,"a"=> 1,"c"=> 2}.sort.to_h # {"a"=>1,"b"=>3,"c"=>2}
    {b:3,a:1,c:2 }.sort.to_h            # {:a=>1,:b=>3,:c=>2}
    {"b"=> 3,"a"=> 1,"c"=> 2}.sort_by{ |key, _| key }.reverse.to_h
    # {"c"=>2,"b"=>3,"a"=>1}
    {b:3,a:1,c:2 }.sort_by { |key, _| key }.reverse.to_h
    # {:a=>1,:b=>3,:c=>2}
    {"b"=> 3,"c"=> 1,"a"=> 2}.sort_by { |_, value| value }.to_h
    # {"c"=>1,"a"=>2,"b"=>3}
    {b:3,c:1,a:2 }.sort_by { |_, value| value }.to_h
    # {:c=>1,:a=>2,:b=>3}
    {"b"=> 3,"c"=> 1,"a"=> 2}.sort_by { |_, value| value }.reverse.to_h
    # {"b"=>3,"a"=>2,"c"=>1}
    {b:3,c:1,a:2 }.sort_by { |_, value| value }.reverse.to_h
    # {:b=>3,:a=>2,:c=>1}
```

## Class
```ruby
class A
  def initialize(name)
    @name = name
  end

  def a
    puts "@name = #{@name}"
  end
end

a = A.new("a")
a.a              # @name = a
```