---
title: "$ (C# リファレンス)"
ms.date: 02/09/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
ms.assetid: 7d9e21b5-eac3-4878-9530-50e4da578acd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d245bab063721abdb930aae113aab2094553b9bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="-c-reference"></a><span data-ttu-id="b84cd-102">$ (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b84cd-102">$ (C# Reference)</span></span>

<span data-ttu-id="b84cd-103">リテラル文字列を[挿入文字列](../keywords/interpolated-strings.md)として識別します。</span><span class="sxs-lookup"><span data-stu-id="b84cd-103">Identifies a string literal as an [interpolated string](../keywords/interpolated-strings.md).</span></span> <span data-ttu-id="b84cd-104">挿入文字列はテンプレートのような文字列で、"*挿入式*" とリテラル テキストを含みます。</span><span class="sxs-lookup"><span data-stu-id="b84cd-104">An interpolated string is a template-like string that contains literal text along with *interpolated expressions*.</span></span> <span data-ttu-id="b84cd-105">挿入文字列が解決されると、たとえば代入ステートメントまたはメソッド呼び出し内で、結果文字列の文字列表現によって挿入式が置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b84cd-105">When the interpolated string is resolved, for example in an assignment statement or a method call, its interpolated expressions are replaced by their string representations in the result string.</span></span> <span data-ttu-id="b84cd-106">挿入文字列は、.NET Framework でサポートされている[複合書式指定文字列](../../../standard/base-types/composite-format.md)の代わりになるものです。</span><span class="sxs-lookup"><span data-stu-id="b84cd-106">Interpolated strings are replacements for the [composite format strings](../../../standard/base-types/composite-format.md) supported by the .NET Framework.</span></span>

<span data-ttu-id="b84cd-107">次の例では、`$` 文字を使用して、挿入文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="b84cd-107">The following example uses the `$` character to define an interpolated string.</span></span>

[!code-csharp[interpolated-string-symbol](../../../../samples/snippets/csharp/language-reference/keywords/dollar-sign1.cs#1)]

<span data-ttu-id="b84cd-108">挿入文字列の詳細については、トピック「[挿入文字列](../keywords/interpolated-strings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b84cd-108">For more information on interpolated strings, see the [Interpolated Strings](../keywords/interpolated-strings.md) topic.</span></span>

## <a name="see-also"></a><span data-ttu-id="b84cd-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="b84cd-109">See Also</span></span>  
 [<span data-ttu-id="b84cd-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="b84cd-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b84cd-111">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b84cd-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b84cd-112">C# 特殊文字</span><span class="sxs-lookup"><span data-stu-id="b84cd-112">C# Special Characters</span></span>](../../../csharp/language-reference/tokens/index.md)
