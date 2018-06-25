---
title: インターフェイスのインデクサー (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 120b6e72a6ab906437c593d6eb33024d1df8f52b
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207966"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="9b938-102">インターフェイスのインデクサー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9b938-102">Indexers in Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="9b938-103">[interface](../../../csharp/language-reference/keywords/interface.md) でインデクサーを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="9b938-103">Indexers can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="9b938-104">インターフェイスのインデクサーのアクセサーは、[クラス](../../../csharp/language-reference/keywords/class.md)のインデクサーのアクセサーと次の点で異なります。</span><span class="sxs-lookup"><span data-stu-id="9b938-104">Accessors of interface indexers differ from the accessors of [class](../../../csharp/language-reference/keywords/class.md) indexers in the following ways:</span></span>  
  
-   <span data-ttu-id="9b938-105">インターフェイスのアクセサーは、修飾子は使用しません。</span><span class="sxs-lookup"><span data-stu-id="9b938-105">Interface accessors do not use modifiers.</span></span>  
  
-   <span data-ttu-id="9b938-106">インターフェイスのアクセサーには、本文はありません。</span><span class="sxs-lookup"><span data-stu-id="9b938-106">An interface accessor does not have a body.</span></span>  
  
 <span data-ttu-id="9b938-107">したがって、アクセサーの目的は、インデクサーが読み取り/書き込み、読み取り専用、または書き込み専用のどれかを示すことです。</span><span class="sxs-lookup"><span data-stu-id="9b938-107">Thus, the purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span>  
  
 <span data-ttu-id="9b938-108">インターフェイスのインデクサー アクセサーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9b938-108">The following is an example of an interface indexer accessor:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_1.cs)]  
  
 <span data-ttu-id="9b938-109">インデクサーのシグネチャは、同じインターフェイスで宣言されている他のすべてのインデクサーの署名とは異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b938-109">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b938-110">例</span><span class="sxs-lookup"><span data-stu-id="9b938-110">Example</span></span>  
 <span data-ttu-id="9b938-111">次の例では、インターフェイスのインデクサーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9b938-111">The following example shows how to implement interface indexers.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/indexers-in-interfaces_2.cs)]  
  
 <span data-ttu-id="9b938-112">前の例では、インターフェイス メンバーの完全修飾名を使用して明示的なインターフェイス メンバーの実装を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9b938-112">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="9b938-113">例:</span><span class="sxs-lookup"><span data-stu-id="9b938-113">For example:</span></span>  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="9b938-114">ただし、完全修飾名は、クラスが同じインデクサーの署名を持つ 2 つ以上のインターフェイスを実装するときにあいまいさを避けるためにのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="9b938-114">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="9b938-115">たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じインデクサーの署名を持っている場合、明示的なインターフェイス メンバーの実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b938-115">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="9b938-116">つまり、次のインデクサーの宣言があります。</span><span class="sxs-lookup"><span data-stu-id="9b938-116">That is, the following indexer declaration:</span></span>  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 <span data-ttu-id="9b938-117">これは、`IEmployee` インターフェイス上でインデクサーを実装します。次の宣言があります。</span><span class="sxs-lookup"><span data-stu-id="9b938-117">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 <span data-ttu-id="9b938-118">これは、`ICitizen` インターフェイスでインデクサーを実装します。</span><span class="sxs-lookup"><span data-stu-id="9b938-118">implements the indexer on the `ICitizen` interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b938-119">参照</span><span class="sxs-lookup"><span data-stu-id="9b938-119">See Also</span></span>  
 [<span data-ttu-id="9b938-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9b938-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b938-121">インデクサー</span><span class="sxs-lookup"><span data-stu-id="9b938-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="9b938-122">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9b938-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="9b938-123">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b938-123">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
