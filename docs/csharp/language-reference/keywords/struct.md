---
title: "struct (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- struct_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
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
ms.openlocfilehash: 309e68a57e1ee869850d960ffaac6cf35eb6e260
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="struct-c-reference"></a><span data-ttu-id="79a1b-102">struct (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="79a1b-102">struct (C# Reference)</span></span>
<span data-ttu-id="79a1b-103">`struct` 型は、通常、関連する変数 (四角形の座標やインベントリ内の項目の特性など) の小さなグループをカプセル化するのに使用される値型です。</span><span class="sxs-lookup"><span data-stu-id="79a1b-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="79a1b-104">次の例に単純な構造体の宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="79a1b-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="79a1b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="79a1b-105">Remarks</span></span>  
 <span data-ttu-id="79a1b-106">構造体には、[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)、[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)、[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[イベント](../../../csharp/programming-guide/events/index.md)、および[入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)を含めることができます。ただし、複数のメンバーが必要な場合は、代わりに型をクラスに変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="79a1b-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="79a1b-107">例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a1b-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="79a1b-108">構造体はインターフェイスを実装できますが、別の構造体から継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="79a1b-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="79a1b-109">そのため、構造体メンバーを `protected` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="79a1b-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="79a1b-110">詳細については、「[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a1b-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="79a1b-111">例</span><span class="sxs-lookup"><span data-stu-id="79a1b-111">Examples</span></span>  
 <span data-ttu-id="79a1b-112">例と詳細については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a1b-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="79a1b-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="79a1b-113">C# Language Specification</span></span>  
 <span data-ttu-id="79a1b-114">例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79a1b-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a1b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="79a1b-115">See Also</span></span>  
 <span data-ttu-id="79a1b-116">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="79a1b-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="79a1b-118">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="79a1b-119">[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-119">[Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md) </span></span>  
 <span data-ttu-id="79a1b-120">[組み込み型の一覧表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-120">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="79a1b-121">[型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-121">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="79a1b-122">[値型](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-122">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="79a1b-123">[class](../../../csharp/language-reference/keywords/class.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-123">[class](../../../csharp/language-reference/keywords/class.md) </span></span>  
 <span data-ttu-id="79a1b-124">[interface](../../../csharp/language-reference/keywords/interface.md) </span><span class="sxs-lookup"><span data-stu-id="79a1b-124">[interface](../../../csharp/language-reference/keywords/interface.md) </span></span>  
 [<span data-ttu-id="79a1b-125">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="79a1b-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)

