---
title: "プロパティとインデクサーの比較 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: 14
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
ms.openlocfilehash: 4bb2de1cfdcf4a8a7c847dfabe8d69124a4adf90
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="1252d-102">プロパティとインデクサーの比較 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1252d-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="1252d-103">インデクサーはプロパティと似ています。</span><span class="sxs-lookup"><span data-stu-id="1252d-103">Indexers are like properties.</span></span> <span data-ttu-id="1252d-104">次の表で示す相違点を除けば、プロパティのアクセサーに対して定義されているすべての規則が、インデクサーのアクセサーにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="1252d-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="1252d-105">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1252d-105">Property</span></span>|<span data-ttu-id="1252d-106">インデクサー</span><span class="sxs-lookup"><span data-stu-id="1252d-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1252d-107">パブリック データ メンバーのように、メソッドを呼び出せるようにします。</span><span class="sxs-lookup"><span data-stu-id="1252d-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="1252d-108">オブジェクト自体で配列表記を使用して、オブジェクトの内部コレクションの要素にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="1252d-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="1252d-109">シンプルな名前でアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="1252d-109">Accessed through a simple name.</span></span>|<span data-ttu-id="1252d-110">インデックスでアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="1252d-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="1252d-111">静的メンバーまたはインスタンス メンバーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="1252d-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="1252d-112">インスタンス メンバーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1252d-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="1252d-113">プロパティの [get](../../../csharp/language-reference/keywords/get.md) アクセサーにはパラメーターがありません。</span><span class="sxs-lookup"><span data-stu-id="1252d-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="1252d-114">インデクサーの `get` アクセサーには、インデクサーと同じ仮パラメーター リストがあります。</span><span class="sxs-lookup"><span data-stu-id="1252d-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="1252d-115">プロパティの [set](../../../csharp/language-reference/keywords/set.md) アクセサーには、暗黙の `value` パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1252d-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="1252d-116">インデクサーの `set` アクセサーには、インデクサーと同じ仮パラメーター リストのほか、[value](../../../csharp/language-reference/keywords/value.md) パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="1252d-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="1252d-117">[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)を持つ簡略化された構文がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="1252d-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="1252d-118">簡略化された構文がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="1252d-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1252d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1252d-119">See Also</span></span>  
 <span data-ttu-id="1252d-120">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1252d-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1252d-121">[インデクサー](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="1252d-121">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 [<span data-ttu-id="1252d-122">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1252d-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)

