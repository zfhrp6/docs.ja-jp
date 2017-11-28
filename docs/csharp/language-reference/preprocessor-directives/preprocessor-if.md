---
title: "#<a name=\"if-c-reference\"></a>if (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#if'
helpviewer_keywords: '#if directive [C#]'
ms.assetid: 48cabbff-ca82-491f-a56a-eeccd528c7c2
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e4e3b79f64f5190d48d7248726ecdf031ad685e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="if-c-reference"></a>#if (C# リファレンス)
C# コンパイラでは、`#if` ディレクティブ、次いで [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) ディレクティブが検出されると、これらのディレクティブ間のコードがコンパイルされます (指定されたシンボルが定義されている場合に限る)。  C や C++ とは異なり、シンボルに数値を代入することはできません。C# の #if ステートメントはブール値であり、シンボルが定義済みかどうかのテストのみを行います。 次に例を示します。  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) (等しい) および [!=](../../../csharp/language-reference/operators/not-equal-operator.md) (等しくない) の各演算子は、[true](../../../csharp/language-reference/keywords/true.md) か [false](../../../csharp/language-reference/keywords/false.md) のどちらであるかのテストにのみ使用できます。 true は、シンボルが定義されていることを意味します。 ステートメント `#if DEBUG` と `#if (DEBUG == true)` の意味は同じです。 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) (かつ)、[&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) (または)、および [!](../../../csharp/language-reference/operators/logical-negation-operator.md) (not) の各演算子を使用すると、複数のシンボルが定義されているかどうかを評価できます。 シンボルと演算子は、かっこを使用してグループ化できます。  
  
## <a name="remarks"></a>コメント  
 `#if` と [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)、[#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)、[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)、[#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)、[#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) の各ディレクティブを組み合わせると、1 つ以上のシンボルが存在するかどうかに応じてコードを含めたり除外したりできます。 これは、デバッグ ビルドのコードをコンパイルする場合や、特定の構成でコンパイルを行う場合に役立ちます。  
  
 `#if` ディレクティブで始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了させる必要があります。  
  
 `#define` を使用するとシンボルを定義できます。定義したシンボルを `#if` ディレクティブに渡す式として使用すると、この式は `true` と評価されます。  
  
 シンボルは、[/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションでも定義できます。 [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) を使うと、シンボルを未定義状態にできます。  
  
 `/define` または `#define` で定義されたシンボルは、同じ名前の変数とは競合しません。 変数名をプリプロセッサ ディレクティブに渡すことはできません。シンボルはプリプロセッサ ディレクティブだけで評価されます。  
  
 `#define` を使用して作成したシンボルのスコープは、そのシンボルが定義されているファイルです。  
  
## <a name="example"></a>例  
  
```csharp
// preprocessor_if.cs  
#define DEBUG
#define MYTEST  
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
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)
