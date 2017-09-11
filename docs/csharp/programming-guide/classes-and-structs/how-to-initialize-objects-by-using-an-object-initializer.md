---
title: "方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
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
ms.openlocfilehash: 01f2391680d9236b42f0d015b944b8f12455d0c8
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="93076-102">方法: オブジェクト初期化子を使用してオブジェクトを初期化する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="93076-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="93076-103">オブジェクト初期化子を使用すると、型のコンストラクターを明示的に呼び出さずに、宣言的な方法で型オブジェクトを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="93076-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
 <span data-ttu-id="93076-104">次の例は、指定したオブジェクトでオブジェクト初期化子を使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93076-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="93076-105">コンパイラは、最初に既定のインスタンス コンストラクターにアクセスし、メンバーの初期化を処理することで、オブジェクト初期化子を処理します。</span><span class="sxs-lookup"><span data-stu-id="93076-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="93076-106">そのため、クラスで既定のコンストラクターが `private` として宣言されている場合、パブリック アクセスを必要とするオブジェクト初期化子は失敗します。</span><span class="sxs-lookup"><span data-stu-id="93076-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>  
  
 <span data-ttu-id="93076-107">匿名型を定義する場合は、オブジェクト初期化子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93076-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="93076-108">詳細については、「[方法: クエリで要素のプロパティのサブセットを返す](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93076-108">For more information, see [How to: Return Subsets of Element Properties in a Query](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93076-109">例</span><span class="sxs-lookup"><span data-stu-id="93076-109">Example</span></span>  
 <span data-ttu-id="93076-110">次の例は、オブジェクト初期化子を使用して、新しい `StudentName` 型を初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93076-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span>  
  
 <span data-ttu-id="93076-111">[!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="93076-111">[!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="93076-112">例</span><span class="sxs-lookup"><span data-stu-id="93076-112">Example</span></span>  
 <span data-ttu-id="93076-113">次の例は、コレクション初期化子を使用して、`StudentName` 型のコレクションを初期化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="93076-113">The following example shows how to initialize a collection of `StudentName` types by using a collection initializer.</span></span> <span data-ttu-id="93076-114">コレクション初期化子は、コンマで区切られた一連のオブジェクト初期化子です。</span><span class="sxs-lookup"><span data-stu-id="93076-114">Note that a collection initializer is a series of comma-separated object initializers.</span></span>  
  
 <span data-ttu-id="93076-115">[!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="93076-115">[!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93076-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="93076-116">Compiling the Code</span></span>  
 <span data-ttu-id="93076-117">このコードを実行するには、クラスをコピーし、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] で作成した Visual C# コンソール アプリケーション プロジェクトに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="93076-117">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)].</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="93076-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="93076-118">See Also</span></span>  
 <span data-ttu-id="93076-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="93076-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="93076-120">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="93076-120">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

