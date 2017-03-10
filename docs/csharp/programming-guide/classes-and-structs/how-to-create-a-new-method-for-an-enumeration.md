---
title: "方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "enum 機能拡張 [C#]"
  - "列挙型 [C#]"
  - "拡張メソッド [C#], 列挙型"
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 7
---
# 方法 : 列挙型対応の新しいメソッドを作成する (C# プログラミング ガイド)
拡張メソッドを使用して、特定の列挙型に対応した機能を追加できます。  
  
## 使用例  
 次の例では、`Grades` 列挙型により、生徒が授業で受け取る成績評価が表されています。  `Passing` という名前の拡張メソッドが `Grades` 型に追加されており、この型の各インスタンスが、合格点を表しているかどうか自ら "認識" できるようになっています。  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/how-to-create-a-new-meth_1.cs)]  
  
 `Extensions` クラスに動的に更新される静的変数が含まれていること、および拡張メソッドの戻り値がその静的変数の現在の値を反映することにも注意してください。  背後では、拡張メソッドがその拡張メソッドが定義されている静的クラスにおいて直接呼び出されることを、この例は示しています。  
  
## コードのコンパイル  
 このコードを実行するには、[!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs-current-short-md.md)] で作成した Visual C\# コンソール アプリケーション プロジェクトに、コードをコピーして貼り付けます。  既定では、このプロジェクトは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] Version 3.5 を対象としており、System.Core.dll への参照と System.Linq の `using` ディレクティブが含まれます。  これらの要件が 1 つ以上プロジェクトから欠落していても、手動で追加できます。  詳細については、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)