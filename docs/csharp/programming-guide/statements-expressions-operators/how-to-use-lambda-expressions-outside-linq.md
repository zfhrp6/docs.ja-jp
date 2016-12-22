---
title: "方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ラムダ式 [C#], LINQ 以外"
ms.assetid: 2b519274-6ee4-4455-ab2e-aed67dbfd07c
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: LINQ 以外でラムダ式を使用する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ラムダ式は [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] クエリに限定されているわけではありません。  デリゲート値になるところ、つまり匿名メソッドを使用できるところであれば、どこでも使用できます。  次の例は、Windows Forms イベント ハンドラーでラムダ式を使用する方法を示しています。  入力 \(<xref:System.Object> および <xref:System.Windows.Forms.MouseEventArgs>\) の型はコンパイラが推論するので、ラムダ入力パラメーターで明示的に指定する必要はありません。  
  
## 使用例  
  
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
  
## 参照  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)