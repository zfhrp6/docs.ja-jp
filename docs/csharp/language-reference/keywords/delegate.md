---
title: "delegate (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
dev_langs:
- CSharp
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 402eedd0c59b5c95e1a9b44faca66ccb4d4e04e7
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="delegate-c-reference"></a><span data-ttu-id="802bf-102">delegate (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="802bf-102">delegate (C# Reference)</span></span>
<span data-ttu-id="802bf-103">デリゲート型の宣言は、メソッド シグネチャに似ています。</span><span class="sxs-lookup"><span data-stu-id="802bf-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="802bf-104">戻り値 1 つのほか、任意の型のパラメーターをいくつでも指定することができます。</span><span class="sxs-lookup"><span data-stu-id="802bf-104">It has a return value and any number of parameters of any type:</span></span>  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="802bf-105">`delegate` は、名前付きメソッドまたは匿名メソッドをカプセル化することができる参照型です。</span><span class="sxs-lookup"><span data-stu-id="802bf-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="802bf-106">デリゲートは C++ の関数ポインターに似ていますが、タイプ セーフであり安全です。</span><span class="sxs-lookup"><span data-stu-id="802bf-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="802bf-107">デリゲートの使い方については、[デリゲート](../../../csharp/programming-guide/delegates/index.md)と[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="802bf-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="802bf-108">コメント</span><span class="sxs-lookup"><span data-stu-id="802bf-108">Remarks</span></span>  
 <span data-ttu-id="802bf-109">デリゲートは[イベント](../../../csharp/programming-guide/events/index.md)の土台となる働きをします。</span><span class="sxs-lookup"><span data-stu-id="802bf-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="802bf-110">デリゲートは名前付きメソッドまたは匿名メソッドに関連付けることによって、インスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="802bf-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="802bf-111">詳細については、[名前付きメソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)と[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="802bf-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="802bf-112">デリゲートは、適合する入力パラメーターと戻り値の型を持ったメソッドまたはラムダ式でインスタンス化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="802bf-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="802bf-113">メソッドのシグネチャでどの程度の変性が許容されるかについて詳しくは、[デリゲートの変性](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="802bf-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca).</span></span> <span data-ttu-id="802bf-114">匿名メソッドで使用する場合は、デリゲートとそれに関連付けるコードとを一緒に宣言します。</span><span class="sxs-lookup"><span data-stu-id="802bf-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="802bf-115">このセクションでは、その両方の方法でデリゲートをインスタンス化しています。</span><span class="sxs-lookup"><span data-stu-id="802bf-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="802bf-116">例</span><span class="sxs-lookup"><span data-stu-id="802bf-116">Example</span></span>  
 <span data-ttu-id="802bf-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="802bf-117">[!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="802bf-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="802bf-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="802bf-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="802bf-119">See Also</span></span>  
 <span data-ttu-id="802bf-120">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-120">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="802bf-121">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="802bf-122">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-122">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="802bf-123">[参照型](../../../csharp/language-reference/keywords/reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-123">[Reference Types](../../../csharp/language-reference/keywords/reference-types.md) </span></span>  
 <span data-ttu-id="802bf-124">[デリゲート](../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-124">[Delegates](../../../csharp/programming-guide/delegates/index.md) </span></span>  
 <span data-ttu-id="802bf-125">[イベント](../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-125">[Events](../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="802bf-126">[名前付きメソッドを使用したデリゲートと匿名メソッド](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="802bf-126">[Delegates with Named vs. Anonymous Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) </span></span>  
 [<span data-ttu-id="802bf-127">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="802bf-127">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)

