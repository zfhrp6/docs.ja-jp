---
title: Null 条件演算子 (C# および Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: da771fa4a2a89dca308508ea81ef8e0060efa7f0
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="2ef92-102">?.</span><span class="sxs-lookup"><span data-stu-id="2ef92-102">?.</span></span> <span data-ttu-id="2ef92-103">および ?[] Null 条件演算子 (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ef92-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="2ef92-104">メンバー アクセス (`?.`) またはインデックス (`?[]`) 操作を実行する前に、左の演算子の値を null に対してテストします。左側のオペランドが `null` に評価される場合、`null` が返されます。</span><span class="sxs-lookup"><span data-stu-id="2ef92-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="2ef92-105">これらの演算子を使用すると、null チェックの処理のために記述するコードを少なくすることができます (特に、データ構造を下っていく場合)。</span><span class="sxs-lookup"><span data-stu-id="2ef92-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="2ef92-106">Null 条件演算子はショートサーキットです。</span><span class="sxs-lookup"><span data-stu-id="2ef92-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="2ef92-107">条件付きのメンバー アクセスおよびインデックス操作のチェーンの 1 つの演算が null を返す場合、チェーンの実行の残りの部分は停止します。</span><span class="sxs-lookup"><span data-stu-id="2ef92-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="2ef92-108">次の例では、`A`、`B`、または `C` が null と評価された場合、`E` は実行されません。</span><span class="sxs-lookup"><span data-stu-id="2ef92-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="2ef92-109">null 条件メンバー アクセスの別の用途は、はるかに少ないコードのスレッド セーフな方法でデリゲートを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="2ef92-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="2ef92-110">従来の方法には、次のようなコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="2ef92-110">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="2ef92-111">新しい方法は格段に単純です。</span><span class="sxs-lookup"><span data-stu-id="2ef92-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="2ef92-112">コンパイラが `PropertyChanged` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="2ef92-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="2ef92-113">null 条件デリゲート呼び出し構文 `PropertyChanged?(e)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ef92-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="2ef92-114">言語仕様</span><span class="sxs-lookup"><span data-stu-id="2ef92-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="2ef92-115">詳しくは、「[Visual Basic 言語リファレンス](../../../visual-basic/language-reference/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2ef92-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ef92-116">参照</span><span class="sxs-lookup"><span data-stu-id="2ef92-116">See Also</span></span>  
 [<span data-ttu-id="2ef92-117">?? (Null 合体演算子)</span><span class="sxs-lookup"><span data-stu-id="2ef92-117">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="2ef92-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="2ef92-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2ef92-119">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2ef92-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2ef92-120">Visual Basic プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2ef92-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
