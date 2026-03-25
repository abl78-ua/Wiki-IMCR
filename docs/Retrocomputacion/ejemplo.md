---
title: Probando mkdocs
---

# ALERTA ESTO ES UNA ***`prueba`***

GBA

$$
\cos x=\sum_{k=0}^{\infty}\frac{(-1)^k}{(2k)!}x^{2k}\quad\forall i \notin A
$$

=== "C"

    ``` c
    #include <stdio.h>

    int main(void) {
      printf("Hello world!\n");
      return 0;
    }
    ```

=== "C++"

    ``` c++
    #include <iostream>

    int main(void) {
      std::cout << "Hello world!" << std::endl;
      return 0;
    }
    ```

!!! info "Info"
	Info

!!! error "Error"
	Hola
	
!!! bug "Bug"
	Hola

!!! warn "Bug"
	Hola

??? info "¿Sabías que... ?"
	Hola

???+ info "Hola"
	Hola

!!! note "Nota"
	Hola
	
!!! abstract "Resumen"
	Hola

!!! tip "Consejo"
	Hola
	
!!! success "Todo bien"
	Hola
	
!!! question "???"
	Hola
	
!!! failure "Fallo"
	Hola

!!! danger "Peligro"
	Hola

!!! example "Ejemplo"
	Hola

!!! quote "Cita"
	Hola

Hola[^ref:GBAwiki]

``` c++
// Complete example of valid c++23 """code"""

#include <cassert>
#include <cstddef>
#include <cstdint>
#include <new>
#include <print>
#include <string>

static int x<:10:>;
const static long long y{ 0xFFF };

struct B
<%
private:
  struct Voldemort
  {
    int a, b;
  };

public:
  constexpr Voldemort
  getIce ()
  {
    return Voldemort{ .a = 130, .b = 69 };
  };
  int
  setValue (const bool &)
  {
    return 130;
  };
  int
  setValue (const std::string &) noexcept
  {
    return 69;
  };
  int
  operator& () const
  {
    return 69;
  };
%>;

int
main (int argc, char **argv)
<%
  B pt;
  std::print (
      "A normal way for writing in modernest' c++ standard, {} == {}\n",
      (pt.*static_cast<int (B::*) (const bool &)> (&B::setValue)) (+"hello"),
      pt.setValue ("CHAO"));

  auto a = pt.getIce ();
  try
    {
      if (a.a
          == static_cast<int> (reinterpret_cast<std::intptr_t> (
              std::launder (reinterpret_cast<int (*)<:10:>> (&0 <:x:>)))))
        throw &pt;
    }
  catch (...)
    {
    };

  return (pt, +<::> <% return a.b; %>());
%>

```


[^ref:GBAwiki]: Wikipedia, [Game Boy Advance](https://en.wikipedia.org/wiki/Game_Boy_Advance) (Consultado el 5/3/2026)
*[GBA]: Game Boy Advance
