---
title: "方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- complex numbers [C#]
- classes [C#], operator overloading
- operator overloading [C#], complex numbers
- operator overloading [C#], using to create classes
- operators [C#], overloading to create a complex number class
ms.assetid: c9b8d982-5112-413f-bae3-b42ae3248ddf
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e851b9d8a46f9cab73883a7b38761fed749c4f93
ms.sourcegitcommit: 22a48b64a0150a60b00b4fc4d8c62cde7f1670c4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a>方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)
この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。 プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)  
 [C# のオーバーロードされた演算子が常に静的である理由](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
