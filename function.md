# ফাংশন

ফাংশন মুলত কিছু স্টেটমেন্টের একটি ব্লক যা একটি প্রোগ্রামে বার বার ব্যবহার করা যায় পুনরায় না লিখে। পিএইচপিতে ১০০০ এর অধিক বিল্টইন ফাংশন আছে , যেগুলো ব্যবহারের
জন্য আপনাকে শুধু সেগুলো কল করতে হবে। এছাড়াও আপনি চাইলে আপনার মনমত ফাংশন লিখে নিতে পারেন। 
যেমনঃ 
বিল্টইন ফাংশনঃ
```php
<?php
var_dump("This is .....");
```

ইউজার ডিফাইন ফাংশনঃ
```php
<?php
function sayHello($name)
{
    return "Hello {$name}!";
}
```
যেহেতু বিল্টইন ফাংশন গুলো শুধু তাদের ডকুমেন্টেশন অনুযায়ী ব্যবহার করা যায় এবং এর জন্য প্রচুর সাপোর্ট রয়েছে তাই আলোচনা সেদিকে আলোচনা না করে ইউজার ডিফাইন ফাংশন নিয়ে করছি। 

সিনট্যাক্সঃ
যেকোন ইউজার ডিফাইন ফাংশন লিখতে হলে আপনাকে নিচের সিনট্যাক্স অনুসরণ করতে হবে। 
```php
<?php
function functionName($arg1,$arg2)
{
    // কোড ব্লক 
}
```
একটি ফাংশনের নাম অবশ্যই ইউনিক হতে হবে, নাম অবশ্যই লেটার অথবা আন্ডারস্কোর (_) দিয়ে শুরু করতে হবে। নামের মধ্যখানে কোন স্পেস দেওয়া যাবে না, প্রয়োজনে আন্ডারস্কোর (_) ব্যবহার করতে হবে।
একটি ইউজার ডিফাইন ফাংশনকে কল করার আগে তাকে ডিক্লেয়ার করে নিতে হবে।  ইউজার ডিফাইন ফাংশনে আর্গুমেন্ট+রিটার্ন থাকতে পারে নাও থাকতে পারে। নিচে কিছু উদাহরন দেওয়া হল।

আর্গুমেন্ট ছাড়াঃ
```php
<?php
function functionName()
{
   echo "Hi i don't have any argument!";
}
```
এই ফাংশনটিতে  কোন আর্গুমেন্ট নেই। অর্থাৎ একে কল করার সময় কোন আর্গুমেন্ট পাস করাতে হবে না। অনেকটা এই রকম করে  `functionName();`

আর্গুমেন্ট সহঃ
```php
<?php
function functionName($arg1,$arg2)
{
   echo $arg1;
   echo $arg2;
}
```
এই ফাংশনটিতে দুইটি আর্গুমেন্ট আছে ($arg1,$arg2) , অর্থাৎ এই ফাংশনটিকে কল করতে হলে ফাংশনের মধ্যে এই দুইটি আর্গুমেন্ট পাস করাতে হবে। অনেকটা এই রকম করে  `functionName('This is arg 1','This is 2');`

রিটার্ন সহঃ
```php
<?php
function functionName($arg1,$arg2)
{
   return $arg1.$arg2;
}
```
পুর্বে ব্যবহারিত  ইউজার ডিফাইন ফাংশনগুলোতে কোন ডাটা রিটার্ন করা হয় নি , শুধু সরাসরি ইকো করা হয়েছে। যদি কোন ইউজার ডিফাইন ফাংশন থেকে প্রাপ্ত ডাটা কোন ভ্যারিয়েবলে সংরক্ষণের প্রয়োজন হয় তখন ফাংশন থেকে ডাটা রিটার্নের প্রয়োজন হয়। তখন `return` ব্যবহার করে ডাটা রিটার্ন করা হয়।  ইউজার ডিফাইন ফাংশনে ডাটা রিটার্ন করলে অনেক সুবিদা পাওয়া যায়। যেমন আপনি চাইলে ডাটাকে ইকো করতে পারেন `echo functionName($arg1,$arg2);`,আবার চাইলে এটাকে ভ্যারিয়েবলে রাখতে পারেন অন্য কাজে ব্যবহারের জন্য `$myVar = functionName($arg1,$arg2);`। আপনি চাইলে এরে / অবজেক্ট / ভ্যারিয়েবল / রেফারেন্স রিটার্ন করতে পারেন।

রেফারেন্স সহ রিটার্নঃ
```php
<?php
function &returns_reference()
{
    return $someref;
}
$newref =& returns_reference();
?>
```
[উদাহরনটি পিএইচপি ম্যানুয়াল থেকে নেওয়া]

ভ্যারিয়েবল ফাংশনঃ
অনেক সময় কোন ফাংশনকে ভ্যারিয়েবলের মাধ্যমে কল করা হয়ে থাকে, এই পদ্ধতিকে ভ্যারিয়েবল ফাংশন বলা হয়ে থাকে।
যেমনঃ
```php
<?php
function foo() {
    echo "In foo()<br />\n";
}

function bar($arg = '')
{
    echo "In bar(); argument was '$arg'.<br />\n";
}

// This is a wrapper function around echo
function echoit($string)
{
    echo $string;
}

$func = 'foo';
$func();        // This calls foo()

$func = 'bar';
$func('test');  // This calls bar()

$func = 'echoit';
$func('test');  // This calls echoit()
?>
```
[উদাহরনটি পিএইচপি ম্যানুয়াল থেকে নেওয়া]


** নোটঃ ইউজার ডিফাইন ফাংশনগুলোকে একটি ফাইলে রাখা বেস্ট প্রাকটিস হিসাবে গন্য করা হয়। এতে একই নামের ফাংশন দু/বেশি বার ডিক্লেয়ার হওয়ার সম্ভবনা থাকে না। এই ফাইলটিকে `requere_once 'file.php';` ব্যবহার করে অন্য ফাইলে এড করতে হয়। 