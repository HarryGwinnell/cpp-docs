---
description: "Learn more about: dllexport, dllimport"
title: "dllexport, dllimport"
ms.date: 05/24/2022
f1_keywords: ["dllimport_cpp", "dllexport_cpp"]
helpviewer_keywords: ["dllexport __declspec keyword", "__declspec keyword [C++], dllexport", "dllimport __declspec keyword", "__declspec keyword [C++], dllimport"]
ms.assetid: ff95b645-ef55-4e72-b848-df44657b3208
---
# `dllexport`, `dllimport`

**Microsoft Specific**

The **`dllexport`** and **`dllimport`** storage-class attributes are Microsoft-specific extensions to the C and C++ languages. You can use them to export and import functions, data, and objects to or from a DLL.

## Syntax

> **`__declspec( dllimport )`** *`declarator`*\
> **`__declspec( dllexport )`** *`declarator`*

## Remarks

These attributes explicitly define the DLL's interface to its client, which can be the executable file or another DLL. Declaring functions as **`dllexport`** eliminates the need for a module-definition (`.def`) file, at least with respect to the specification of exported functions. The **`dllexport`** attribute replaces the **`__export`** keyword.

If a class is marked `__declspec(dllexport)`, any specializations of class templates in the class hierarchy are implicitly marked as `__declspec(dllexport)`. It means that class templates are explicitly instantiated and the class's members must be defined.

**`dllexport`** of a function exposes the function with its decorated name, sometimes known as "name mangling". For C++ functions, the decorated name includes extra characters that encode type and parameter information. C functions or functions that are declared as `extern "C"` follow C name decoration rules. For more information on name decoration in C/C++ code, see [Decorated names](../build/reference/decorated-names.md).

To export an undecorated name, you can link by using a Module Definition (`.def`) file that defines the undecorated name in an `EXPORTS` section. For more information, see [`EXPORTS`](../build/reference/exports.md). Another way to export an undecorated name is to use a `#pragma comment(linker, "/export:alias=decorated_name")` directive in the source code.

When you declare **`dllexport`** or **`dllimport`**, you must use [extended attribute syntax](../cpp/declspec.md) and the **`__declspec`** keyword.

## Example

```cpp
// Example of the dllimport and dllexport class attributes
__declspec( dllimport ) int i;
__declspec( dllexport ) void func();
```

Alternatively, to make your code more readable, you can use macro definitions:

```cpp
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport void func();
DllExport int i = 10;
DllImport int j;
DllExport int n;
```

For more information, see:

- [Definitions and declarations](../cpp/definitions-and-declarations-cpp.md)

- [Defining inline C++ functions with `dllexport` and `dllimport`](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

- [General rules and limitations](../cpp/general-rules-and-limitations.md)

- [Using `dllimport` and `dllexport` in C++ classes](../cpp/using-dllimport-and-dllexport-in-cpp-classes.md)

**END Microsoft Specific**

## See also

[`__declspec`](../cpp/declspec.md)\
[Keywords](../cpp/keywords-cpp.md)
