---
title: "this (C# リファレンス)"
description: "this キーワード (C# リファレンス)"
keywords: "this (C#)、this キーワード (C#)、this キーワード (C# リファレンス)、this キーワード (C# 言語リファレンス)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="3bf31-104">this (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="3bf31-104">this (C# Reference)</span></span>
<span data-ttu-id="3bf31-105">`this` キーワードはクラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="3bf31-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3bf31-106">ここでは、クラス インスタンスでの `this` の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="3bf31-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="3bf31-107">拡張メソッドでの使用の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bf31-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="3bf31-108">`this` の一般的な使い方を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3bf31-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="3bf31-109">似た名前によって非表示にされるメンバーを修飾する場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3bf31-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="3bf31-110">オブジェクトを他のメソッドにパラメーターとして渡す場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3bf31-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="3bf31-111">インデクサーを宣言する場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3bf31-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="3bf31-112">静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターがありません。</span><span class="sxs-lookup"><span data-stu-id="3bf31-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="3bf31-113">静的メソッドで `this` を参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="3bf31-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bf31-114">例</span><span class="sxs-lookup"><span data-stu-id="3bf31-114">Example</span></span>  
 <span data-ttu-id="3bf31-115">この例では、似た名前によって非表示にされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="3bf31-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="3bf31-116">また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。</span><span class="sxs-lookup"><span data-stu-id="3bf31-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3bf31-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="3bf31-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3bf31-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bf31-118">See Also</span></span>  
 [<span data-ttu-id="3bf31-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="3bf31-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3bf31-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="3bf31-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3bf31-121">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="3bf31-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3bf31-122">base</span><span class="sxs-lookup"><span data-stu-id="3bf31-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="3bf31-123">メソッド</span><span class="sxs-lookup"><span data-stu-id="3bf31-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
