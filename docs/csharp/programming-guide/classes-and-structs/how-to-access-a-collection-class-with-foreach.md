---
title: "方法: foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
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
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="89150-102">方法: foreach を使用してコレクション クラスにアクセスする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="89150-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="89150-103">次のコード例では、[foreach](../../../csharp/language-reference/keywords/foreach-in.md) で使用できる非ジェネリック コレクション クラスを記述する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="89150-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="89150-104">この例では、文字列トークナイザー クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="89150-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89150-105">この例では、汎用のコレクション クラスを使用できないときのみに推奨される方法を示します。</span><span class="sxs-lookup"><span data-stu-id="89150-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="89150-106"><xref:System.Collections.Generic.IEnumerable%601> をサポートするタイプ セーフの汎用的なコレクション クラスを実装する方法の例は、「[反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89150-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="89150-107">この例では、次のコード セグメントが `Tokens` クラスを使用し、"This is a sample sentence." という文を </span><span class="sxs-lookup"><span data-stu-id="89150-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="89150-108">' ' と '-' の区切りを使用してトークンに分割しています。</span><span class="sxs-lookup"><span data-stu-id="89150-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="89150-109">その後、コードでは `foreach` ステートメントを使用し、それらのトークンを示します。</span><span class="sxs-lookup"><span data-stu-id="89150-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 <span data-ttu-id="89150-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="89150-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="89150-111">例</span><span class="sxs-lookup"><span data-stu-id="89150-111">Example</span></span>  
 <span data-ttu-id="89150-112">`Tokens` クラスは、内部でトークンの保存に配列を使用します。</span><span class="sxs-lookup"><span data-stu-id="89150-112">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="89150-113">配列は <xref:System.Collections.IEnumerator> と <xref:System.Collections.IEnumerable> を実装するため、このコード例では、`Tokens` クラスで定義する代わりに、配列の列挙メソッド (<xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、<xref:System.Collections.IEnumerator.Current%2A>) を使用することができました。</span><span class="sxs-lookup"><span data-stu-id="89150-113">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="89150-114">その定義方法およびそれらの動作を示すために、例にはメソッドの定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="89150-114">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 <span data-ttu-id="89150-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="89150-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span></span>  
  
 <span data-ttu-id="89150-116">C# の場合、<xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を実装しなくてもコレクション クラスは `foreach` 互換になります。</span><span class="sxs-lookup"><span data-stu-id="89150-116">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="89150-117">クラスに必須の <xref:System.Collections.IEnumerable.GetEnumerator%2A>、<xref:System.Collections.IEnumerator.MoveNext%2A>、<xref:System.Collections.IEnumerator.Reset%2A>、<xref:System.Collections.IEnumerator.Current%2A> メンバーがある場合、`foreach` と連動します。</span><span class="sxs-lookup"><span data-stu-id="89150-117">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="89150-118">インターフェイスを省略すると、<xref:System.Object> よりも限定的な `Current` 用の戻り値の型を定義することが可能になると言う利点があります。</span><span class="sxs-lookup"><span data-stu-id="89150-118">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="89150-119">これにより、タイプ セーフとなります。</span><span class="sxs-lookup"><span data-stu-id="89150-119">This provides type safety.</span></span>  
  
 <span data-ttu-id="89150-120">たとえば、前の例の下記の行を変更します。</span><span class="sxs-lookup"><span data-stu-id="89150-120">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="89150-121">`Current` では、文字列を返すので、`foreach` ステートメントで互換性のない型が使用されたとき、コンパイラが次のコードのとおりそれを検出できます。</span><span class="sxs-lookup"><span data-stu-id="89150-121">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="89150-122"><xref:System.Collections.IEnumerable> と <xref:System.Collections.IEnumerator> を省略した場合、コレクション クラスが `foreach` ステートメント、同等のステートメントや他の共通言語ランタイム言語と互換性がなくなるという欠点があります。</span><span class="sxs-lookup"><span data-stu-id="89150-122">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89150-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="89150-123">See Also</span></span>  
 <span data-ttu-id="89150-124"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="89150-124"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="89150-125">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="89150-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="89150-126">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="89150-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="89150-127">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="89150-127">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 [<span data-ttu-id="89150-128">コレクション</span><span class="sxs-lookup"><span data-stu-id="89150-128">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

