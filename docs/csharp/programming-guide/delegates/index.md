---
title: "デリゲート (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, デリゲート"
  - "デリゲート [C#]"
ms.assetid: 97de039b-c76b-4b9c-a27d-8c1e1c8d93da
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# デリゲート (C# プログラミング ガイド)
[デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、特定のパラメーター リストおよび戻り値の型を使用して、メソッドへの参照を表す型です。  デリゲートをインスタンス化するときは、互換性のあるシグネチャと戻り値の型を持つ任意のメソッドにそのインスタンスを関連付けることができます。  メソッドは、デリゲート インスタンスを使用して起動する \(呼び出す\) ことができます。  
  
 デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。  イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。  カスタム メソッドを作成して、特定のイベントの発生時に、作成したメソッドが Windows コントロールなどのクラスから呼び出されるようにできます。  次の例にデリゲート宣言を示します。  
  
 [!code-cs[csProgGuideDelegates#20](../../../csharp/programming-guide/delegates/codesnippet/CSharp/index_1.cs)]  
  
 デリゲート型と一致するアクセス可能なクラスまたは構造体のメソッドはすべて、デリゲートに代入できます。  メソッドは、静的メソッドとインスタンス メソッドのいずれかにできます。  このため、メソッド呼び出しをプログラムによって変更でき、また新しいコードを既存のクラスに接続することもできます。  
  
> [!NOTE]
>  メソッドのオーバーロードのコンテキストでは、メソッドのシグネチャに戻り値は含まれません。  しかしデリゲートのコンテキストでは、シグネチャに戻り値が含まれます。  つまり、メソッドにはデリゲートと同じ戻り値の型が必要です。  
  
 このようにメソッドをパラメーターとして参照できるため、デリゲートはコールバック メソッドを定義するのに最適です。  たとえば、2 つのオブジェクトを比較するメソッドへの参照は、並べ替えのアルゴリズムへの引数として渡すことができます。  比較を行うコードは独立したプロシージャであるため、並べ替えのアルゴリズムはより一般的な方法で記述できます。  
  
## デリゲートの概要  
 デリゲートには、次の特徴があります。  
  
-   デリゲートは、C\+\+ の関数ポインターに似ていますが、タイプ セーフです。  
  
-   デリゲートを使用すると、メソッドをパラメーターとして渡すことができます。  
  
-   デリゲートは、コールバック メソッドを定義するのに使用できます。  
  
-   デリゲートは連結でき、たとえば、複数のメソッドを 1 つのイベントで呼び出すことができます。  
  
-   メソッドは、デリゲート型に正確に一致する必要がありません。  詳細については、「[デリゲートの分散の使用](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
-   C\# Version 2.0 で、[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)の概念が導入され、別個に定義されたメソッドの代わりにコード ブロックをパラメーターとして渡せるようになりました。  C\# 3.0 ではラムダ式が導入され、インライン コード ブロックをより簡潔に記述できるようになりました。  匿名メソッドと \(特定のコンテキストにおける\) ラムダ式はどちらも、デリゲート型にコンパイルされます。  これらの機能は総称して、匿名関数と呼ばれるようになりました。  ラムダ式の詳細については、「[匿名関数](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)」を参照してください。  
  
## このセクションの内容  
  
-   [デリゲートの使用](../../../csharp/programming-guide/delegates/using-delegates.md)  
  
-   [When to Use Delegates Instead of Interfaces \(C\# Programming Guide\)](http://msdn.microsoft.com/ja-jp/2e759bdf-7ca4-4005-8597-af92edf6d8f0)  
  
-   [名前付きメソッドを使用したデリゲートと匿名メソッドを使用したデリゲート](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
  
-   [匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
-   [デリゲートの分散の使用](../Topic/Using%20Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [方法 : デリゲートを結合する \(マルチキャスト デリゲート\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
  
-   [方法 : デリゲートを宣言し、インスタンス化して使用する](../../../csharp/programming-guide/delegates/how-to-declare-instantiate-and-use-a-delegate.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参考書籍の該当する章  
 『[C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)』の「[Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395)」  
  
 『[Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)』の「[Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418)」  
  
## 参照  
 <xref:System.Delegate>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)