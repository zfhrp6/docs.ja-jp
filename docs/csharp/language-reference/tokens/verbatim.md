---
title: "@ (C# リファレンス)"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '@_CSharpKeyword'
- '@'
dev_langs:
- CSharp
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 08e3da6aaeee037d7272ea8cddc4382a436b683b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-c-reference"></a><span data-ttu-id="746d3-102">@ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="746d3-102">@ (C# Reference)</span></span>

<span data-ttu-id="746d3-103">特殊文字 `@` は、verbatim 識別子として機能します。</span><span class="sxs-lookup"><span data-stu-id="746d3-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="746d3-104">これは次の目的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="746d3-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="746d3-105">C# のキーワードを識別子として使用できるようにする。</span><span class="sxs-lookup"><span data-stu-id="746d3-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="746d3-106">コード要素のプレフィックスとして `@` 文字を使用すると、その要素はC# のキーワードではなく、識別子としてコンパイラに解釈されます。</span><span class="sxs-lookup"><span data-stu-id="746d3-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="746d3-107">次の例では、`@` 文字を使用して、`for` ループで使用する `for` という識別子を定義しています。</span><span class="sxs-lookup"><span data-stu-id="746d3-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   <span data-ttu-id="746d3-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="746d3-108">[!code-cs[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]</span></span>

1. <span data-ttu-id="746d3-109">文字列リテラルを逐語的に解釈することを示す。</span><span class="sxs-lookup"><span data-stu-id="746d3-109">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="746d3-110">このインスタンス内の `@` 文字は、*verbatim 文字列リテラル*を定義します。</span><span class="sxs-lookup"><span data-stu-id="746d3-110">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="746d3-111">単純なエスケープ シーケンス (バック スラッシュの `"\\"` など)、16 進数のエスケープ シーケンス (大文字 A の `"\x0041"` など)、および Unicode のエスケープ シーケンス (大文字 A の `"\u0041"` など) は、リテラルに解釈されます。</span><span class="sxs-lookup"><span data-stu-id="746d3-111">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A, and Unicode escape sequences, such as `"\u0041"` for an uppercase A, are interpreted literally.</span></span> <span data-ttu-id="746d3-112">引用符のエスケープ シーケンス (`""`) だけは、リテラルに解釈することはできません。一重引用符が生成されます。</span><span class="sxs-lookup"><span data-stu-id="746d3-112">Only a quote escape sequence (`""`) is not interpreted literally; it produces a single quotation mark.</span></span> <span data-ttu-id="746d3-113">次の例では、2 つの同じファイル パスを定義しています。一方は通常の文字列リテラルを使用して、もう一方は verbatim 文字列リテラルを使用して定義しています。</span><span class="sxs-lookup"><span data-stu-id="746d3-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="746d3-114">これは、verbatim 文字列リテラルの一般的な用途の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="746d3-114">This is one of the more common uses of verbatim string literals.</span></span>

   <span data-ttu-id="746d3-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span><span class="sxs-lookup"><span data-stu-id="746d3-115">[!code-cs[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]</span></span>

   <span data-ttu-id="746d3-116">次の例は、同じ文字シーケンスを通常の文字列リテラルと verbatim 文字列リテラルで定義した場合の結果を示したものです。</span><span class="sxs-lookup"><span data-stu-id="746d3-116">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   <span data-ttu-id="746d3-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span><span class="sxs-lookup"><span data-stu-id="746d3-117">[!code-cs[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]</span></span>

1. <span data-ttu-id="746d3-118">名前の競合がある場合に、コンパイラが属性を区別できるようにする。</span><span class="sxs-lookup"><span data-stu-id="746d3-118">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="746d3-119">属性は @System.Attribute の派生型です。</span><span class="sxs-lookup"><span data-stu-id="746d3-119">An attribute is a type that derives from @System.Attribute.</span></span> <span data-ttu-id="746d3-120">通常、その型の名前には **Attribute** サフィックスが含まれます。これは、コンパイラがその規則を強制していない場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="746d3-120">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="746d3-121">そのため属性は、完全な型名 (たとえば、`[InfoAttribute]`) か、短縮名 (たとえば、`[Info]`) によってコード内から参照できます。</span><span class="sxs-lookup"><span data-stu-id="746d3-121">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="746d3-122">ただし、短縮された 2 つの属性型名が同じである場合、一方の型名に **Attribute** サフィックスが含まれていて、もう一方に含まれていないと、名前の競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="746d3-122">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="746d3-123">たとえば、次のコードでは、`Info` と `InfoAttribute` のどちらの属性が `Main` メソッドに適用されるのをコンパイラが判断できないため、コンパイルが失敗します。</span><span class="sxs-lookup"><span data-stu-id="746d3-123">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Main` method.</span></span>

   ```csharp
   using System;

   [AttributeUsage(AttributeTargets.Class)]
   public class Info : Attribute
   {
      private string information;
      
      public Info(string info)
      {
          information = info;
      }
   }

   [AttributeUsage(AttributeTargets.Method)]
   public class InfoAttribute : Attribute
   {
      private string information;
      
      public InfoAttribute(string info)
      {
          information = info;
      }
   }

   [Info("A simple executable.")]
   public class Example
   {
      [InfoAttribute("The entry point.")]
      public static void Main()
      {
      }
   }
   ```  

   <span data-ttu-id="746d3-124">verbatim 識別子を使用して `Info` 属性を識別すれば、コンパイルは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="746d3-124">If the verbatim identifier is used to identify the `Info` attribute, the example compiles successfully.</span></span>

   <span data-ttu-id="746d3-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="746d3-125">[!code-cs[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim4.cs#1)]</span></span>

## <a name="see-also"></a><span data-ttu-id="746d3-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="746d3-126">See Also</span></span>  
 <span data-ttu-id="746d3-127">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="746d3-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="746d3-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="746d3-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="746d3-129">C# の特殊文字</span><span class="sxs-lookup"><span data-stu-id="746d3-129">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)

