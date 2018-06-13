---
title: params (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: d7e0094d0f60aa201ae7229983f3e4b9764d2cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33265471"
---
# <a name="params-c-reference"></a><span data-ttu-id="0831a-102">params (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0831a-102">params (C# Reference)</span></span>
<span data-ttu-id="0831a-103">`params` キーワードを使用すると、可変数個の引数を受け取る[メソッド パラメーター](../../../csharp/language-reference/keywords/method-parameters.md)を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0831a-103">By using the `params` keyword, you can specify a [method parameter](../../../csharp/language-reference/keywords/method-parameters.md) that takes a variable number of arguments.</span></span>  
  
 <span data-ttu-id="0831a-104">パラメーター宣言で指定した型の引数のコンマ区切りのリスト、または指定した型の引数の配列を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0831a-104">You can send a comma-separated list of arguments of the type specified in the parameter declaration or an array of arguments of the specified type.</span></span> <span data-ttu-id="0831a-105">また、引数を渡さないこともできます。</span><span class="sxs-lookup"><span data-stu-id="0831a-105">You also can send no arguments.</span></span> <span data-ttu-id="0831a-106">引数を渡さない場合、`params` リストの長さはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="0831a-106">If you send no arguments, the length of the `params` list is zero.</span></span>  
  
 <span data-ttu-id="0831a-107">1 つのメソッド宣言内では、`params` キーワード以後にパラメーターを追加できないため、1 つの `params` キーワードだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0831a-107">No additional parameters are permitted after the `params` keyword in a method declaration, and only one `params` keyword is permitted in a method declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0831a-108">例</span><span class="sxs-lookup"><span data-stu-id="0831a-108">Example</span></span>  
 <span data-ttu-id="0831a-109">次の例に示すように、さまざまな方法で `params` パラメーターに引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="0831a-109">The following example demonstrates various ways in which arguments can be sent to a `params` parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsMethodParams#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/params_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0831a-110">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0831a-110">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0831a-111">参照</span><span class="sxs-lookup"><span data-stu-id="0831a-111">See Also</span></span>  
 [<span data-ttu-id="0831a-112">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0831a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0831a-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0831a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0831a-114">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="0831a-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0831a-115">メソッド パラメーター</span><span class="sxs-lookup"><span data-stu-id="0831a-115">Method Parameters</span></span>](../../../csharp/language-reference/keywords/method-parameters.md)
