# Proposals to "improve" the Zig language

Each proposal is marked with a level of how much I belive it should be accepted

3: Necessary  
2: Would be great  
1: Does not do much  
0: Pointless  

## Change label syntax for consistency
Level: 2  

```zig
label: for (0..10) {
    break :label;
}
// blocks
label: {
    //...
}
```
```zig
for:label (0..10) {
    break:label;
}
// blocks
:label {
    //...
}
```
> Reasoning: same syntax for declaration and use of labels  
> Variant: use for@label instead of for:label


## Explicit pointer mutability
Level: 3  

```zig
var foo: *i32 = undefined;
const bar: *const i32 = undefined;
```
```zig
var foo: *var i32 = undefined;
const bar: *const i32 = undefined;
```
> Reasoning: remove the convenience of mutable pointer when not necessary, possible typo, and disambiguate from the multiplication operator  
> Variant: use a new ```mut``` keyword  

> [!IMPORTANT]
> This has already been rejected by Andrew Kelley in 2020

## Explicitly mention slices are pointers
Level: 1  

```zig
const foo: []i32 = undefined;
const bar: []const u8 = undefined;

const array: [10]u32 = undefined;
```
```zig
const foo: *[i32] = undefined;
const bar: *const [u8] = undefined;

const array: [10]u32 = undefined;
```

## Private struct members
Level: 3  

```zig
const Foo = struct {
    private: i32,
    pub public: i32,

    fn privateFn(self: *@This) {
        //...
    }
    pub fn publicFn(self: *@This) {
        privateFn(self);
    }
};
```
> [!IMPORTANT]
> Feature proposal, no equivalent in current zig syntax  

<!-- # Arbitrary changes -->
<!-- NOTE: whoops, this is pretty much a different language, really -->
<!-- Things that would make zig not even zig anymore -->
<!---->
<!-- ## Rename null to none -->
<!-- Level: 0 -->
<!---->
<!-- ```zig -->
<!-- var some: ?i32 = null; -->
<!-- ``` -->
<!-- ```zig -->
<!-- var some: ?i32 = none; -->
<!-- ``` -->
<!---->
<!-- ## Disambiguate variables from types -->
<!-- Level: 0 -->
<!---->
<!-- ```zig -->
<!-- const Foo = i32; -->
<!-- const Foo = struct { -->
<!--     //... -->
<!-- }; -->
<!---->
<!-- const var: i32 = 10; -->
<!-- ``` -->
<!-- ```zig -->
<!-- type Foo = i32; -->
<!-- type Foo = struct { -->
<!--     //... -->
<!-- }; -->
<!---->
<!-- const var: i32 = 10; -->
<!-- ``` -->

## Warnings
Level: 3  
Please? :(  
