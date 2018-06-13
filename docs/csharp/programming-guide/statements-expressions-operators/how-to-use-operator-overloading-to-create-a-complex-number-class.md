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
# <a name="how-to-use-operator-overloading-to-create-a-complex-number-class-c-programming-guide"></a>方法 : 演算子のオーバーロードを使用して複素数クラスを作成する (C# プログラミング ガイド)
この例では、演算子のオーバーロードを使用して、複素数の加算を定義する複素数クラス `Complex` を作成する方法を示します。 プログラムは、`ToString` メソッドのオーバーライドを使用して、数値の虚数部と実数部、および加算結果を表示します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideStatements#16](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-use-operator-overloading-to-create-a-complex-number-class_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# 演算子](../../../csharp/language-reference/operators/index.md)  
 [演算子 (C# リファレンス)](../../../csharp/language-reference/keywords/operator.md)  
 [C# のオーバーロードされた演算子が常に静的である理由](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
