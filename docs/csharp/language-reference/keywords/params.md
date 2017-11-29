---
title: "params (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66cfc8e7b131a4443ee227df5e39c7e3b775324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="params-c-reference"></a><span data-ttu-id="f1408-102">params (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f1408-102">params (C# Reference)</span></span>
<span data-ttu-id="f1408-103">`params` キーワードを使用すると、可変数個の引数を受け取る[メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f1408-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="f1408-104">パラメーター宣言で指定した型の引数のコンマ区切りのリスト、または指定した型の引数の配列を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f1408-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="f1408-105">また、引数を渡さないこともできます。</span><span class="sxs-lookup"><span data-stu-id="f1408-105">You also can send no arguments.</span></span> <span data-ttu-id="f1408-106">引数を渡さない場合、`params` リストの長さはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="f1408-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="f1408-107">1 つのメソッド宣言内では、`params` キーワード以後にパラメーターを追加できないため、1 つの `params` キーワードだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="f1408-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1408-108">例</span><span class="sxs-lookup"><span data-stu-id="f1408-108">Example</span></span>  
 <span data-ttu-id="f1408-109">次の例に示すように、さまざまな方法で `params` パラメーターに引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="f1408-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f1408-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f1408-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f1408-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1408-111">See Also</span></span>  
 [<span data-ttu-id="f1408-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f1408-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f1408-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f1408-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1408-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="f1408-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f1408-115">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1408-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
