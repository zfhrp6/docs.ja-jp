---
title: "set (C# リファレンス)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords: set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b810280724dcf608859bfa455947a75ce64b7abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-c-reference"></a><span data-ttu-id="aafc0-102">set (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="aafc0-102">set (C# Reference)</span></span>
<span data-ttu-id="aafc0-103">`set` キーワードは、プロパティまたはインデクサーで、プロパティ値またはインデクサーの要素値を割り当てる "*アクセサー*" メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="aafc0-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="aafc0-104">使用例を含む詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」、「[自動実装プロパティ](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー](../../../csharp/programming-guide/indexers/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aafc0-104">For more information and examples, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="aafc0-105">次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `set` アクセサーを定義しています。</span><span class="sxs-lookup"><span data-stu-id="aafc0-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="aafc0-106">また、`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻しています。</span><span class="sxs-lookup"><span data-stu-id="aafc0-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[set#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  

<span data-ttu-id="aafc0-107">多くの場合、前の例のように、`set` アクセサーは値を返す 1 つのステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="aafc0-107">Often, the `set` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="aafc0-108">C# 7 以降では、式形式のメンバーとして `set` アクセサーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="aafc0-108">Starting with C# 7, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="aafc0-109">次の例では、`get` アクセサーと `set` アクセサーの両方を、式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="aafc0-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

 [!code-csharp[set#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
    
<span data-ttu-id="aafc0-110">プロパティの `get` アクセサーと `set` アクセサーがプライベート バッキング フィールドの値の設定と取得以外の操作を実行しない単純な場合では、自動実装プロパティに対する C# コンパイラのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="aafc0-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="aafc0-111">次の例では、自動実装プロパティとして `Hours` を実装しています。</span><span class="sxs-lookup"><span data-stu-id="aafc0-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[set#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
    
## <a name="c-language-specification"></a><span data-ttu-id="aafc0-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="aafc0-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aafc0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="aafc0-113">See Also</span></span>  
 [<span data-ttu-id="aafc0-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="aafc0-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aafc0-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="aafc0-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aafc0-116">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="aafc0-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="aafc0-117">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aafc0-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
