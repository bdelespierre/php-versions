# PHP New Features CheatSheet

The neatest __PHP__ cheatsheet around. Trust me, I'm a random __Gist__ from __GitHub__ :octocat:

+ PHP 7
   + [PHP 7.2](#php-72) - _2017_
   + [PHP 7.1](#php-71) - _2016_
   + [PHP 7.0](#php-70) - _2015_
+ PHP 5
   + [PHP 5.6](#php-56) - _2014_
   + [PHP 5.5](#php-55) - _2013_
   + [PHP 5.4](#php-54) - _2012_
   + [PHP 5.3](#php-53) - _2010_
+ [Glossary](#glossary)
+ [Credits](#credits)

## PHP 7.2

Initial Release __2017-11-30__ : [New object type](#new-object-type), [Abstract method overriding](#abstract-method-overriding), [Sodium is now a core extension](#sodium-is-now-a-core-extension), [Password hashing with Argon2](#password-hashing-with-argon2), [Extended string types for PDO](#extended-string-types-for-pdo), [Additional emulated prepares debugging information for PDO](#additional-emulated-prepares-debugging-information-for-pdo), [Support for extended operations in LDAP](#support-for-extended-operations-in-ldap), [Address Information additions to the Sockets extension](#address-information-additions-to-the-sockets-extension), [Parameter type widening](#parameter-type-widening), [Allow a trailing comma for grouped namespaces](#allow-a-trailing-comma-for-grouped-namespaces), [proc_nice() support on Windows](#proc_nice-support-on-windows), [pack() and unpack() endian support](#pack-and-unpack-endian-support), [Enhancements to the EXIF extension](#enhancements-to-the-exif-extension), [New features in PCRE](#new-features-in-pcre), [SQLite3 allows writing BLOBs](#sqlite3-allows-writing-blobs), [Oracle OCI8 Transparent Application Failover Callbacks](#oracle-oci8-transparent-application-failover-callbacks), [Enhancements to the ZIP extension](#enhancements-to-the-zip-extension)

### [New object type](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.object-type)
```PHP
function (object $obj) { /* ... */ }
```

### [Abstract method overriding](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.abstract-method-overriding)
```PHP
abstract class A
{
    abstract function test(string $s);
}
abstract class B extends A
{
    // overridden - still maintaining contravariance for parameters and covariance for return
    abstract function test($s) : int;
}
```

### [Sodium is now a core extension](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.sodium)
```PHP
$secret_key = sodium_crypto_secretbox_keygen();
$message = 'Sensitive information';
$nonce = random_bytes(SODIUM_CRYPTO_SECRETBOX_NONCEBYTES);
$encrypted_message = sodium_crypto_secretbox($message, $nonce, $secret_key);
```

### [Password hashing with Argon2](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.pws-hashing-with-argon2)
```PHP
// Argon2i with default cost factors
password_hash('password', PASSWORD_ARGON2I);

// Argon2i by name with custom cost factors
password_hash('password', PASSWORD_ARGON2I, ['memory_cost' => 1<<17, 'time_cost' => 4, 'threads' => 2]);

// The new options for the algorithm are listed as follows.
$options = [
    'memory_cost' => PASSWORD_ARGON2_DEFAULT_MEMORY_COST, // memory_cost = 1024 KiB
    'time_cost'   => PASSWORD_ARGON2_DEFAULT_TIME_COST,   // time_cost = 2
    'threads'     => PASSWORD_ARGON2_DEFAULT_THREADS,     // threads = 2
];
```

### [Extended string types for PDO](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.pdo-extended-str-types)
```PHP
$db->quote('über', PDO::PARAM_STR | PDO::PARAM_STR_NATL);
```

### [Additional emulated prepares debugging information for PDO](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.additional-emulated-prepares-debugging-info)
```PHP
$sth = $pdo->prepare("...");
$sth-;>debugDumpParams();
```

### [Support for extended operations in LDAP](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.extended-ops-in-ldap)
```PHP
```

### [Address Information additions to the Sockets extension](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.addr-info-in-sockets)
```PHP
```

### [Parameter type widening](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.param-type-widening)
```PHP
interface A
{
    public function Test(array $input);
}

class B implements A
{
    public function Test($input){} // type omitted for $input
}
```

### [Allow a trailing comma for grouped namespaces](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.trailing-comma-in-grouped-namespaces)
```PHP
use Foo\Bar\{
    Foo,
    Bar,
    Baz,
};
```

### [proc_nice() support on Windows](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.proc_nice-windows-support)
```PHP
```

### [pack() and unpack() endian support](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.pack-unpack-endian-support)
```PHP
```

### [Enhancements to the EXIF extension](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.exif-features)
```PHP
```

### [New features in PCRE](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.pcre)
```PHP
```

### [SQLite3 allows writing BLOBs](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.sqlite3)
```PHP
```

### [Oracle OCI8 Transparent Application Failover Callbacks](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.oci8)
```PHP
```

### [Enhancements to the ZIP extension](http://php.net/manual/en/migration72.new-features.php#migration72.new-features.zip)
```PHP
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-72">PHP 7.2</a></p>

## PHP 7.1

Initial Release __2016-12-01__ : [Nullable types](#nullable-types), [Void functions](#void-functions), [Symmetric array destructuring](#symmetric-array-destructuring), [Class constant visibility](#class-constant-visibility), [iterable pseudo-type](#iterable-pseudo-type), [Multi catch exception handling](#multi-catch-exception-handling), [Support for keys in list()](#support-for-keys-in-list), [Support for negative string offsets](#support-for-negative-string-offsets), [Convert callables to Closures with Closure::fromCallable()](#convert-callables-to-closures-with-closurefromcallable), [Asynchronous signal handling](#asynchronous-signal-handling)

### [Nullable types](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.nullable-types)
```PHP
function foo(): ?string {}
function foo(?string $bar) {}
```

### [Void functions](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.void-functions)
```PHP
function foo(): void {}
```

### [Symmetric array destructuring](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.symmetric-array-destructuring)
```PHP
[$a,$b] = [1,2];
foreach ([[1,2],[3,4]] as [$a,$b]);
```

### [Class constant visibility](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.class-constant-visibility)
```PHP
class Foo
{
    const A = 1;
    public const B = 2;
    protected const C = 3;
    private const D = 4;
}
```

### [iterable pseudo-type](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.iterable-pseudo-type)
```PHP
function foo(iterable $it) {}
```

### [Multi catch exception handling](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.mulit-catch-exception-handling)
```PHP
try {} catch (RuntimeException | LogicException $e) {}
```

### [Support for keys in list()](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.support-for-keys-in-list)
```PHP
list('a' => $foo, 'b' => $bar) = ['a' => 1, 'b' => 2];
foreach ([['a' => 1, 'b' => 2], ['a' => 3, 'b' => 4]] as list('a' => $foo, 'b' => $bar));
```

### [Support for negative string offsets](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.support-for-negative-string-offsets)
```PHP
echo "abc"[-1]; // c
```

### [Convert callables to Closures with Closure::fromCallable()](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.convert-callables-to-closures)
```PHP
$fn = Closure::fromCallable([Foo::class, 'barMethod']);
```

### [Asynchronous signal handling](http://php.net/manual/fr/migration71.new-features.php#migration71.new-features.asynchronous-signal-handling)
```PHP
pcntl_async_signals(true); // turn on async signals
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-71">PHP 7.1</a></p>

## PHP 7.0

Initial Release __2015-12-03__ : [Scalar type declarations](#scalar-type-declarations), [Return type declarations](#return-type-declarations), [Null coalescing operator](#null-coalescing-operator), [Spaceship operator](#spaceship-operator), [Constant arrays using define()](#constant-arrays-using-define), [Anonymous classes](#anonymous-classes), [Unicode codepoint escape syntax](#unicode-codepoint-escape-syntax), [Closure::call()](#closurecall), [Filtered unserialize()](#filtered-unserialize), [IntlChar](#intlchar), [Expectations](#expectations), [Group use declarations](#group-use-declarations), [Generator Return Expressions](#generator-return-expressions), [Generator delegation](#generator-delegation), [Integer division with intdiv()](#integer-division-with-intdiv), [Session options](#session-options), [preg_replace_callback_array()](#preg_replace_callback_array), [CSPRNG Functions](#csprng-functions), [list() can always unpack objects implementing ArrayAccess](#list-can-always-unpack-objects-implementing-arrayaccess), [Other Features](#other-features)


### [Scalar type declarations](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.scalar-type-declarations)
```PHP
function foo(string $s, int $i, float $f, bool $b) {}
```

### [Return type declarations](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.return-type-declarations)
```PHP
function foo(): array
```

### [Null coalescing operator](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.null-coalesce-op)
```PHP
$a = $b[1] ?? 2;
```

### [Spaceship operator](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.spaceship-op)
```PHP
echo 1 <=> 1; // 0
echo 1 <=> 2; // -1
echo 2 <=> 1; // 1
```

### [Constant arrays using define()](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.define-array)
```PHP
define('ARR', [1,2,3]);
```

### [Anonymous classes](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.anonymous-classes)
```PHP
$o = new class {};
```

### [Unicode codepoint escape syntax](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.unicode-codepoint-escape-syntax)
```PHP
echo "\u{aa}";
```

### [Closure::call()](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.closure-call-method)
```PHP
$fn = function() { return $this->x; };
$fn->call(new class { $x = 1 }); // 1
```

### [Filtered unserialize()](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.filtered-unserialize)
```PHP
$data = unserialize($foo, ["allowed_classes" => false]);
$data = unserialize($foo, ["allowed_classes" => [Foo::class, Bar::class]]);
```

### [IntlChar](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.intlchar)
```PHP
printf('%x', IntlChar::CODEPOINT_MAX); // 10ffff
echo IntlChar::charName('@'); // COMMERCIAL AT
var_dump(IntlChar::ispunct('!')); // bool(true)
```

### [Expectations](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.expectations)
```PHP
ini_set('assert.exception', 1);
class CustomError extends AssertionError {}
assert(false, new CustomError('Some error message'));
```

### [Group use declarations](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.group-use-declarations)
```PHP
use some\namespace\{ClassA, ClassB, ClassC as C};
use function some\namespace\{fn_a, fn_b, fn_c};
use const some\namespace\{ConstA, ConstB, ConstC};
```

### [Generator Return Expressions](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.generator-return-expressions)
```PHP
$gen = (function() { yield 1; yield 2; return 3; })();
foreach ($gen as $val);
$gen->getReturn(); // 3
```

### [Generator delegation](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.generator-delegation)
```PHP
function foo() { yield 1; yield 2; yield from bar(); }
function bar() { yield 3; yield 4; }
```

### [Integer division with intdiv()](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.intdiv)
```PHP
intdiv(10, 3); // 3
```

### [Session options](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.session-options)
```PHP
session_start([
    'cache_limiter' => 'private',
    'read_and_close' => true,
]);
```

### [preg_replace_callback_array()](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.preg-repace-callback-array-function)
```PHP
preg_replace_callback_array([
    '~[a]+~' => function($match) {},
    '~[b]+~' => function($match) {},
], $subject);
```

### [CSPRNG Functions](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.csprng-functions)
```PHP
random_bytes();
random_int();
```

### [list() can always unpack objects implementing ArrayAccess](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.list-arrayaccess)
```PHP
list($a, $b) = new arrayObject([1,2]);
```

### [Other Features](http://php.net/manual/fr/migration70.new-features.php#migration70.new-features.others)
```PHP
(clone $foo)->bar();
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-70">PHP 7.0</a></p>

## PHP 5.6

Initial Release __2014-08-28__ : [Constant expressions](#constant-expressions), [Variadic functions via ...](#variadic-functions-via-), [Argument unpacking via ...](#argument-unpacking-via-), [Exponentiation via **](#exponentiation-via-), [use function and use const](#use-function-and-use-const), [phpdbg](#phpdbg), [Default character encoding](#default-character-encoding), [php://input is reusable](#phpinput-is-reusable), [Large file uploads](#large-file-uploads), [GMP supports operator overloading](#gmp-supports-operator-overloading), [hash_equals() for timing attack safe string comparison](#hash_equals-for-timing-attack-safe-string-comparison), [__debugInfo()](#__debuginfo), [gost-crypto hash algorithm](#gost-crypto-hash-algorithm), [pgsql async support](#pgsql-async-support)

### [Constant expressions](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.const-scalar-exprs)
```PHP
const ONE = 1;
const TWO = ONE * 2;
const ARR = [ONE, TWO];

class C {
    const THREE = TWO + 1;
    const ONE_THIRD = ONE / self::THREE;
    const SENTENCE = 'The value of THREE is '.self::THREE;
    public function f($a = ONE + self::THREE) {}
}
```

### [Variadic functions via ...](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.variadics)
```PHP
function foo(...$arg) { return array_sum($args); }
```

### [Argument unpacking via ...](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.splat)
```PHP
$args = [2,3];
foo(1, ...$args); // 6
```

### [Exponentiation via **](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.exponentiation)
```PHP
2 ** 3; // 2x2x2 = pow(2,3) = 8
```

### [use function and use const](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.use)
```PHP
use const Name\Space\FOO;
use function Name\Space\foo;

```

### [phpdbg](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.phpdbg)
```PHP
// PHP now includes an interactive debugger called phpdbg implemented as a SAPI module
```

### [Default character encoding](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.default-encoding)
```PHP
ini_get('default_charset'); // UTF-8
```

### [php://input is reusable](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.reusable-input)
```PHP
$payload = file_get_contents('php://input');
```

### [Large file uploads](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.large-file)
```PHP
// Files larger than 2 gigabytes in size are now accepted
```

### [GMP supports operator overloading](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.gmp)
```PHP
gmp_init(41) + 1; // 42
```

### [hash_equals() for timing attack safe string comparison](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.hash-equals)
```PHP
hash_equals(crypt("123", "#salt#", crypt(filter_input(INPUT_POST, 'pass'), "#salt#")));
```

### [__debugInfo()](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.debuginfo)
```PHP
class Foo
{
    private $prop = "bar";

    public function __debugInfo()
    {
        return ["prop" => "foo" . $this->prop];
    }
}

var_dump(new Foo); // foobar
```

### [gost-crypto hash algorithm](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.gost)
```PHP
hash("gost-crypto", "The quick brown fox jumps over the lazy dog.");
```

### [pgsql async support](http://php.net/manual/en/migration56.new-features.php#migration56.new-features.postgresql)
```PHP
$conn = pg_connect("dbname=foo", PGSQL_CONNECT_ASYNC);
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-56">PHP 5.6</a></p>

## PHP 5.5

Initial Release __2013-06-20__ : [Generators added](#generators-added), [finally keyword added](#finally-keyword-added), [New password hashing API](#new-password-hashing-api), [foreach now supports list()](#foreach-now-supports-list), [empty() supports arbitrary expressions](#empty-supports-arbitrary-expressions), [array and string literal dereferencing](#array-and-string-literal-dereferencing), [Class name resolution via ::class](#class-name-resolution-via-class), [OPcache extension added](#opcache-extension-added), [foreach now supports non-scalar keys](#foreach-now-supports-non-scalar-keys)

### [Generators added](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.generators)
```PHP
function xrange($start, $limit, $step = 1) {
    for ($i = $start; $i <= $limit; $i += $step) {
        yield $i;
    }
}
```

### [finally keyword added](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.finally)
```PHP
try {
    throw new Exception("foobar");
} catch (Exception $e) {
    /*re*/throw $e;
} finally {
    echo "I'm always executed, not matter what!";
}
```

### [New password hashing API](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.password)
```PHP
password_hash("rasmuslerdorf", PASSWORD_DEFAULT);
```

### [foreach now supports list()](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.foreach-list)
```PHP
foreach ([[1,2],[3,4]] as list($a, $b));
```

### [empty() supports arbitrary expressions](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.empty)
```PHP
function always_false() { return false; }
empty(always_false()); // true
```

### [array and string literal dereferencing](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.const-dereferencing)
```PHP
[1,2,3][1]; // 2
"123"[2]; // 3
```

### [Class name resolution via ::class](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.class-name)
```PHP
Foo\Bar::class;
```

### [OPcache extension added](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.opcache)
```PHP
// OPcache improves PHP performance by storing precompiled script bytecode in shared memory,
// thereby removing the need for PHP to load and parse scripts on each request.
```

### [foreach now supports non-scalar keys](http://php.net/manual/en/migration55.new-features.php#migration55.new-features.non-scalar-iterator-keys)
```PHP
foreach ($iterator as $object => $value);
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-55">PHP 5.5</a></p>

## PHP 5.4

Initial Release __2012-02-01__ : [Support for traits has been added](#support-for-traits-has-been-added), [Short array syntax has been added](#short-array-syntax-has-been-added), [Function array dereferencing has been added](#function-array-dereferencing-has-been-added), [Closures now support $this](#closures-now-support-this), [<?= is now always available](#-is-now-always-available), [Class member access on instantiation has been added](#class-member-access-on-instantiation-has-been-added), [Class::{expr}() syntax is now supported](#classexpr-syntax-is-now-supported), [Binary number format has been added](#binary-number-format-has-been-added), [Improved parse error messages and improved incompatible arguments warnings](#improved-parse-error-messages-and-improved-incompatible-arguments-warnings), [The session extension can now track the upload progress of files](#the-session-extension-can-now-track-the-upload-progress-of-files), [Built-in development web server in CLI mode](#built-in-development-web-server-in-cli-mode)

### [Support for traits has been added](http://php.net/manual/en/language.oop5.traits.php)
```PHP
trait Foo { public function hello() { echo "hello!"; } }
class Bar { use Foo; }
echo new Bar; // "hello!"
```

### [Short array syntax has been added](http://php.net/manual/en/migration54.new-features.php)
```PHP
$arr = ['one' => 1, 'two' => 2, 'three' => 3];
```

### [Function array dereferencing has been added](http://php.net/manual/en/migration54.new-features.php)
```PHP
function arr() { return [1,2,3]; }
echo arr()[0]; // 1
```

### [Closures now support $this](http://php.net/manual/en/functions.anonymous.php)
```PHP
$fn = Closure::bind(function() { echo $this->foo; }, (object)['foo' => 'bar']);
$fn(); // 'bar'
```

### [<?= is now always available](http://php.net/manual/en/migration54.new-features.php)
```PHP
<p><?="hello!"?></p>
```

### [Class member access on instantiation has been added](http://php.net/manual/en/migration54.new-features.php)
```PHP
echo (new Foo)->bar();
```

### [Class::{expr}() syntax is now supported](http://php.net/manual/en/migration54.new-features.php)
```PHP
echo Foo::{"get".$bar}();
```

### [Binary number format has been added](http://php.net/manual/en/migration54.new-features.php)
```PHP
echo 0b101010; // 42
```

### [Improved parse error messages and improved incompatible arguments warnings](http://php.net/manual/en/migration54.new-features.php)
```PHP
// ...
```

### [The session extension can now track the upload progress of files](http://php.net/manual/en/session.upload-progress.php)
```PHP
$key = ini_get("session.upload_progress.prefix") . $_POST[ini_get("session.upload_progress.name")];
var_dump($_SESSION[$key]);
```

### [Built-in development web server in CLI mode](http://php.net/manual/en/features.commandline.webserver.php)
```SHELL
$ php -S localhost:8000
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-54">PHP 5.4</a></p>

## PHP 5.3

Initial Release __2010-07-22__ : [Support for namespaces has been added](#support-for-namespaces-has-been-added), [Support for Late Static Bindings has been added](#support-for-late-static-bindings-has-been-added), [Support for jump labels (limited goto) has been added](#support-for-jump-labels-limited-goto-has-been-added), [Support for native Closures (Lambda/Anonymous functions) has been added](#support-for-native-closures-lambdaanonymous-functions-has-been-added), [There are two new magic methods, __callStatic() and __invoke()](#there-are-two-new-magic-methods-__callstatic-and-__invoke), [Nowdoc syntax is now supported, similar to Heredoc syntax, but with single quotes](#nowdoc-syntax-is-now-supported-similar-to-heredoc-syntax-but-with-single-quotes), [It is now possible to use Heredocs to initialize static variables and class properties/constants](#it-is-now-possible-to-use-heredocs-to-initialize-static-variables-and-class-propertiesconstants), [Heredocs may now be declared using double quotes, complementing the Nowdoc syntax](#heredocs-may-now-be-declared-using-double-quotes-complementing-the-nowdoc-syntax), [Constants can now be declared outside a class using the const keyword](#constants-can-now-be-declared-outside-a-class-using-the-const-keyword), [The ternary operator now has a shorthand form: ?:](#the-ternary-operator-now-has-a-shorthand-form-), [The HTTP stream wrapper now considers all status codes from 200 to 399 to be successful](#the-http-stream-wrapper-now-considers-all-status-codes-from-200-to-399-to-be-successful), [Dynamic access to static methods is now possible](#dynamic-access-to-static-methods-is-now-possible), [Exceptions can now be nested](#exceptions-can-now-be-nested), [A garbage collector for circular references has been added, and is enabled by default](#a-garbage-collector-for-circular-references-has-been-added-and-is-enabled-by-default), [The mail() function now supports logging of sent email via the mail.log configuration directive](#the-mail-function-now-supports-logging-of-sent-email-via-the-maillog-configuration-directive)

### [Support for namespaces has been added](http://php.net/manual/en/language.namespaces.php)
```PHP
namespace Foo\Bar;
use Another\Namespace\Class as Something;
```

### [Support for Late Static Bindings has been added](http://php.net/manual/en/language.oop5.late-static-bindings.php)
```PHP
class A
{
    const FOO = 1;

    public static function bar()
    {
        return static::FOO;
    }
}

class B extends A
{
    const FOO = 2;
}

echo B::bar(); // 2
```

### [Support for jump labels (limited goto) has been added](http://php.net/manual/en/control-structures.goto.php)
![XKCD Goto](http://php.net/manual/en/images/0baa1b9fae6aec55bbb73037f3016001-xkcd-goto.png)
```PHP
goto a;
echo 'Foo'; // never printed
a:
echo 'Bar';
```

### [Support for native Closures (Lambda/Anonymous functions) has been added](http://php.net/manual/en/functions.anonymous.php)
```PHP
$fn = function() {};
```

### [There are two new magic methods, __callStatic() and __invoke()](http://php.net/manual/en/migration53.new-features.php)
```PHP
class Foo
{
    public static function __callStatic($method, $args)
    {
        echo $method;
    }
}

Foo::something(); // 'something'

class Bar
{
    public function __invoke()
    {
        return 'foobar';
    }
}

$o = new Bar;
echo $o(); // 'foobar'
```

### [Nowdoc syntax is now supported, similar to Heredoc syntax, but with single quotes](http://php.net/manual/en/migration53.new-features.php)
```PHP
$name = 'Robert Paulson';
echo <<< EOF
His name is {$name}.
His name is {$name}.
His name is {$name}.
EOF;
```

### [It is now possible to use Heredocs to initialize static variables and class properties/constants](http://php.net/manual/en/migration53.new-features.php)
```PHP
class foo
{
    public $bar = <<< EOT
bar
EOT;
}
```

### [Heredocs may now be declared using double quotes, complementing the Nowdoc syntax](http://php.net/manual/en/migration53.new-features.php)
```PHP
echo <<<EOT
My name is "$name". I am printing some $foo->foo.
Now, I am printing some {$foo->bar[1]}.
This should print a capital 'A': \x41
EOT;
```

### [Constants can now be declared outside a class using the const keyword](http://php.net/manual/en/migration53.new-features.php)
```PHP
const FOO = "bar";
```

### [The ternary operator now has a shorthand form: ?:](http://php.net/manual/en/migration53.new-features.php)
```PHP
echo $a ? 'yes!' : 'nope :(';
```

### [The HTTP stream wrapper now considers all status codes from 200 to 399 to be successful](http://php.net/manual/en/migration53.new-features.php)
```PHP
// ...
```

### [Dynamic access to static methods is now possible](http://php.net/manual/en/migration53.new-features.php)
```PHP
echo Foo::{$bar}();
```

### [Exceptions can now be nested](http://php.net/manual/en/migration53.new-features.php)
```PHP
throw new RuntimeException("something went wrong...", 0, $previousException);
```

### [A garbage collector for circular references has been added, and is enabled by default](http://php.net/manual/en/migration53.new-features.php)
```PHP
gc_collect_cycles();
```

### [The mail() function now supports logging of sent email via the mail.log configuration directive](http://php.net/manual/en/migration53.new-features.php)
```PHP
$logfile = ini_get('mail.log');
```

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#php-53">PHP 5.3</a></p>

## Glossary

- [<?= is now always available](#-is-now-always-available) _5.4_
- [__debugInfo()](#__debuginfo) _5.6_
- [A garbage collector for circular references has been added, and is enabled by default](#a-garbage-collector-for-circular-references-has-been-added-and-is-enabled-by-default) _5.3_
- [Abstract method overriding](#abstract-method-overriding) _7.2_
- [Additional emulated prepares debugging information for PDO](#additional-emulated-prepares-debugging-information-for-pdo) _7.2_
- [Address Information additions to the Sockets extension](#address-information-additions-to-the-sockets-extension) _7.2_
- [Allow a trailing comma for grouped namespaces](#allow-a-trailing-comma-for-grouped-namespaces) _7.2_
- [Anonymous classes](#anonymous-classes) _7.0_
- [Argument unpacking via ...](#argument-unpacking-via-) _5.6_
- [array and string literal dereferencing](#array-and-string-literal-dereferencing) _5.5_
- [Asynchronous signal handling](#asynchronous-signal-handling) _7.1_
- [Binary number format has been added](#binary-number-format-has-been-added) _5.4_
- [Built-in development web server in CLI mode](#built-in-development-web-server-in-cli-mode) _5.4_
- [Class constant visibility](#class-constant-visibility) _7.1_
- [Class member access on instantiation has been added](#class-member-access-on-instantiation-has-been-added) _5.4_
- [Class name resolution via ::class](#class-name-resolution-via-class) _5.5_
- [Class::{expr}() syntax is now supported](#classexpr-syntax-is-now-supported) _5.4_
- [Closure::call()](#closurecall) _7.0_
- [Closures now support $this](#closures-now-support-this) _5.4_
- [Constant arrays using define()](#constant-arrays-using-define) _7.0_
- [Constant expressions](#constant-expressions) _5.6_
- [Constants can now be declared outside a class using the const keyword](#constants-can-now-be-declared-outside-a-class-using-the-const-keyword) _5.3_
- [Convert callables to Closures with Closure::fromCallable()](#convert-callables-to-closures-with-closurefromcallable) _7.1_
- [CSPRNG Functions](#csprng-functions) _7.0_
- [Default character encoding](#default-character-encoding) _5.6_
- [Dynamic access to static methods is now possible](#dynamic-access-to-static-methods-is-now-possible) _5.3_
- [empty() supports arbitrary expressions](#empty-supports-arbitrary-expressions) _5.5_
- [Enhancements to the EXIF extension](#enhancements-to-the-exif-extension) _7.2_
- [Enhancements to the ZIP extension](#enhancements-to-the-zip-extension) _7.2_
- [Exceptions can now be nested](#exceptions-can-now-be-nested) _5.3_
- [Expectations](#expectations) _7.0_
- [Exponentiation via **](#exponentiation-via-) _5.6_
- [Extended string types for PDO](#extended-string-types-for-pdo) _7.2_
- [Filtered unserialize()](#filtered-unserialize) _7.0_
- [finally keyword added](#finally-keyword-added) _5.5_
- [foreach now supports list()](#foreach-now-supports-list) _5.5_
- [foreach now supports non-scalar keys](#foreach-now-supports-non-scalar-keys) _5.5_
- [Function array dereferencing has been added](#function-array-dereferencing-has-been-added) _5.4_
- [Generator delegation](#generator-delegation) _7.0_
- [Generator Return Expressions](#generator-return-expressions) _7.0_
- [Generators added](#generators-added) _5.5_
- [GMP supports operator overloading](#gmp-supports-operator-overloading) _5.6_
- [gost-crypto hash algorithm](#gost-crypto-hash-algorithm) _5.6_
- [Group use declarations](#group-use-declarations) _7.0_
- [hash_equals() for timing attack safe string comparison](#hash_equals-for-timing-attack-safe-string-comparison) _5.6_
- [Heredocs may now be declared using double quotes, complementing the Nowdoc syntax](#heredocs-may-now-be-declared-using-double-quotes-complementing-the-nowdoc-syntax) _5.3_
- [Improved parse error messages and improved incompatible arguments warnings](#improved-parse-error-messages-and-improved-incompatible-arguments-warnings) _5.4_
- [Integer division with intdiv()](#integer-division-with-intdiv) _7.0_
- [IntlChar](#intlchar) _7.0_
- [It is now possible to use Heredocs to initialize static variables and class properties/constants](#it-is-now-possible-to-use-heredocs-to-initialize-static-variables-and-class-propertiesconstants) _5.3_
- [iterable pseudo-type](#iterable-pseudo-type) _7.1_
- [Large file uploads](#large-file-uploads) _5.6_
- [list() can always unpack objects implementing ArrayAccess](#list-can-always-unpack-objects-implementing-arrayaccess) _7.0_
- [Multi catch exception handling](#multi-catch-exception-handling) _7.1_
- [New features in PCRE](#new-features-in-pcre) _7.2_
- [New object type](#new-object-type) _7.2_
- [New password hashing API](#new-password-hashing-api) _5.5_
- [Nowdoc syntax is now supported, similar to Heredoc syntax, but with single quotes](#nowdoc-syntax-is-now-supported-similar-to-heredoc-syntax-but-with-single-quotes) _5.3_
- [Null coalescing operator](#null-coalescing-operator) _7.0_
- [Nullable types](#nullable-types), [Void functions](#void-functions) _7.1_
- [OPcache extension added](#opcache-extension-added) _5.5_
- [Oracle OCI8 Transparent Application Failover Callbacks](#oracle-oci8-transparent-application-failover-callbacks) _7.2_
- [Other Features](#other-features) _7.0_
- [pack() and unpack() endian support](#pack-and-unpack-endian-support) _7.2_
- [Parameter type widening](#parameter-type-widening) _7.2_
- [Password hashing with Argon2](#password-hashing-with-argon2) _7.2_
- [pgsql async support](#pgsql-async-support) _5.6_
- [php://input is reusable](#phpinput-is-reusable) _5.6_
- [phpdbg](#phpdbg) _5.6_
- [preg_replace_callback_array()](#preg_replace_callback_array) _7.0_
- [proc_nice() support on Windows](#proc_nice-support-on-windows) _7.2_
- [Return type declarations](#return-type-declarations) _7.0_
- [Scalar type declarations](#scalar-type-declarations) _7.0_
- [Session options](#session-options) _7.0_
- [Short array syntax has been added](#short-array-syntax-has-been-added) _5.4_
- [Sodium is now a core extension](#sodium-is-now-a-core-extension) _7.2_
- [Spaceship operator](#spaceship-operator) _7.0_
- [SQLite3 allows writing BLOBs](#sqlite3-allows-writing-blobs) _7.2_
- [Support for extended operations in LDAP](#support-for-extended-operations-in-ldap) _7.2_
- [Support for jump labels (limited goto) has been added](#support-for-jump-labels-limited-goto-has-been-added) _5.3_
- [Support for keys in list()](#support-for-keys-in-list) _7.1_
- [Support for Late Static Bindings has been added](#support-for-late-static-bindings-has-been-added) _5.3_
- [Support for namespaces has been added](#support-for-namespaces-has-been-added) _5.3_
- [Support for native Closures (Lambda/Anonymous functions) has been added](#support-for-native-closures-lambdaanonymous-functions-has-been-added) _5.3_
- [Support for negative string offsets](#support-for-negative-string-offsets) _7.1_
- [Support for traits has been added](#support-for-traits-has-been-added) _5.4_
- [Symmetric array destructuring](#symmetric-array-destructuring) _7.1_
- [The HTTP stream wrapper now considers all status codes from 200 to 399 to be successful](#the-http-stream-wrapper-now-considers-all-status-codes-from-200-to-399-to-be-successful) _5.3_
- [The mail() function now supports logging of sent email via the mail.log configuration directive](#the-mail-function-now-supports-logging-of-sent-email-via-the-maillog-configuration-directive) _5.3_
- [The session extension can now track the upload progress of files](#the-session-extension-can-now-track-the-upload-progress-of-files) _5.4_
- [The ternary operator now has a shorthand form: ?:](#the-ternary-operator-now-has-a-shorthand-form-) _5.3_
- [There are two new magic methods, __callStatic() and __invoke()](#there-are-two-new-magic-methods-__callstatic-and-__invoke) _5.3_
- [Unicode codepoint escape syntax](#unicode-codepoint-escape-syntax) _7.0_
- [use function and use const](#use-function-and-use-const) _5.6_
- [Variadic functions via ...](#variadic-functions-via-) _5.6_

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#glossary">Glossary</a></p>

## Credits

<a rel="license" href="http://creativecommons.org/licenses/by/4.0/"><img alt="Licence Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by/4.0/88x31.png"></a>

<i><span xmlns:dct="http://purl.org/dc/terms/" href="http://purl.org/dc/dcmitype/Text" property="dct:title" rel="dct:type">PHP New Features CheatSheet</span></i> by <a xmlns:cc="http://creativecommons.org/ns#" href="mailto:benjamin.delespierre@gmail.com" property="cc:attributionName" rel="cc:attributionURL">Benjamin Delespierre</a> is licensed under <a rel="license" href="http://creativecommons.org/licenses/by/4.0/">Creative Commons Attribution 4.0 International</a>.

Based from <a href="http://php.net/manual/en/">The PHP Manual</a> by <a xmlns:dct="http://purl.org/dc/terms/" href="http://php.net/manual/en/copyright.php" rel="dct:source">The PHP Group</a>.

Social icons from [Foundation](http://zurb.com/playground/foundation-icon-fonts-3).

<p align="right"><a href="#php-new-features-cheatsheet">Summary</a> &#187; <a href="#credits">Credits</a></p>
