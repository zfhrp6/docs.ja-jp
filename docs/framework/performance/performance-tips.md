---
title: ".NET のパフォーマンスに関するヒント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C# 言語, パフォーマンス"
  - "パフォーマンス [C#]"
  - "パフォーマンス [Visual Basic]"
  - "Visual Basic, パフォーマンス"
ms.assetid: ae275793-857d-4102-9095-b4c2a02d57f4
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
caps.handback.revision: 36
---
# .NET のパフォーマンスに関するヒント
*パフォーマンス*という用語は、プログラムの実行速度を表す一般的な用語です。  ソース コード内で特定の基本規則に従うことにより、実行速度を上げることができることもあります。  プログラムによっては、コードを綿密に調べることが重要で、プロファイラーを使用して、可能な限り速く実行しているかどうかを確認することが必要な場合もあります。  一方、記述どおりに許容可能な速度でコードが実行されているため、このような最適化が必要ないプログラムもあります。  ここでは、パフォーマンスの低下が発生する一般的な状況と、パフォーマンスを向上させるためのヒント、およびパフォーマンスに関する追加のトピックについて説明します。  パフォーマンスの計画と計測の詳細については、「[Performance](../../../docs/framework/performance/index.md)」を参照してください。  
  
## ボックス化とボックス化解除  
 たとえば、<xref:System.Collections.ArrayList?displayProperty=fullName> などの非ジェネリック コレクション クラスで、頻繁に値型をボックス化する必要がある状況では、値型の使用を回避するのが最も適しています。  <xref:System.Collections.Generic.List%601?displayProperty=fullName> などのジェネリック コレクションを使用することで、値型のボックス化を回避できます。  ボックス化とボックス化解除は、負荷の大きい処理です。  値型をボックス化するときは、完全に新しいオブジェクトを作成する必要があります。  これには、単純な参照割り当てと比較して最大 20 倍もの時間がかかることがあります。  また、ボックス化を解除するときは、キャストのプロセスで代入の 4 倍の時間がかかることがあります。  詳細については、「[ボックス化とボックス化解除](../Topic/Boxing%20and%20Unboxing%20\(C%23%20Programming%20Guide\).md)」を参照してください。  
  
## 文字列  
 たとえば、短いループ内で多くの文字列変数を連結する場合は、C\# の [\+ 演算子](../Topic/+%20Operator%20\(C%23%20Reference\).md)または Visual Basic の[連結演算子](../Topic/Concatenation%20Operators%20\(Visual%20Basic\).md)ではなく、<xref:System.Text.StringBuilder?displayProperty=fullName> を使用します。  詳細については、「[方法: 複数の文字列を連結する](../Topic/How%20to:%20Concatenate%20Multiple%20Strings%20\(C%23%20Programming%20Guide\).md)」および「[Concatenation Operators in Visual Basic](../Topic/Concatenation%20Operators%20in%20Visual%20Basic.md)」を参照してください。  
  
## デストラクター  
 空のデストラクターは使用しないでください。  デストラクターがクラスに存在するときは、エントリが終了キューで作成されます。  デストラクターを呼び出すと、ガベージ コレクターが呼び出され、このキューを処理します。  デストラクターが空の場合は、これによってパフォーマンスが低下します。  詳細については、「[デストラクター](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)」および「[Object Lifetime: How Objects Are Created and Destroyed](../Topic/Object%20Lifetime:%20How%20Objects%20Are%20Created%20and%20Destroyed%20\(Visual%20Basic\).md)」を参照してください。  
  
## その他のリソース  
  
-   [Writing Faster Managed Code: Know What Things Cost \(高速なマネージ コードを書く: 何にコストがかかるのかを知る\)](http://go.microsoft.com/fwlink/?LinkId=99294)  
  
-   [Writing High\-Performance Managed Applications: A Primer \(高パフォーマンスのマネージ アプリケーションを書く: 入門編\)](http://go.microsoft.com/fwlink/?LinkId=99295)  
  
-   [ガベージ コレクターの基本とパフォーマンスのヒント](http://go.microsoft.com/fwlink/?LinkId=99296)  
  
-   [.NET アプリケーションのパフォーマンス関連のヒントとトリック](http://go.microsoft.com/fwlink/?LinkId=99297)  
  
-   [Inside Diagnostic Tools for .NET \(.NET の診断ツールの裏側\)](http://go.microsoft.com/fwlink/?LinkId=112407)  
  
-   [Rico Mariani's Performance Tidbits \(Rico Mariani が紹介するパフォーマンスに関するニュース\)](http://go.microsoft.com/fwlink/?LinkId=115679)  
  
## 参照  
 [Performance](../../../docs/framework/performance/index.md)   
 [プログラミングの概念](../Topic/Programming%20Concepts.md)   
 [Visual Basic Programming Guide](../Topic/Visual%20Basic%20Programming%20Guide.md)   
 [C\# プログラミング ガイド](../Topic/C%23%20Programming%20Guide.md)