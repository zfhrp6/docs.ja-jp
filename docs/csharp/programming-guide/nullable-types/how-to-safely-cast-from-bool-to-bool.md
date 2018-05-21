---
title: '方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: 18f44018621182427199dee56146f29b8d3068f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="06c13-102">方法: bool? から bool に安全にキャストする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="06c13-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="06c13-103">Null 許容 `bool?` 型は、`true`、`false`、`null` の 3 つの異なる値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="06c13-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="06c13-104">そのため、`bool?` 型は、`if`、`for`、`while` などの条件文で使用できません。</span><span class="sxs-lookup"><span data-stu-id="06c13-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="06c13-105">たとえば、次のコードはコンパイラ エラーになります。</span><span class="sxs-lookup"><span data-stu-id="06c13-105">For example, the following code causes a compiler error.</span></span>  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="06c13-106">コンパイルできないのは、条件文のコンテキストで `null` の意味があいまいだからです。</span><span class="sxs-lookup"><span data-stu-id="06c13-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="06c13-107">条件付きステートメントで `bool?` を使用するにはまず、その <xref:System.Nullable%601.HasValue%2A> プロパティをチェックしてその値が `null` でないことを確認します。次に、`bool` にキャストします。</span><span class="sxs-lookup"><span data-stu-id="06c13-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="06c13-108">詳細については、「[bool](../../../csharp/language-reference/keywords/bool.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06c13-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="06c13-109">`bool?` でキャストを実行するときに値が `null` になっていると、条件テストで <xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="06c13-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="06c13-110">次の例は、`bool?` から `bool` に安全にキャストするための 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="06c13-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="06c13-111">例</span><span class="sxs-lookup"><span data-stu-id="06c13-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="06c13-112">参照</span><span class="sxs-lookup"><span data-stu-id="06c13-112">See Also</span></span>  
 [<span data-ttu-id="06c13-113">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="06c13-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06c13-114">リテラル キーワード</span><span class="sxs-lookup"><span data-stu-id="06c13-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="06c13-115">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="06c13-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="06c13-116">??演算子</span><span class="sxs-lookup"><span data-stu-id="06c13-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
