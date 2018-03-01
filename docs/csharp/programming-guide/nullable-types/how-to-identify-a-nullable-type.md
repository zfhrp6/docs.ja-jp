---
title: "方法: Null 許容型を識別する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 610ed18308df02c5632361cd09ef94330dea598b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a><span data-ttu-id="1e03c-102">方法: Null 許容型を識別する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="1e03c-102">How to: Identify a Nullable Type (C# Programming Guide)</span></span>
<span data-ttu-id="1e03c-103">C# の [typeof](../../../csharp/language-reference/keywords/typeof.md) 演算子を使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="1e03c-103">You can use the C# [typeof](../../../csharp/language-reference/keywords/typeof.md) operator to create a <xref:System.Type> object that represents a Nullable type:</span></span>  
  
```  
System.Type type = typeof(int?);  
```  
  
 <span data-ttu-id="1e03c-104"><xref:System.Reflection> 名前空間のクラスおよびメソッドを使用して、Null 許容型を表す <xref:System.Type> オブジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1e03c-104">You can also use the classes and methods of the <xref:System.Reflection> namespace to generate <xref:System.Type> objects that represent Nullable types.</span></span> <span data-ttu-id="1e03c-105">ただし、実行時に <xref:System.Object.GetType%2A> メソッドまたは `is` 演算子を使用して Null 許容型の変数から型情報を取得しようとすると、Null 許容型自体ではなく、基になる型を表す <xref:System.Type> オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1e03c-105">However, if you try to obtain type information from Nullable variables at runtime by using the <xref:System.Object.GetType%2A> method or the `is` operator, the result is a <xref:System.Type> object that represents the underlying type, not the Nullable type itself.</span></span>  
  
 <span data-ttu-id="1e03c-106">Null 許容型に対して `GetType` を呼び出すと、型が暗黙的に <xref:System.Object> に変換されるときに、ボックス化操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1e03c-106">Calling `GetType` on a Nullable type causes a boxing operation to be performed when the type is implicitly converted to <xref:System.Object>.</span></span> <span data-ttu-id="1e03c-107">そのため、<xref:System.Object.GetType%2A> は常に、Null 許容型ではなく、基になる型を表す <xref:System.Type> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="1e03c-107">Therefore <xref:System.Object.GetType%2A> always returns a <xref:System.Type> object that represents the underlying type, not the Nullable type.</span></span>  
  
```  
int? i = 5;  
Type t = i.GetType();  
Console.WriteLine(t.FullName); //"System.Int32"  
```  
  
 <span data-ttu-id="1e03c-108">C# の [is](../../../csharp/language-reference/keywords/is.md) 演算子も Null 許容型の基になる型に作用します。</span><span class="sxs-lookup"><span data-stu-id="1e03c-108">The C# [is](../../../csharp/language-reference/keywords/is.md) operator also operates on a Nullable's underlying type.</span></span> <span data-ttu-id="1e03c-109">そのため、変数が Null 許容型であるかどうかを判別する際に `is` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="1e03c-109">Therefore you cannot use `is` to determine whether a variable is a Nullable type.</span></span> <span data-ttu-id="1e03c-110">次の例は、`is` 演算子が Nullable\<int> 変数を int として処理することを示しています。</span><span class="sxs-lookup"><span data-stu-id="1e03c-110">The following example shows that the `is` operator treats a Nullable\<int> variable as an int.</span></span>  
  
```  
static void Main(string[] args)  
{  
  int? i = 5;  
  if (i is int) // true  
    //…  
}  
```  
  
## <a name="example"></a><span data-ttu-id="1e03c-111">例</span><span class="sxs-lookup"><span data-stu-id="1e03c-111">Example</span></span>  
 <span data-ttu-id="1e03c-112">次のコードを使用して、<xref:System.Type> オブジェクトが Null 許容型を表しているかどうかを判別します。</span><span class="sxs-lookup"><span data-stu-id="1e03c-112">Use the following code to determine whether a <xref:System.Type> object represents a Nullable type.</span></span> <span data-ttu-id="1e03c-113">このトピックで前述したように、`Type` オブジェクトが <xref:System.Object.GetType%2A> の呼び出しから返された場合、このコードは常に false を返します。</span><span class="sxs-lookup"><span data-stu-id="1e03c-113">Remember that this code always returns false if the `Type` object was returned from a call to <xref:System.Object.GetType%2A>, as explained earlier in this topic.</span></span>  
  
```  
if (type.IsGenericType && type.GetGenericTypeDefinition() == typeof(Nullable<>)) {…}  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e03c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e03c-114">See Also</span></span>  
 [<span data-ttu-id="1e03c-115">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="1e03c-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="1e03c-116">Null 許容型のボックス化</span><span class="sxs-lookup"><span data-stu-id="1e03c-116">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)
