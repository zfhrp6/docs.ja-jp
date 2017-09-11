---
title: "get (C# リファレンス)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
dev_langs:
- CSharp
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 11
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
ms.openlocfilehash: 88603864ae0a31a193cab211b8ce8061ec63c169
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="get-c-reference"></a><span data-ttu-id="709d7-102">get (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="709d7-102">get (C# Reference)</span></span>

<span data-ttu-id="709d7-103">`get` キーワードは、プロパティの*アクセサー*メソッド、またはプロパティ値かインデクサー要素を返すインデクサーを定義します。</span><span class="sxs-lookup"><span data-stu-id="709d7-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="709d7-104">詳しくは、「[プロパティ (C# プログラミング ガイド)](../../../csharp/programming-guide/classes-and-structs/properties.md)」、「[自動実装するプロパティ (C# プログラミング ガイド)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー (C# プログラミング ガイド)](../../../csharp/programming-guide/indexers/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="709d7-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="709d7-105">次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `set` アクセサーを定義します。</span><span class="sxs-lookup"><span data-stu-id="709d7-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="709d7-106">`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻します。</span><span class="sxs-lookup"><span data-stu-id="709d7-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 <span data-ttu-id="709d7-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="709d7-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span></span>  
  
<span data-ttu-id="709d7-108">前の例のように、多くの場合、`get` アクセサーは値を返す 1 つのステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="709d7-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="709d7-109">C# 7 以降では、式形式のメンバーとして `get` アクセサーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="709d7-109">Starting with C# 7, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="709d7-110">次の例では、`get` アクセサーと `set` アクセサーの両方を、式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="709d7-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 <span data-ttu-id="709d7-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="709d7-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span></span>   
 
<span data-ttu-id="709d7-112">プロパティの `get` および `set` アクセサーがプライベート バッキング フィールドの値を設定または取得する以外の操作を実行しない単純なケースでは、自動実装プロパティに対する C# コンパイラのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="709d7-112">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="709d7-113">次の例では、自動実装プロパティとして `Hours` を実装しています。</span><span class="sxs-lookup"><span data-stu-id="709d7-113">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 <span data-ttu-id="709d7-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="709d7-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="709d7-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="709d7-115">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="709d7-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="709d7-116">See Also</span></span>  
 <span data-ttu-id="709d7-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="709d7-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="709d7-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="709d7-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="709d7-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="709d7-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>

