---
title: "方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "継承 [C#], オーバーライド (OnPaint と ToString を)"
  - "ToString メソッド, オーバーライド (C# での)"
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法: ToString メソッドをオーバーライドする (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# のすべてのクラスと構造体は、<xref:System.Object> クラスを暗黙的に継承します。  そのため、C\# では、すべてのオブジェクトが <xref:System.Object.ToString%2A> メソッドを取得します。このメソッドは、該当するオブジェクトの文字列形式を返します。  たとえば、`int` 型の変数はすべて `ToString` メソッドを持ち、次のようにその変数の内容を文字列として返すことができます。  
  
 [!code-cs[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 カスタムのクラスまたは構造体を作成するときは、クライアント コードにカスタム型の情報を提供するため、<xref:System.Object.ToString%2A> メソッドをオーバーライドする必要があります。  
  
 `ToString` のメソッドのカスタム書式の書式指定文字列やそのほかの種類の使用方法の詳細については、 " " を参照してください [型の書式設定](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)。  
  
> [!IMPORTANT]
>  このメソッドを使用して提供する情報を決定するときは、作成したクラスまたは構造体が信頼関係のないコードによって使用されるかどうかを考慮します。  悪意があるコードで利用される可能性がある情報を提供しないように注意してください。  
  
### クラスまたは構造体内の ToString メソッドをオーバーライドするには  
  
1.  次の修飾子および戻り値の値を指定して、`ToString` メソッドを定義します。  
  
    ```c#  
    public override string ToString(){}  
    ```  
  
2.  文字列を返すようにメソッドを実装します。  
  
     次の例では、特定のクラス インスタンスに固有のデータに加えて、クラス名も返されます。  
  
     [!code-cs[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     `ToString` メソッドをテストする方法を次のコード例に示します。  
  
     [!code-cs[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## 参照  
 <xref:System.IFormattable>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [文字列](../../../csharp/programming-guide/strings/index.md)   
 [string](../../../csharp/language-reference/keywords/string.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [オーバーライド](../../../csharp/language-reference/keywords/override.md)   
 [virtual](../../../csharp/language-reference/keywords/virtual.md)   
 [型の書式設定](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md)