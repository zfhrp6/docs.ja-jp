---
title: "$ (C# リファレンス)"
ms.date: 2017-02-09
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
dev_langs:
- CSharp
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
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
ms.openlocfilehash: 65dfc7b28059c4d41dd9113fd60c6a64987bfc2b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-c-reference"></a><span data-ttu-id="2a951-102">$ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2a951-102">$ (C# Reference)</span></span>

<span data-ttu-id="2a951-103">リテラル文字列を[挿入文字列](../keywords/interpolated-strings.md)として識別します。</span><span class="sxs-lookup"><span data-stu-id="2a951-103">Identifies a string literal as an [interpolated string](../keywords/interpolated-strings.md).</span></span> <span data-ttu-id="2a951-104">挿入文字列はテンプレートのような文字列で、"*挿入式*" とリテラル テキストを含みます。</span><span class="sxs-lookup"><span data-stu-id="2a951-104">An interpolated string is a template-like string that contains literal text along with *interpolated expressions*.</span></span> <span data-ttu-id="2a951-105">挿入文字列が解決されると、たとえば代入ステートメントまたはメソッド呼び出し内で、結果文字列の文字列表現によって挿入式が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="2a951-105">When the interpolated string is resolved, for example in an assignment statement or a method call, its interpolated expressions are replaced by their string representations in the result string.</span></span> <span data-ttu-id="2a951-106">挿入文字列は、.NET Framework でサポートされている[複合書式指定文字列](../../../standard/base-types/composite-format.md)の代わりになるものです。</span><span class="sxs-lookup"><span data-stu-id="2a951-106">Interpolated strings are replacements for the [composite format strings](../../../standard/base-types/composite-format.md) supported by the .NET Framework.</span></span>

<span data-ttu-id="2a951-107">次の例では、`$` 文字を使用して、挿入文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="2a951-107">The following example uses the `$` character to define an interpolated string.</span></span>

<span data-ttu-id="2a951-108">[!CODE-cs[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="2a951-108">[!CODE-cs[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]</span></span>

<span data-ttu-id="2a951-109">挿入文字列の詳細については、トピック「[挿入文字列](../keywords/interpolated-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a951-109">For more information on interpolated strings, see the [Interpolated Strings](../keywords/interpolated-strings.md) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a951-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a951-110">See Also</span></span>  
 <span data-ttu-id="2a951-111">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="2a951-111">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="2a951-112">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2a951-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="2a951-113">C# の特殊文字</span><span class="sxs-lookup"><span data-stu-id="2a951-113">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)

