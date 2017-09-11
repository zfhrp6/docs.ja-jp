---
title: "typeof (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
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
ms.openlocfilehash: fdb335e44a5a3634520d3a86495a4508597b4f70
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="typeof-c-reference"></a><span data-ttu-id="b5eec-102">typeof (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="b5eec-102">typeof (C# Reference)</span></span>
<span data-ttu-id="b5eec-103">型の `System.Type` オブジェクトを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5eec-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="b5eec-104">`typeof` 式は次の形式になります。</span><span class="sxs-lookup"><span data-stu-id="b5eec-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b5eec-105">コメント</span><span class="sxs-lookup"><span data-stu-id="b5eec-105">Remarks</span></span>  
 <span data-ttu-id="b5eec-106">式の実行時の型を取得する場合は、次の例のように、.NET Framework のメソッド <xref:System.Object.GetType%2A> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5eec-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="b5eec-107">`typeof` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="b5eec-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="b5eec-108">`typeof` 演算子は、オープン ジェネリック型に対しても使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5eec-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="b5eec-109">複数の型パラメーターを持つ型には、適切な数のコンマを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5eec-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="b5eec-110">次の例は、メソッドの戻り値の型がジェネリック <xref:System.Collections.Generic.IEnumerable%601> であるかどうかを確認する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5eec-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="b5eec-111">ここでは、メソッドが MethodInfo 型のインスタンスであると仮定します。</span><span class="sxs-lookup"><span data-stu-id="b5eec-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="b5eec-112">例</span><span class="sxs-lookup"><span data-stu-id="b5eec-112">Example</span></span>  
 <span data-ttu-id="b5eec-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b5eec-113">[!code-cs[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5eec-114">例</span><span class="sxs-lookup"><span data-stu-id="b5eec-114">Example</span></span>  
 <span data-ttu-id="b5eec-115">このサンプルでは、<xref:System.Object.GetType%2A> メソッドを使用して、数値計算結果の格納に使用される型を確認しています。</span><span class="sxs-lookup"><span data-stu-id="b5eec-115">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="b5eec-116">これは、結果の数のストレージ要件によって変わります。</span><span class="sxs-lookup"><span data-stu-id="b5eec-116">This depends on the storage requirements of the resulting number.</span></span>  
  
 <span data-ttu-id="b5eec-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b5eec-117">[!code-cs[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b5eec-118">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b5eec-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5eec-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5eec-119">See Also</span></span>  
 <span data-ttu-id="b5eec-120"><xref:System.Type?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b5eec-120"><xref:System.Type?displayProperty=fullName></span></span>   
 <span data-ttu-id="b5eec-121">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5eec-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b5eec-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5eec-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b5eec-123">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="b5eec-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="b5eec-124">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="b5eec-124">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 [<span data-ttu-id="b5eec-125">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="b5eec-125">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

