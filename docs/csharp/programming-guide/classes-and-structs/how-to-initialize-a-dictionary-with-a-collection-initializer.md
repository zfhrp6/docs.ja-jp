---
title: "方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コレクション初期化子 [C#]、ディクショナリ"
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# 方法 : コレクション初期化子を使用してディクショナリを初期化する (C# プログラミング ガイド)
<xref:System.Collections.Generic.Dictionary%602> には、キーと値のペアのコレクションが含まれます。  <xref:System.Collections.Generic.Dictionary%602.Add%2A> メソッドは、キー用と値用の 2 つのパラメーターを受け取ります。  <xref:System.Collections.Generic.Dictionary%602> または `Add` メソッドが複数のパラメーターを受け取るコレクションを初期化するには、次の例に示すように、各パラメーターのセットを中かっこで囲みます。  
  
## 使用例  
 次のコード例では、<xref:System.Collections.Generic.Dictionary%602> が `StudentName` 型のインスタンスで初期化されます。  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 コレクションの各要素の中かっこの 2 つのペアに注目してください。  最も内側の中かっこは `StudentName` のオブジェクト初期化子を囲み、最も外側の中かっこは、`students` <xref:System.Collections.Generic.Dictionary%602> に追加されるキーと値のペアの初期化子を囲んでいます。  最後に、ディクショナリのコレクション初期化子全体が中かっこで囲まれています。  
  
## コードのコンパイル  
 このコードを実行するには、[!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] で作成した Visual C\# コンソール アプリケーション プロジェクトに、クラスをコピーして貼り付けます。  既定では、このプロジェクトは [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 を対象としており、System.Core.dll への参照と System.Linq のディレクティブの使用が含まれます。  これらの要件が 1 つ以上プロジェクトから欠落していても、手動で追加できます。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)