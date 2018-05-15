---
title: get (C# リファレンス)
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 671cadce0bd120ec0728562ec448b2ce6edf2dd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="get-c-reference"></a><span data-ttu-id="c5f2b-102">get (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="c5f2b-102">get (C# Reference)</span></span>

<span data-ttu-id="c5f2b-103">`get` キーワードは、プロパティの*アクセサー*メソッド、またはプロパティ値かインデクサー要素を返すインデクサーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="c5f2b-104">詳しくは、「[プロパティ (C# プログラミング ガイド)](../../../csharp/programming-guide/classes-and-structs/properties.md)」、「[自動実装するプロパティ (C# プログラミング ガイド)](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)」、および「[インデクサー (C# プログラミング ガイド)](../../../csharp/programming-guide/indexers/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="c5f2b-105">次の例では、`Seconds` という名前のプロパティの `get` アクセサーと `set` アクセサーを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="c5f2b-106">また、`_seconds` という名前のプライベート フィールドを使って、プロパティの値を戻しています。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="c5f2b-107">多くの場合、前の例のように、`get` アクセサーは値を返す 1 つのステートメントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="c5f2b-108">C# 7.0 以降では、式形式のメンバーとして `get` アクセサーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="c5f2b-109">次の例では、`get` アクセサーと `set` アクセサーの両方を、式形式のメンバーとして実装しています。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="c5f2b-110">プロパティの `get` アクセサーと `set` アクセサーがプライベート バッキング フィールドの値の設定と取得以外の操作を実行しない単純な場合では、自動実装プロパティに対する C# コンパイラのサポートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="c5f2b-111">次の例では、自動実装プロパティとして `Hours` を実装しています。</span><span class="sxs-lookup"><span data-stu-id="c5f2b-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c5f2b-112">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="c5f2b-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5f2b-113">参照</span><span class="sxs-lookup"><span data-stu-id="c5f2b-113">See Also</span></span>  
 [<span data-ttu-id="c5f2b-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="c5f2b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c5f2b-115">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="c5f2b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="c5f2b-116">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="c5f2b-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>
