---
title: "方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "デリゲート [C#], 宣言とインスタンス化"
ms.assetid: 61c4895f-f785-48f8-8bfe-db73b411c4ae
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# 方法 : デリゲートを宣言し、インスタンス化して使用する (C# プログラミング ガイド)
C\# 1.0 以降では、次の例に示すようにデリゲートを宣言できます。  
  
 [!code-cs[csProgGuideDelegates#13](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#14](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_2.cs)]  
  
 C\# 2.0 では、次の例に示すように、前の宣言をさらに簡潔に記述できます。  
  
 [!code-cs[csProgGuideDelegates#32](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_3.cs)]  
  
 C\# 2.0 以降では、次の例に示すように、匿名メソッドを使用して[デリゲート](../../../csharp/language-reference/keywords/delegate.md)を宣言および初期化することもできます。  
  
 [!code-cs[csProgGuideDelegates#15](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_4.cs)]  
  
 C\# 3.0 以降では、次の例に示すように、ラムダ式を使用してデリゲートを宣言およびインスタンス化することもできます。  
  
 [!code-cs[csProgGuideDelegates#31](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_5.cs)]  
  
 詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 この例では、デリゲートの宣言方法、インスタンス化方法、および使用方法を示します。  `BookDB` クラスは、書籍のデータベースを管理する書店データベースをカプセル化します。  このクラスは、`ProcessPaperbackBooks` メソッドを公開します。このメソッドは、データベースからすべてのペーパーバックを検索し、それぞれについてデリゲートを呼び出します。  使用される `delegate` 型の名前は、`ProcessBookDelegate` です。  `Test` クラスはこのクラスを使用して、ペーパーバックの書名と平均価格を出力します。  
  
 デリゲートを使用すると、書店データベースとクライアント コードの機能の分担を適切に行うことができます。  クライアント コードは、書籍の在庫状況や書店コードがペーパーバックを検索する方法については関知しません。  書店コードは、ペーパーバックの検索後の処理については関知しません。  
  
## 使用例  
 [!code-cs[csProgGuideDelegates#12](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_6.cs)]  
  
## 信頼性の高いプログラミング  
  
-   デリゲートの宣言  
  
     次のステートメントは、新しいデリゲート型を宣言します。  
  
     [!code-cs[csProgGuideDelegates#16](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_7.cs)]  
  
     各デリゲート型は、引数の数、引数型、およびカプセル化できるメソッドの戻り値の型を表します。  引数型または戻り値の型の新しいセットが必要になった場合には、新しいデリゲート型を宣言する必要があります。  
  
-   デリゲートのインスタンス化  
  
     デリゲート型を宣言したら、デリゲート オブジェクトを作成して、特定のメソッドに関連付ける必要があります。  前の例では、次の例のように、`PrintTitle` メソッドを `ProcessPaperbackBooks` メソッドに渡すことにより行います。  
  
     [!code-cs[csProgGuideDelegates#17](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_8.cs)]  
  
     このコードは、[静的](../../../csharp/language-reference/keywords/static.md)メソッド `Test.PrintTitle` と関連付けられている新しいデリゲート オブジェクトを作成します。  同様に、`totaller` オブジェクトの静的でないメソッド `AddBookToTotal` は、次の例のように渡されます。  
  
     [!code-cs[csProgGuideDelegates#18](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_9.cs)]  
  
     どちらの場合も、新しいデリゲート オブジェクトは `ProcessPaperbackBooks` メソッドに渡されます。  
  
     デリゲートが作成されると、デリゲートに関連付けられたメソッドは変更できません。つまり、デリゲート オブジェクトは不変であることに注意してください。  
  
-   デリゲートの呼び出し  
  
     作成されたデリゲート オブジェクトは、通常、デリゲートを呼び出す他のコードに渡されます。  デリゲート オブジェクトを呼び出すには、デリゲート オブジェクトの名前を使用します。名前の後ろには、デリゲートへ渡す引数をかっこで囲んで指定します。  デリゲートの呼び出しの例を、次に示します。  
  
     [!code-cs[csProgGuideDelegates#19](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-declare-instantiate-and-use-a-delegate_10.cs)]  
  
     この例のように、デリゲートは、同期的に呼び出すことも、`BeginInvoke` メソッドと `EndInvoke` メソッドを使用して非同期的に呼び出すこともできます。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [イベント](../../../csharp/programming-guide/events/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)