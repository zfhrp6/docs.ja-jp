---
title: "ジェネリックの利点 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], 利点"
ms.assetid: 80f037cd-9ea7-48be-bfc1-219bfb2d4277
caps.latest.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 23
---
# ジェネリックの利点 (C# プログラミング ガイド)
ジェネリックを使用することによって、汎用基本型 <xref:System.Object> との値で型をキャストして一般化を行う、共通言語ランタイムや C\# 言語の以前のバージョンの制限を解決できます。  ジェネリック クラスを作成すると、コンパイル時にタイプ セーフなコレクションを作成できます。  
  
 ジェネリック以外のコレクション クラスを使用する際の制限は、.NET Framework クラス ライブラリの <xref:System.Collections.ArrayList> コレクション クラスを使用する短いプログラムを作成してみるとわかります。  <xref:System.Collections.ArrayList> は、変更なしで参照型や値型を格納できるたいへん便利なコレクション クラスです。  
  
 [!code-cs[csProgGuideGenerics#4](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_1.cs)]  
  
 ただし、この利便性の一方でマイナス面もあります。  <xref:System.Collections.ArrayList> に追加される参照型や値型は暗黙的に <xref:System.Object> にアップキャストされます。  項目が値型の場合は、リストに追加するときにボックス化し、取得するときにボックス化解除する必要があります。  キャスト操作もボックス化およびボックス化解除操作もパフォーマンスに影響します。ボックス化およびボックス化解除の影響は、大型のコレクションの反復処理が必要な場合に非常に大きくなります。  
  
 また、コンパイル時の型チェックがないという制限もあります。<xref:System.Collections.ArrayList> はすべてを <xref:System.Object> にキャストするため、コンパイル時にクライアント コードが次のような処理を行うのを防止できません。  
  
 [!code-cs[csProgGuideGenerics#5](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_2.cs)]  
  
 異種コレクションを作成することは有効であり、意図的に行うこともありますが、その場合、文字列と `int` を 1 つの <xref:System.Collections.ArrayList> に組み合わせると、プログラミング エラーになる可能性があります。このエラーは、実行時まで検出されません。  
  
 C\# 言語の Version 1.0 および 1.1 では、.NET Framework 基本クラス ライブラリのコレクション クラスにおける一般化されたコードの問題は、独自の型に固有のコレクションを記述することによってのみ回避できました。  もちろん、このようなクラスは複数のデータ型で再利用できないため、一般化のメリットがなく、格納する型ごとにクラスを書き直す必要があります。  
  
 <xref:System.Collections.ArrayList> や他の同じようなクラスで実際に必要なのは、クライアント コードで、使用する特定のデータ型をインスタンスごとに指定する方法です。  このような方法があれば、`T:System.Object` にアップキャストする必要性がなくなり、またコンパイラが型チェックを実行することもできるようになります。  言い換えれば、<xref:System.Collections.ArrayList> には型パラメーターが必要なのです。  これを実現するのがジェネリックです。  `N:System.Collections.Generic` 名前空間の <xref:System.Collections.Generic.List%601> ジェネリック コレクションでは、コレクションに項目を追加するという同じ操作が次のようになります。  
  
 [!code-cs[csProgGuideGenerics#6](../../../csharp/programming-guide/generics/codesnippet/csharp/benefits-of-generics_3.cs)]  
  
 クライアント コードでは、<xref:System.Collections.ArrayList> と比較される <xref:System.Collections.Generic.List%601> と共に追加される構文は、宣言とインスタンス化での型引数だけです。  このようにコーディングは若干複雑になりますが、それと引き換えに、<xref:System.Collections.ArrayList> よりも安全であるだけでなく、特にリスト項目が値型のときには処理時間が大幅に短縮されるリストを作成できます。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [ボックス化とボックス化解除](../../../csharp/programming-guide/types/boxing-and-unboxing.md)   
 [コレクションのベスト プラクティス](http://go.microsoft.com/fwlink/?LinkId=112403)