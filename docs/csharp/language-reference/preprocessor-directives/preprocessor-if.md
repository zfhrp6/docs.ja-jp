---
title: "#if (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#if"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#if ディレクティブ [C#]"
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# #if (C# リファレンス)
`#if` ディレクティブとその後にある [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) ディレクティブが C\# コンパイラによって検出されると、これらのディレクティブ間のコードは、指定のシンボルが定義されている場合にのみコンパイルされます。  C および C\+\+ とは異なり、シンボルに数値を割り当てることはできません。C\# の \#if ステートメントはブール型であり、シンボルが定義されているかどうかのみをテストします。  次に例を示します。  
  
```  
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 [true](../../../csharp/language-reference/keywords/true.md) か [false](../../../csharp/language-reference/keywords/false.md) かをテストするときには、[\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) \(等値\) と [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) \(非等値\) の演算子のみを使用できます。  true はシンボルが定義されていることを意味します。  `#if DEBUG` ステートメントは `#if (DEBUG == true)` と同じ意味です。  演算子を使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) は、\(または\)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) \(または\)、および [\!](../../../csharp/language-reference/operators/logical-negation-operator.md)\(ではなく\) 複数のシンボルが定義されているかどうかを評価します。  シンボルと演算子は、かっこを使用してグループ化できます。  
  
## 解説  
 `#if` を、[\#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)、および [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) ディレクティブと組み合わせて使用すると、1 つ以上のシンボルの存在に応じて、コードを処理対象にしたり、処理対象から外したりできます。  これは、デバッグ ビルド用にコンパイルするときや、特定の構成でコンパイルするときに使用すると便利です。  
  
 `#if` で始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了する必要があります。  
  
 `#define` を使用すると、シンボルを定義できます。定義したシンボルを式として `#if` ディレクティブに渡すと、式は `true` と評価されます。  
  
 また、シンボルは [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。  [\#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。  
  
 `/define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。  変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。  
  
 `#define` で定義されたシンボルのスコープは、シンボルが定義されたファイル内だけです。  
  
## 使用例  
  
```  
// preprocessor_if.cs  
#define DEBUG #define MYTEST  
using System;  
public class MyClass   
{  
    static void Main()   
    {  
#if (DEBUG && !MYTEST)  
        Console.WriteLine("DEBUG is defined");  
#elif (!DEBUG && MYTEST)  
        Console.WriteLine("MYTEST is defined");  
#elif (DEBUG && MYTEST)  
        Console.WriteLine("DEBUG and MYTEST are defined");  
#else  
        Console.WriteLine("DEBUG and MYTEST are not defined");  
#endif  
    }  
}  
```  
  
  **DEBUG and MYTEST are defined**   
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)