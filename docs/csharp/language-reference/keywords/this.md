---
title: "this (C# リファレンス)"
description: "this キーワード (C# リファレンス)"
keywords: "this (C#)、this キーワード (C#)、this キーワード (C# リファレンス)、this キーワード (C# 言語リファレンス)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.openlocfilehash: 1e764bbd85d06a3b1898f6574064b2844f6d6813
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="this-c-reference"></a><span data-ttu-id="ac3c8-104">this (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ac3c8-104">this (C# Reference)</span></span>
<span data-ttu-id="ac3c8-105">`this` キーワードはクラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac3c8-106">ここでは、クラス インスタンスでの `this` の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="ac3c8-107">拡張メソッドでの使用の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="ac3c8-108">`this` の一般的な使い方を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="ac3c8-109">似た名前によって非表示にされるメンバーを修飾する場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-109">To qualify members hidden by similar names, for example:</span></span>  
  
 <span data-ttu-id="ac3c8-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac3c8-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span></span>  
  
-   <span data-ttu-id="ac3c8-111">オブジェクトを他のメソッドにパラメーターとして渡す場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-111">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="ac3c8-112">インデクサーを宣言する場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-112">To declare indexers, for example:</span></span>  
  
 <span data-ttu-id="ac3c8-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac3c8-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span></span>  
  
 <span data-ttu-id="ac3c8-114">静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターがありません。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-114">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="ac3c8-115">静的メソッドで `this` を参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-115">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac3c8-116">例</span><span class="sxs-lookup"><span data-stu-id="ac3c8-116">Example</span></span>  
 <span data-ttu-id="ac3c8-117">この例では、似た名前によって非表示にされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-117">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="ac3c8-118">また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。</span><span class="sxs-lookup"><span data-stu-id="ac3c8-118">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 <span data-ttu-id="ac3c8-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="ac3c8-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ac3c8-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ac3c8-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ac3c8-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac3c8-121">See Also</span></span>  
 <span data-ttu-id="ac3c8-122">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac3c8-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="ac3c8-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac3c8-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ac3c8-124">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="ac3c8-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="ac3c8-125">[base](../../../csharp/language-reference/keywords/base.md) </span><span class="sxs-lookup"><span data-stu-id="ac3c8-125">[base](../../../csharp/language-reference/keywords/base.md) </span></span>  
 [<span data-ttu-id="ac3c8-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="ac3c8-126">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

