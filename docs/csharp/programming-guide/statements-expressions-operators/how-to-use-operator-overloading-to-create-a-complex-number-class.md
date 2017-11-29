---
title: "方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2053684a9b20c3ec8f4d8ac275832516b3f2c265
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a><span data-ttu-id="fdbbc-102">方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="fdbbc-102">How to: Use Operator Overloading to Create a Complex Number Class (C# Programming Guide)</span></span>
<span data-ttu-id="fdbbc-103">この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fdbbc-103">This example shows how you can use operator overloading to create a complex number class `Complex` that defines complex addition.</span></span> <span data-ttu-id="fdbbc-104">プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="fdbbc-104">The program displays the imaginary and the real parts of the numbers and the addition result using an override of the `ToString` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdbbc-105">例</span><span class="sxs-lookup"><span data-stu-id="fdbbc-105">Example</span></span>  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fdbbc-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdbbc-106">See Also</span></span>  
 [<span data-ttu-id="fdbbc-107">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="fdbbc-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fdbbc-108">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="fdbbc-108">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="fdbbc-109">演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fdbbc-109">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="fdbbc-110">C# のオーバーロードされた演算子が常に静的である理由</span><span class="sxs-lookup"><span data-stu-id="fdbbc-110">Why are overloaded operators always static in C#?</span></span>](http://go.microsoft.com/fwlink/?LinkId=112383)
