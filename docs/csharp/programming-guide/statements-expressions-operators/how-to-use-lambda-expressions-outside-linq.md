---
title: "方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], outside LINQ
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c99f6bc7c9db1f0e2341c31ec5bf60217723d4e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-lambda-expressions-outside-linq-c-programming-guide"></a>方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)
ラムダ式の使用は [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリに限定されているわけではありません。 デリゲート値が想定される場面、すなわち匿名メソッドを使用できる場面であれば、どこでもラムダ式を使用できます。 次の例では、Windows フォームのイベント ハンドラーでラムダ式を使用する方法を示します。 なお、入力 (<xref:System.Object> と <xref:System.Windows.Forms.MouseEventArgs>) の型はコンパイラによって推論されるため、ラムダ入力パラメーターで明示的に指定する必要がありません。  
  
## <a name="example"></a>例  
  
```  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
       this.Click += (s, e) => { MessageBox.Show(((MouseEventArgs)e).Location.ToString());};  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [統合言語クエリ (LINQ)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
