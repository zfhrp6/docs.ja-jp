---
title: this (C# リファレンス)
description: this キーワード (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 04496079114be45388926993b67e8f1d3f2e9f15
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172036"
---
# <a name="this-c-reference"></a><span data-ttu-id="9f64e-103">this (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9f64e-103">this (C# Reference)</span></span>
<span data-ttu-id="9f64e-104">`this` キーワードはクラスの現在のインスタンスを参照します。拡張メソッドの最初のパラメーターの修飾子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="9f64e-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f64e-105">ここでは、クラス インスタンスでの `this` の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="9f64e-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="9f64e-106">拡張メソッドでの使用の詳細については、「[拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9f64e-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="9f64e-107">`this` の一般的な使い方を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9f64e-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="9f64e-108">似た名前によって非表示にされるメンバーを修飾する場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9f64e-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="9f64e-109">オブジェクトを他のメソッドにパラメーターとして渡す場合は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9f64e-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="9f64e-110">インデクサーを宣言する場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9f64e-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="9f64e-111">静的メンバー関数は、クラス レベルで存在し、オブジェクトの一部ではないため、`this` ポインターがありません。</span><span class="sxs-lookup"><span data-stu-id="9f64e-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="9f64e-112">静的メソッドで `this` を参照するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="9f64e-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f64e-113">例</span><span class="sxs-lookup"><span data-stu-id="9f64e-113">Example</span></span>  
 <span data-ttu-id="9f64e-114">この例では、似た名前によって非表示にされている `Employee` クラスのメンバー `name` と `alias` を修飾するために `this` が使用されています。</span><span class="sxs-lookup"><span data-stu-id="9f64e-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="9f64e-115">また、別のクラスに属するメソッド `CalcTax` にオブジェクトを渡すためにも使用されています。</span><span class="sxs-lookup"><span data-stu-id="9f64e-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9f64e-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9f64e-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9f64e-117">参照</span><span class="sxs-lookup"><span data-stu-id="9f64e-117">See Also</span></span>  
 [<span data-ttu-id="9f64e-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="9f64e-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9f64e-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9f64e-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9f64e-120">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="9f64e-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9f64e-121">base</span><span class="sxs-lookup"><span data-stu-id="9f64e-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="9f64e-122">メソッド</span><span class="sxs-lookup"><span data-stu-id="9f64e-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
