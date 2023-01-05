+++
title = "Sample blogpost"
date = 2022-03-23
+++

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec ut sem a tellus rutrum accumsan sed
in eros. Sed eget tristique neque, in malesuada nibh. Sed id placerat nunc. Aliquam erat volutpat.
Nullam vitae ligula diam. Donec vehicula tempus libero, sed convallis quam rhoncus quis. Etiam
dictum venenatis augue, eu ornare velit efficitur non. Aliquam efficitur commodo neque, nec sodales
ipsum euismod quis. Sed hendrerit enim mi, sit amet varius ante scelerisque a.

Quisque sit amet placerat diam, vel mattis justo. Nunc sodales felis urna, ut pulvinar felis aliquet
in. Nullam non dolor sem. Phasellus mattis, augue et varius laoreet, ante quam feugiat sapien, in
ornare lectus lorem vitae tellus. Mauris eget quam interdum, rhoncus dolor ut, facilisis justo.
Nullam interdum nec leo at convallis. Praesent varius sem at sollicitudin scelerisque. Morbi ipsum
quam, fringilla vitae nisi eu, mollis hendrerit tortor.

Quisque elementum auctor tellus, sed commodo lorem hendrerit in. Aliquam nec arcu commodo ex
vulputate cursus. Pellentesque id quam metus. Etiam dapibus venenatis turpis, eget aliquet lectus
maximus ac. Ut vitae diam a felis vehicula suscipit nec et nisl. Suspendisse rhoncus ullamcorper
malesuada. Phasellus pulvinar euismod nulla sed pellentesque. Vestibulum ante ipsum primis in
faucibus orci luctus et ultrices posuere cubilia curae; Duis interdum sapien a augue tempus euismod.
Aenean egestas odio ut ante rutrum aliquet.

Sed id dui in sem venenatis aliquam. Phasellus sit amet ex eros. Vivamus vestibulum tincidunt
tellus, non dictum purus dapibus quis. Phasellus scelerisque vulputate quam, et auctor elit eleifend
molestie. Sed commodo eleifend massa, ac tincidunt tortor malesuada id. Aenean feugiat bibendum
tempus. Duis euismod molestie massa, ut mollis risus. Curabitur dapibus varius tincidunt. Aliquam
eget pellentesque est. Duis efficitur facilisis suscipit. Etiam felis nisl, ultricies ut elementum
sed, elementum in dui.

Integer ut ligula feugiat, euismod urna in, dictum ligula. Fusce ac tellus vel diam vulputate rutrum
vitae vel odio. Praesent nec sapien pharetra, commodo nisi quis, blandit libero. Donec dignissim
purus et metus blandit hendrerit. Nulla fringilla sapien ac aliquet pulvinar. Aenean ac mi eu elit
bibendum finibus nec at nulla. Vivamus vel convallis dolor.

```cpp
#include <string>
#include <cstddef>
#include <concepts>

// Declaration of the concept "Hashable", which is satisfied by any type 'T'
// such that for values 'a' of type 'T', the expression std::hash<T>{}(a)
// compiles and its result is convertible to std::size_t
template<typename T>
concept Hashable = requires(T a)
{
    { std::hash<T>{}(a) } -> std::convertible_to<std::size_t>;
};

struct meow {};

// Constrained C++20 function template:
template<Hashable T>
void f(T) {}
//
// Alternative ways to apply the same constraint:
// template<typename T>
//     requires Hashable<T>
// void f(T) {}
//
// template<typename T>
// void f(T) requires Hashable<T> {}

int main()
{
    using std::operator""s;

    f("abc"s);    // OK, std::string satisfies Hashable
    // f(meow{}); // Error: meow does not satisfy Hashable
}
```
