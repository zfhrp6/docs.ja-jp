---
title: "params (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5999911b96d17c710096e74c8f3da65223e778fc
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="params-c-reference"></a><span data-ttu-id="9d8f9-102">params (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9d8f9-102">params (C# Reference)</span></span>
<span data-ttu-id="9d8f9-103">`params` キーワードを使用すると、可変数個の引数を受け取る[メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="9d8f9-104">パラメーター宣言で指定した型の引数のコンマ区切りのリスト、または指定した型の引数の配列を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="9d8f9-105">また、引数を渡さないこともできます。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-105">You also can send no arguments.</span></span> <span data-ttu-id="9d8f9-106">引数を渡さない場合、`params` リストの長さはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="9d8f9-107">1 つのメソッド宣言内では、`params` キーワード以後にパラメーターを追加できないため、1 つの `params` キーワードだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d8f9-108">例</span><span class="sxs-lookup"><span data-stu-id="9d8f9-108">Example</span></span>  
 <span data-ttu-id="9d8f9-109">次の例に示すように、さまざまな方法で `params` パラメーターに引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="9d8f9-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 <span data-ttu-id="9d8f9-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9d8f9-110">[!code-cs[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9d8f9-111">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9d8f9-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d8f9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d8f9-112">See Also</span></span>  
 <span data-ttu-id="9d8f9-113">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d8f9-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9d8f9-114">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d8f9-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9d8f9-115">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9d8f9-115">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="9d8f9-116">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="9d8f9-116">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)

