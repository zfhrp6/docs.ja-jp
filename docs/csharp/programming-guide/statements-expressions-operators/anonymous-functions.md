---
title: "匿名関数 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a>匿名関数 (C# プログラミング ガイド)
匿名関数は、デリゲート型が必要とされる任意の場所で使用できる "インライン" のステートメントまたは式です。 名前付きデリゲートを初期化するときや、メソッドのパラメーターとして名前付きデリゲート型の代わりに渡したりするときに使用できます。  
  
 ここでは、2 種類ある匿名関数について説明します。  
  
-   [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  ラムダ式は、式ツリーとデリゲートにバインドできます。  
  
## <a name="the-evolution-of-delegates-in-c"></a>C# のデリゲートの進化  
 C# 1.0 では、コードのどこかで定義したメソッドを使用して明示的に初期化することで、デリゲートのインスタンスを作成していました。 C# 2.0 では、デリゲートの呼び出しで実行できる名前なしのインライン ステートメント ブロックを記述する方法として、匿名メソッドの概念が導入されました。 C# 3.0 では、ラムダ式が導入されました。ラムダ式は、概念的には匿名メソッドと似ていますが、より表現力が豊かで簡潔です。 これら 2 つの機能は総称として*匿名関数*と呼ばれます。 一般的に、バージョン 3.5 以降の [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] をターゲットとするアプリケーションであれば、ラムダ式を使用することが推奨されます。  
  
 次の例は、C# 1.0 から C# 3.0 のデリゲート作成の進化を示しています。  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ステートメント、式、および演算子](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)  
 [式ツリー](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
