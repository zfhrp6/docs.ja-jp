---
title: struct (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="struct-c-reference"></a><span data-ttu-id="1165c-102">struct (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1165c-102">struct (C# Reference)</span></span>
<span data-ttu-id="1165c-103">`struct` 型は、通常、関連する変数 (四角形の座標やインベントリ内の項目の特性など) の小さなグループをカプセル化するのに使用される値型です。</span><span class="sxs-lookup"><span data-stu-id="1165c-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="1165c-104">次の例に単純な構造体の宣言を示します。</span><span class="sxs-lookup"><span data-stu-id="1165c-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="1165c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="1165c-105">Remarks</span></span>  
 <span data-ttu-id="1165c-106">構造体には、[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)、[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)、[フィールド](../../../csharp/programming-guide/classes-and-structs/fields.md)、[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)、[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)、[インデクサー](../../../csharp/programming-guide/indexers/index.md)、[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)、[イベント](../../../csharp/programming-guide/events/index.md)、および[入れ子にされた型](../../../csharp/programming-guide/classes-and-structs/nested-types.md)を含めることができます。ただし、複数のメンバーが必要な場合は、代わりに型をクラスに変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1165c-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="1165c-107">例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1165c-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="1165c-108">構造体はインターフェイスを実装できますが、別の構造体から継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="1165c-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="1165c-109">そのため、構造体メンバーを `protected` として宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="1165c-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="1165c-110">詳細については、「[構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1165c-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1165c-111">使用例</span><span class="sxs-lookup"><span data-stu-id="1165c-111">Examples</span></span>  
 <span data-ttu-id="1165c-112">例と詳細については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1165c-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1165c-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="1165c-113">C# Language Specification</span></span>  
 <span data-ttu-id="1165c-114">例については、「[構造体の使用](../../../csharp/programming-guide/classes-and-structs/using-structs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1165c-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1165c-115">参照</span><span class="sxs-lookup"><span data-stu-id="1165c-115">See Also</span></span>  
 [<span data-ttu-id="1165c-116">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="1165c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1165c-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1165c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1165c-118">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="1165c-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1165c-119">既定値の一覧表</span><span class="sxs-lookup"><span data-stu-id="1165c-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="1165c-120">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="1165c-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="1165c-121">型</span><span class="sxs-lookup"><span data-stu-id="1165c-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="1165c-122">値型</span><span class="sxs-lookup"><span data-stu-id="1165c-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="1165c-123">class</span><span class="sxs-lookup"><span data-stu-id="1165c-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="1165c-124">interface</span><span class="sxs-lookup"><span data-stu-id="1165c-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="1165c-125">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="1165c-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
