# OOP_PHP
# What is OOP?

- OOP ( Object Oriented Programming ):
    - a style of codeing that allows developers to group similar tasks into classes
    - use classes to organize the data and structure of an application
    - depend on **"Don't Repeat Yourself" (DRY)** principle is about reducing the repetition of code

# Why we should use OOP?

- 
    - more security
    - more dynamic
    - more clean

# What are class and object?

- 
    
    class is a template for objects, and an object is an instance of a class
    
    class ⇒ is a blueprint that you can create an object from , has properties and methods,
    
                   variable inside class ⇒ property
    
    ```php
    <?php
    /*
     How to cearte class
    class class_name {
        $properity1;
        $properity2="OOP"; // default value all object take this default value if not be changed
        
    }
    // How to create object
    $obj = new class_name(); 
    // How to change property
    $obj->properity1='Hello';
    
    */
    
    // EX
    
    **class Apple_Device{
      // properties
      public $ram; // (public-private-protected) visibility markers 
      var $inch; // var = public
      public $space='32GB';// default value
    
    }
    
    // create object
    $iphone7= new Apple_Device(); // $iphone7 and $iphone11 have the same property  but may have diffrent values
    $iphone11= new Apple_Device();
    // properties have no values 
    echo '<pre>';     
    print_r($iphone7);
    echo '</pre>';
    
    echo '<pre>';
    print_r($iphone11);
    echo '</pre>';
    
    // change properties 
    $iphone7->ram='8GB';
    $iphone7->inch='5inch';
    $iphone7->space= '32GB';
    $iphone7->color='gold'; // property color not exist in class but i can add to this object only
    
    $iphone11->ram='16GB';
    $iphone11->inch='10inch';
    $iphone11->space= '128GB';
    $iphone11->colour='white'; // property colour not exist in class but i can add to this object only
    
    // after assign values to properties
    echo '<pre>';
    print_r($iphone7);
    echo '</pre>';
    
    echo '<pre>';
    print_r($iphone11);
    echo '</pre>';**
    
    ```
    

# Class Methods

- 
    
    Functions inside classes ⇒ Methods
    
    ```php
    <?php
    /*
    How to create method
    class class_name {
     visibility_ marker function fun_name(){
         implementation
     }
    }
    */
    // EX
    
    **class Apple_Device{
      // properties
      public $ram; // (public-private-protected) visibility markers 
      var $inch; // var = public
      public $space='32GB';// default value
    
      public function HomePressed(){ // method
        echo 'Hello';
      }
    
    }
    // How to access function
    // 1- create object from class
    //2- access method
    
    $iphine6= new Apple_Device();
    $iphone6->HomePressed();**
    
    ```
    

# **Pseudo Variable $this**

- 
    
    **$this** is a reserved keyword in PHP that refers to the calling object.
    
    ```php
    **<?php
    class Apple_Device{
      public $owner_name;
      public $ram;
      var $inch; 
      public $space;
    
      public function SetOwnerName($owner){ // method with Arguments
        if(strlen($owner)<3)
          echo 'Owner can not be less than 3 chars<br>';
        else{
            $this->owner_name=$owner;
            echo 'Owner Name has been set <br>';
        }
         
      }
        
    
    }
    
    // create object
    $iphone7= new Apple_Device(); // $iphone7 and $iphone11 have the same property  but may have diffrent values
    $iphone11= new Apple_Device();
    
    // change properties 
    $iphone7->ram='8GB';
    $iphone7->inch='5inch';
    $iphone7->space= '32GB';
    // send owner name as a parameter
    $iphone7->SetOwnerName('Ma');  // output => Owner can not be less than 3 chars
    
    $iphone11->ram='16GB';
    $iphone11->inch='10inch';
    $iphone11->space= '128GB';
    // send owner name as a parameter
    $iphone11->SetOwnerName('Mariam');   // output => OK**
    
    ```
    

# **Class Constants**

- 
    - A class constant is declared inside a class with the `const` keyword.
    - A constant cannot be changed once it is declared.
    - We can access a constant inside class by using   self   keyword the scope resolution operator (`::`) followed by the constant name
    - We can access a constant from outside the class by using the class name  or the object name followed by the scope resolution operator (`::`) followed by the constant name
    
    ```php
    **<?php
    class Apple_Device{
      public $owner_name;
      public $ram;
      var $inch; 
      public $space;
      const NAME_LEN=5;  // best practice upper_case letter
    
      public function SetOwnerName($owner){ // method with parameters
        // How to access const inside class
        if(strlen($owner)<self::NAME_LEN)  
          echo 'Owner can not be less than '.self::NAME_LEN.' chars<br>';
        else{
            $this->owner_name=$owner;
            echo 'Owner Name has been set <br>';
        }
         
      }
    }
    
    // create object
    $iphone7= new Apple_Device(); 
    
    // change properties 
    $iphone7->ram='8GB';
    $iphone7->inch='5inch';
    $iphone7->space= '32GB';
    $iphone7->SetOwnerName('Ma');  // output => Owner can not be less than 3 chars
    // How to access const outside class
    // 1- by using class name
     echo Apple_Device::NAME_LEN.'<br>';
    // 2- by using object name
    echo $iphone7::NAME_LEN.'<br>';**
    
    ```
    

# Self  VS  $this

- 
    - self ⇒ refers to current class and access static members ( constant ) ,don’t need $ because it is not represent variable but represent class construction
    - $this ⇒ refers to current object , access non static members

# **Methods with Arguments**

- 
    
    ```php
    **<?php
    class Apple_Device{
     
      public $ram;
      var $inch; 
      public $space;
      
      public function change_prop($r ,$in ,$sp){
        $this->ram=$r;
        $this->inch=$in;
        $this->space=$sp;
      }
    }
    
    // create object
    $iphone7= new Apple_Device(); 
    
    // change properties 
    $iphone7->change_prop('4GB','16in','32GB');
    
    echo '<pre>';
    var_dump($iphone7);
    echo '</pre>';**
    
    ```
    

# Encapsulation

- Encapsulation ⇒ "information hiding”
    
    ```php
    **<?php
    class Apple_Device{
     
      public $ram;
      var $inch; 
      public $space;
      private $lock;  // private property can't access outside class
      
      public function change_prop($r ,$in ,$sp){
        $this->ram=$r;
        $this->inch=$in;
        $this->space=$sp;
      }
      public function change_lock($lo){
        $this->lock= sha1($lo);      // The sha1() function calculates the SHA-1 hash of a string.
                                     // The sha1() function uses the US Secure Hash Algorithm 1.
      }
    }
    
    // create object
    $iphone7= new Apple_Device(); 
    
    // change properties 
    $iphone7->change_prop('4GB','16in','32GB');
    $iphone7->change_lock('2612');
     // $iphone7->lock="2612";  this give error
     
    echo '<pre>';
    var_dump($iphone7);
    echo '</pre>';**
    
    ```
    

# **Inheritance**

- 
    - Inheritance in OOP = When a class derives from another class.
    - The child class will inherit all the public and protected properties and methods from the parent class. In addition, it can have its own properties and methods.
    - An inherited class is defined by using the `extends` keyword.
    
    ```php
    **<?php
    class Apple_Device{
     
      public $ram;
      var $inch; 
      public $space;
      public $color;
      private $lock;  // private property can't access outside class
    
      
      public function change_prop($r ,$in ,$sp){
        $this->ram=$r;
        $this->inch=$in;
        $this->space=$sp;
      }
      public function change_lock($lo){
        $this->lock= sha1($lo);      // The sha1() function calculates the SHA-1 hash of a string.
                                     // The sha1() function uses the US Secure Hash Algorithm 1.
      }
    }
    
    class Sony extends Apple_Device{   // this class inherit all properties and methods in class apple
       public $camera;
        //   public function change_prop($r ,$in ,$sp, $ca){   this generate error because is not similar to function in apple class 
        //   $this->ram=$r;
        //   $this->inch=$in;
        //   $this->space=$sp;
        //   $this->camera=$ca
        //  }
       public function say_hi(){
        echo 'Hello Sony';
       }
    }
    
    // create object
    $iphone7= new Apple_Device(); 
    
    // change properties 
    $iphone7->change_prop('4GB','16in','32GB');
    $iphone7->change_lock('2612');
     // $iphone7->lock="2612";  this give error
     $sony1= new Sony();
     $sony1->change_prop('4GB','16in','32GB');
     $sony1->change_lock('2612');
    echo '<pre>';
    var_dump($iphone7);
    echo '</pre>';
    
    echo '<pre>';
    var_dump($sony1);
    echo '</pre>';**
    
    ```
    

# **Inheritance Override**

- redefining the methods (use the same name) in the child class ( change implementation ).
    
    ```php
    **<?php
    class Apple_Device{
    
      public function say_hello(){
        echo 'Hello Iphone<br>';
       }
    }
    class Sony extends Apple_Device{   // this class inherit all properties and methods in class apple
       public function say_hello(){
        echo 'Hello Sony<br>';
       }
    }
    // create object
    $iphone7= new Apple_Device(); 
    $sony1= new Sony();
    $iphone7->say_hello();
    $sony1->say_hello();**
    
    ```
    

# **Inheritance Final Keyword**

- The `final` keyword can be used to prevent class inheritance or to prevent method overriding.
    
    ```php
    **<?php
    final class mobile {
      // some code
    }
    // will result in error
    class iphone extends mobile {
      // some code
    }
    ?>
    
    ////////////////////   OR  /////////////////////
    
    <?php
    class class mobile {
      final public function hello() {
        // some code
      }
    }
    
    class iphone extends mobile {
      // will result in error
      public function hello() {
        // some code
      }
    }
    ?>** 
    ```
    

# Abstraction

- An abstract class or method is defined with the `abstract` keyword
    - Cannot create object from it
    - abstract class is a structure for other classes that inherit from it
    - it has methods and props
    - it has abstract methods and non-abstract methods
    - abstract methods ⇒ cannot have body ⇒ if you create abstract function you have to use it in inherit class
    - non-abstract methods ⇒ have body but it is not the best practice
    
    ```php
    **<?php
    
    abstract class makeDevice{
        abstract public function testPerformance(); //  abstract function
        abstract public function veriUser(); 
        abstract public function sayHello($n); 
    } 
    class AppelDevice extends makeDevice
    {
        public $user;
        public function testPerformance(){ // must use abstract function
            echo "Performance 100%";
        }
    
        public function veriUser(){
            echo "Verified";
        }
        public function sayHello($user){
            echo "Hello $user";
        }
    
    }
    
    $iphone = new AppelDevice();
    $iphone->sayHello("mariem");
    
    echo "<pre>";
    print_r($iphone);
    echo "</pre>";**
    ```
