---
title: "方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 15
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
ms.openlocfilehash: 2ce629320744d46787aaabba48740f05c917fdcb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="7d52f-102">方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="7d52f-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="7d52f-103">この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7d52f-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="7d52f-104">プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="7d52f-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d52f-105">例</span><span class="sxs-lookup"><span data-stu-id="7d52f-105">Example</span></span>  
 <span data-ttu-id="7d52f-106">[!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7d52f-106">[!code-cs[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d52f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d52f-107">See Also</span></span>  
 <span data-ttu-id="7d52f-108">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7d52f-108">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="7d52f-109">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="7d52f-109">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="7d52f-110">[operator (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md) </span><span class="sxs-lookup"><span data-stu-id="7d52f-110">[operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md) </span></span>  
 [<span data-ttu-id="7d52f-111">C# のオーバーロードされた演算子が常に静的である理由</span><span class="sxs-lookup"><span data-stu-id="7d52f-111">Why are overloaded operators always static in C#?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112383)

