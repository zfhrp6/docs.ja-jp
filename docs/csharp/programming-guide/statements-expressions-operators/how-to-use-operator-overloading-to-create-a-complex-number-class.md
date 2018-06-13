---
title: '方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
ms.openlocfilehash: d746355dac1b99690a5a94c829bd35598c6c8be8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328865"
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="e3877-102">方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e3877-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="e3877-103">この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e3877-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="e3877-104">プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="e3877-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3877-105">例</span><span class="sxs-lookup"><span data-stu-id="e3877-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3877-106">参照</span><span class="sxs-lookup"><span data-stu-id="e3877-106">See Also</span></span>  
 [<span data-ttu-id="e3877-107">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="e3877-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3877-108">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="e3877-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="e3877-109">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e3877-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="e3877-110">C# のオーバーロードされた演算子が常に静的である理由</span><span class="sxs-lookup"><span data-stu-id="e3877-110">Why are overloaded operators always static in C#?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
