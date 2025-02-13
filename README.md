# <a href="https://mirage-joggers-141.notion.site/OOP_PHP-18f4e5b8ea4a80ea8773ea3a2d5ab267?pvs=4">Notion</a>
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
    
    **`$this`** is a reserved keyword in PHP that refers to the calling object.
    
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
    - We can access a constant inside class by using  `self` keyword the scope resolution operator (`::`) followed by the constant name
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
    

# Self  **`*VS*`** $this

- 
    - `self` ⇒ refers to current class and access static members ( constant ) ,don’t need $ because it is not represent variable but represent class construction
    - `$this` ⇒ refers to current object , access non static members

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
    

# **Polymorphism**

- describes pattern in oop in which classes have different functionality while sharing common interface
    - interface ⇒ has methods have no implementation, have no properties
    - Interfaces are declared with the `interface` keyword
    - To implement an interface, a class must use the `implements` keyword
    
    ```php
    **<?php
    interface Device{
      public function say_hello();
    }
    
    class Apple implements Device{
    // we must use say_hello function 
       public function say_hello(){  // if i don't use it will generate error
         echo 'Hello Iphone<br>';
       }
    }
    
    class Sony implements Device{
       public function say_hello(){
         echo 'Hello Sony<br>';
       }
    }
    
    $app=new Apple();
    $app->say_hello();
    
    $sony=new Sony();
    $sony->say_hello();**
    
    ```
    

# **Interfaces *vs*  Abstract Classes**

- Interface are similar to abstract classes( can’t create object from ). The differences between interfaces and abstract classes are:
    - Interfaces cannot have properties, while abstract classes can
    - All interface methods must be public, while abstract class methods is public or protected
    - All methods in an interface are abstract, so they cannot be implemented in code and the abstract keyword is not necessary
    - Classes can implement an interface while inheriting from another class at the same time
    - class can implement more than one interface but can’t extend more than 1 class

# **Visibility Markers**

- **public-private-protected**
    - `public` - the property or method can be accessed from everywhere. This is default if i don’t determine the visibility.
    - `protected` - the property or method can be accessed within the class and by classes derived from that class
    - `private` - the property or method can ONLY be accessed within the class

# Magic Methods

- Methods with a special name start with double underscore `__`
    1. `__construct()` :  
        - this function automatically called when you create an object from a class ,
        - can be inherited.
        - A constructor allows you to initialize an object's properties upon creation of the object.
        
        ```php
        **<?php
        class Device{
          public $space;
          public function __construct($sp){
              $this->space=$sp;
              echo 'object is created<br>';
          }
        }
        $app=new Device('32GB');**
        ```
        
    2. `__destruct()` :
        - A destructor is called when the object is destructed or the script is stopped or exited.
        - don’t take arguments
        
        ```php
        **<?php
        class Device{
          public $space;
          public function __construct($sp){
              $this->space=$sp;
              echo 'object is created<br>';
          }
        
          public function __destruct(){
            echo 'object is destroyed<br>';
        }
        }
        $app=new Device('32GB');**
        
        ```
        
    3. `__call()` :
        - method is invoked automatically when a non-existing method or inaccessible method is called
        - can be used to achieve overloading
        - accept two parameters ⇒ method name  and its parameters
        
        ```php
        **<?php
        class Device{
          public function hello($user){
              echo 'hello'.$user.'<br>';
          }
        public function __call($method,$params){
          echo 'Function ( ' .$method .' ) not exist or not accessible<br>';
          print_r($params);
        }
        }
        $app=new Device();
        $app->hi("mariam");  // output Function hi not exist or not accessible
        $app->say_hello("mariam");// output Function say_hello not exist or not accessible
        
        ///////////////////////  overloading  /////////////////////////////////
        
        class shape{
           public function __call($fun_name,$params){
              if($fun_name=='area'){
               $cnt=count($params);
               switch($cnt){
                 case 1:
                    $a= 3.14*$params[0]*$params[0];
                    echo 'area of circle ='.$a.'<br>';
                    break;
                 case 2:
                  $a=  $params[0]*$params[1];
                  echo 'area of rectangle ='.$a.'<br>';
                    break;
               }
        
              }
           }
        }
        
        $obj=new shape();
         $obj->area(5,6); // area of rectangle =30
         $obj->area(5); // area of circle =78.5**
        
        ```
        
    4. `__get()` & `__set()` :
        - are used to intercept calls to get or set the value of inaccessible properties of an object.
        - They allow you to define custom behaviors when getting or setting the value of a property that is not directly accessible.
        - `__get( )` ⇒ accept one parameter.
        - `__set( )` ⇒ accept two parameters.
        
        ```php
        **<?php
        class Device{
         private $pass;
         public $space;
         public function __get($p){
          echo 'This property '.$p.' is not exist or not accessible<br>';
         }
         public function  __set($p,$val){
          echo 'This proprety '.$p.' is not exist or not accessible<br>';
          echo 'You can not assign this value '.$val.' to this property<br>';
         }
        }
        $app=new Device();
        $app->pass; // access private property
        $app->color; // access property not exist
        $app->pass='123';// assign private property
        $app->color='red'; //assign property not exist**
        ```
        
    5. `colne & __clone()`  :
        - Taking copy of object in php works by reference.
        - The `clone` keyword is used to create a copy of an object to prevent referencing                 ( shallow copy ).
        
        keyword `clone` EX:
        
        ```php
        **<?php
        class User{
         public $name="menna";
        }
        $main=new User();
        $copy_by_ref=$main; // copy by reference
        $copy_by_val=clone $main; // copy by value
        $main->name="mariam"; // will change in main & copy_by_ref but copy_by_val not change
        echo '<pre>';
        print_r($main);
        echo '</pre>';
        
        echo '<pre>';
        print_r($copy_by_ref);
        echo '</pre>';
        
        echo '<pre>';
        print_r($copy_by_val);
        echo '</pre>';
        
        $copy_by_val->name="malak"; // will  change in copy_by_val only
        $copy_by_ref->name="maro";  // will change in copy_by_ref and main
        
        echo '<pre>';
        print_r($main);
        echo '</pre>';
        
        echo '<pre>';
        print_r($copy_by_ref);
        echo '</pre>';
        
        echo '<pre>';
        print_r($copy_by_val);
        echo '</pre>';**
        
        ```
        
    
    magic method `__clone( )` :
    
    - in shallow copy If any of the properties was a reference to another variable or object, then only the reference is copied. Objects are always passed by reference, so if the original object has another object in its properties, the copy will point to the same object
    - This behavior can be changed by creating a `__clone()` method in the class ( deep copy )
    
    ```php
    **<?php
    class address {
      public $city;
      public $code;
      public function set_address($ct,$co){
        $this->city=$ct;
        $this->code=$co;
      }
    }
    class User{
     public $name="menna";
     public $add;
     // creating object inside class  if i don't use construct will generate error
     public function __construct(){
      $this->add=new address();
     }
     public function set_name($na){
      $this->name=$na;
     }
     public function __clone(){
      $this->add=new address();
      $this->name="menna";
     }
    }
    
    $user1 =new User();
    $user1->set_name("mariam");
    $user1->add->set_address("Mansoura",'050');
    echo '<pre>';
    print_r($user1);
    echo '</pre>';
    
    // user2 will take the values in the original class not in user1 
    $user2=clone $user1;
    echo '<pre>';
    print_r($user2);
    echo '</pre>';
    
    // user1 only will change
    $user1->set_name("maro");
    $user1->add=new address();
    $user1->add->set_address("Mahala",'020');
    echo '<pre>';
    print_r($user1);
    echo '</pre>';
    echo '<pre>';
    print_r($user2);
    echo '</pre>';**
    ```
    

# **Static Properties and Methods**

- static properties and methods in class can be accessed from outside class without create an object from the class by using `class_name::$property`  or  `class_name::method_name()`
    - inside static methods you can’t use `$this`
    - if i create an object from the class i can’t access static property but static methods can be accessed
    - static properties keep their values for the duration of the script
    
    ```php
    **<?php
    class User{
       public static $name;
       public static function say_hello(){
        echo 'Hello<br>';
       }
    }
    User::say_hello();
    User::$name="mariam";
    echo User::$name;
    User::$name="menna";
    // using object
    $obj=new User();
    $obj->say_hello(); // work
    $obj->name="menna"; // error
    echo User::$name; // output menna (the last value)**
    ```
    

# **Methods Chaining**

- To use Methods Chaining the method must return `$this`
    
    ```php
    **<?php
    class chain{
    
    public function say_hello(){
       echo "Hello ";
       return $this;
    }
    public function user($u){
      echo $u;
      return $this;
    }
    public function oop(){
       echo ' in oop';
       return $this;
    }
    }
    
    $chaining=new chain();
    $chaining->say_hello()->user('mariam')->oop();**
    ```
    
    ## How to chain static methods 🤔
    
    - To use Methods Chaining the static method must return `self::class`
    
    ```php
    **<?php
    class chain{
    
    public static function say_hello(){
       echo "Hello ";
       return self::class;
    
    }
    public static function user($u){
      echo $u;
      return self::class;
    }
    
    public static function oop(){
       echo ' in oop<br>';
       return self::class;
    }
    }
    // using object
    $obj=new chain();
    $obj->say_hello()::user('mariam')::oop(); // or  $obj::say_hello()::user('mariam')::oop();
    // using class name
    chain::say_hello()::user('menna')::oop();**
    ```
    
    ## Can i  chain using object and arrow chaining ( → )? 🤔
    
        **YES** 🥳
    
    ```php
    **<?php
    class chain{
    
    public static function say_hello(){
       echo "Hello ";
       // to allow chaining
       return self::class;
    
    }
    public static function user($u){
      echo $u;
      return self::class;
    }
    
    public static function oop(){
       echo ' in oop<br>';
       return self::class;
    }
    // To chain using object and -> 
    public function callSayHello() {
    // use self:: to access static members
       self::say_hello();
       return $this;
    }
    
    public function callUser($u) {
       self::user($u);
       return $this;
    }
    
    public function callOop() {
       self::oop();
       return $this;
    }
    }
    
    $obj = new Chain();
    
    $obj->callSayHello()->callUser('mariam')->callOop();**
    ```
    

# **Traits**

- A mechanism for code reuse in single inheritance language such as php( can’t extend more than one class)
    - you can’t extend or implement
    - you can’t create object from it
    - it support class not replace it
    - have properties and methods
    
    ```php
    **<?php
    
    // create trait
    trait faceDetect{  
        public function faceID(){
            echo 'Hello from Face Detect<br>';
        }
    }
    
    trait fingerTouch{ 
        public function finger_Touch(){
            echo 'Hello from finger Touch<br>';
        }
    }
    
    class Iphone{
       // how to use trait
        use faceDetect;
        use fingerTouch;
    }
    $phone = new Iphone(); 
    
    $phone->faceID();
    $phone->finger_Touch();
    echo "<pre>";
    print_r($phone);
    echo "</pre>";**
    ```
    
    ## trait in another trait
    
    ```php
    **<?php
    
    // create trait
    trait faceDetect{  
        public function faceID(){
            echo 'Hello from Face Detect<br>';
        }
    }
    
    trait fingerTouch{ 
        public function finger_Touch(){
            echo 'Hello from finger Touch<br>';
        }
    }
    trait allFeatures{ // trait in another one
       use faceDetect, fingerTouch;
    
    }
    class Iphone{
       // how to use trait
        use faceDetect;
        use fingerTouch;
    }
    class sony{
       use allFeatures;
    }
    $phone1 = new Iphone(); 
    $phone1->faceID();
    $phone1->finger_Touch();
    echo "<pre>";
    print_r($phone1);
    echo "</pre>";
    // the same output like phone1
    $phone2 = new sony(); 
    $phone2->faceID();
    $phone2->finger_Touch();
    echo "<pre>";
    print_r($phone2);
    echo "</pre>";**
    ```
    
    ## Trait has higher priority than class
    
    ```php
    **<?php
    trait hello{
       public function say_hello(){
       echo 'hello from trait<br>';
       }
    }
    class Iphone{
      
        public function say_hello(){
          echo 'hello from class<br>';
          }
    }
    class sony extends Iphone{
       use hello;
    }
    
    $phone2 = new sony(); 
    $phone2->say_hello();// hello from trait**
    
    ```
    
    ## if i use two traits have the same method this will generate error How to fix it? 🤔
    
    ```php
    **<?php
    trait trait1{
       public function say_hello(){
       echo 'hello from trait 1<br>';
       }
    }
    trait trait2{
       public function say_hello(){
          echo 'hello from trait 2<br>';
          }
    }
    class Iphone{
        /* use trait1,trait2; ====> error
           how to fix error
           use trait1,trait2{
           trait_name :: function_name 'insteadof'(keyword) another_trait_name;
           }
        */
          use trait1,trait2{
          trait1::say_hello insteadof trait2;
          trait2::say_hello as hello;   // to use trait2 to i give the method alias (another name)
          } 
     
    }
    
    $phone2 = new Iphone(); 
    $phone2->say_hello(); // hello from trait 1
    $phone2->hello(); // hello from trait 2**
    
    ```
    

# **Namespace**

- Namespaces are qualifiers that solve two different problems:
    1. They allow for better organization by grouping classes that work together to perform a task
    2. They allow the same name to be used for more than one class
    
    ```php
    **// file
    // sony.php
    <?php
    namespace sony;
    class create_phone{
    
      public function say_hello(){
        echo 'Hello from sony<br>';
      }
    
    }**
    
    ```
    
    ```php
    **// file
    // iphone.php
    <?php
    // I can create two name space in the same file but not the best practice 
    namespace iphone\hardware{
    class create_phone{
    
      public function say_hello(){
        echo 'Hello from iphone hardware<br>';
      }
    }
    }
    namespace iphone\software{
        class create_phone{
    
            public function say_hello(){
              echo 'Hello from iphone software<br>';
            }
          
          }
    }**
    
    ```
    
    ```php
    **// file
    //LG.php
    <?php
    namespace LG;
    class create_phone{
    
      public function say_hello(){
        echo 'Hello from LG<br>';
      }
    
    }**
    
    ```
    
    ```php
    **<?php
    require 'iphone.php';
    require 'LG.php';
    require 'sony.php';
    // i can give alias to namespace 
    // syntax [use keyword] [namespace] [as keyword] [alias name]
    use iphone\hardware as ih;
    
    // use namespapce\class name => to access class in iphone.php
    
    $obj1=new ih\create_phone();
    $obj11=new iphone\software\create_phone();
    $obj2=new LG\create_phone();
    $obj3=new sony\create_phone();
    // Hello from iphone hardware
    $obj1->say_hello();
    //  Hello from iphone software
    $obj11->say_hello(); 
    // Hello from LG
    $obj2->say_hello();
    // Hello from sony
    $obj3->say_hello();**
    ```
    

# **Autoload Classes**

- instead of require every file in in index.php like that
    
    ```php
    **require 'iphone.php';
    require 'sony.php';
    require 'LG.php';**
    ```
    
    **we can do it to auto load classes using** **`spl_autoload_register( )` function**
    
    - create folder and create in it all classes each class in file and name the file same name of class in this file
        
    ![image](https://github.com/user-attachments/assets/24bbcd0d-8fb4-4287-8fee-c8952bdecaa6)

        
    
    ```php
    **<?php
    // spl_autoload_register(function) i can pass ordinary function or  anonymous function or arrow function
    // anonymous function
    spl_autoload_register(function ($class){  
       require 'classes/'.$class.'.class.php';
    });
    /////////////////////////////////////////////////////
    /*
    arrow function
    
    spl_autoload_register(fn ($class)=>
       require 'classes/'.$class.'.class.php'
    );
    
    /////////////////////////////////////////////////////
    ordinary function
    
    function Classs($class){
        return require 'classes/'.$class.'.class.php';
    }
    spl_autoload_register("Classs"
    );
    
    */
    
    $p1=new iphone();
    $p2=new sony();
    $p3=new LG();
    $p1->say_hello();  //Hello from iphone
    $p2->say_hello();  // Hello from sony
    $p3->say_hello();  // Hello from LG**
    ```
