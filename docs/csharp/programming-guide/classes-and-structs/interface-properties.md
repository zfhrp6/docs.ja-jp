---
title: "インターフェイスのプロパティ (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
caps.latest.revision: 13
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
ms.openlocfilehash: 2b76cdc4e8419b08dcd95c3711eaead5513ae1d9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="f93aa-102">インターフェイスのプロパティ (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f93aa-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="f93aa-103">[interface](../../../csharp/language-reference/keywords/interface.md) でプロパティを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="f93aa-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="f93aa-104">インターフェイスのインデクサー アクセサーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f93aa-104">The following is an example of an interface indexer accessor:</span></span>  
  
 <span data-ttu-id="f93aa-105">[!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f93aa-105">[!code-cs[csProgGuideProperties#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_1.cs)]</span></span>  
  
 <span data-ttu-id="f93aa-106">インターフェイス プロパティのアクセサーには、本文はありません。</span><span class="sxs-lookup"><span data-stu-id="f93aa-106">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="f93aa-107">したがって、アクセサーの目的は、プロパティが読み取り/書き込み、読み取り専用、または書き込み専用のどれかを示すことです。</span><span class="sxs-lookup"><span data-stu-id="f93aa-107">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f93aa-108">例</span><span class="sxs-lookup"><span data-stu-id="f93aa-108">Example</span></span>  
 <span data-ttu-id="f93aa-109">この例では、インターフェイス `IEmployee` に読み取り/書き込み専用のプロパティ `Name` および読み取り専用のプロパティ `Counter` があります。</span><span class="sxs-lookup"><span data-stu-id="f93aa-109">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="f93aa-110">クラス `Employee` は `IEmployee` インターフェイスを実装し、これら 2 つのプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="f93aa-110">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="f93aa-111">プログラムは、新しい従業員の名前と現在の従業員の数を読み込んで、従業員の名前と計算した従業員番号を表示します。</span><span class="sxs-lookup"><span data-stu-id="f93aa-111">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="f93aa-112">メンバーが宣言されているインターフェイスを参照するプロパティの完全修飾名を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="f93aa-112">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="f93aa-113">例:</span><span class="sxs-lookup"><span data-stu-id="f93aa-113">For example:</span></span>  
  
 <span data-ttu-id="f93aa-114">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f93aa-114">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span></span>  
  
 <span data-ttu-id="f93aa-115">これは、[明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f93aa-115">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="f93aa-116">たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じ `Name` プロパティを持っている場合、明示的なインターフェイス メンバーの実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="f93aa-116">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="f93aa-117">つまり、次のプロパティの宣言があります。</span><span class="sxs-lookup"><span data-stu-id="f93aa-117">That is, the following property declaration:</span></span>  
  
 <span data-ttu-id="f93aa-118">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f93aa-118">[!code-cs[csProgGuideProperties#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_2.cs)]</span></span>  
  
 <span data-ttu-id="f93aa-119">これは、`IEmployee` インターフェイスで `Name` プロパティを実装します。次の宣言があります。</span><span class="sxs-lookup"><span data-stu-id="f93aa-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 <span data-ttu-id="f93aa-120">[!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f93aa-120">[!code-cs[csProgGuideProperties#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_3.cs)]</span></span>  
  
 <span data-ttu-id="f93aa-121">これは、`ICitizen` インターフェイスで `Name` プロパティを実装します。</span><span class="sxs-lookup"><span data-stu-id="f93aa-121">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 <span data-ttu-id="f93aa-122">[!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="f93aa-122">[!code-cs[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]</span></span>  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="f93aa-123">出力例</span><span class="sxs-lookup"><span data-stu-id="f93aa-123">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="f93aa-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f93aa-124">See Also</span></span>  
 <span data-ttu-id="f93aa-125">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f93aa-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f93aa-126">[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md) </span><span class="sxs-lookup"><span data-stu-id="f93aa-126">[Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) </span></span>  
 <span data-ttu-id="f93aa-127">[プロパティの使用](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span><span class="sxs-lookup"><span data-stu-id="f93aa-127">[Using Properties](../../../csharp/programming-guide/classes-and-structs/using-properties.md) </span></span>  
 <span data-ttu-id="f93aa-128">[プロパティとインデクサーの比較](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md) </span><span class="sxs-lookup"><span data-stu-id="f93aa-128">[Comparison Between Properties and Indexers](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md) </span></span>  
 <span data-ttu-id="f93aa-129">[インデクサー](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="f93aa-129">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="f93aa-130">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f93aa-130">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)

