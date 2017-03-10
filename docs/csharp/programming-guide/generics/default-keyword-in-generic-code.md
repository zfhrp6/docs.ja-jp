---
title: "ジェネリック コードの default キーワード (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "default キーワード [C#], ジェネリック プログラミング"
  - "ジェネリック [C#], default キーワード"
ms.assetid: b9daf449-4e64-496e-8592-6ed2c8875a98
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# ジェネリック コードの default キーワード (C# プログラミング ガイド)
ジェネリック クラスとジェネリック メソッドでは、あらかじめ以下の情報を把握していない場合に、パラメーター化された型 T に既定値を割り当てる方法が 1 つの問題となります。  
  
-   T が参照型か値型か  
  
-   T が値型の場合、数値か構造体か  
  
 パラメーター化された型 T の変数がある場合、ステートメント t \= null は、T が参照型のときにのみ有効です。また、t \= 0 は、数値では機能しますが、構造体では機能しません。  この問題を解決するには、`default` キーワードを使用します。このキーワードは、参照型の場合には null を返し、数値の値型にはゼロを返します。  構造体の場合、ゼロまたは null \(値型か参照型かによって変わります\) に初期化された構造体の各メンバーを返します。  null 許容値型の場合、default は <xref:System.Nullable%601?displayProperty=fullName> を返します。これは、他の構造体と同様に初期化されます。  
  
 `GenericList<T>` クラスで `default` キーワードを使用する方法の例を次に示します。  詳細については、「[ジェネリックの概要 \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/generics/introduction-to-generics.md)」を参照してください。  
  
 [!code-cs[csProgGuideGenerics#41](../../../csharp/programming-guide/generics/codesnippet/csharp/default-keyword-in-gener_1.cs)]  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリック](../../../csharp/programming-guide/generics/index.md)   
 [ジェネリック メソッド](../../../csharp/programming-guide/generics/generic-methods.md)   
 [ジェネリック](../Topic/Generics%20in%20the%20.NET%20Framework.md)