---
title: "How to: Combine Data with LINQ by Using Joins (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [LINQ in Visual Basic], joins"
  - "joins [LINQ in Visual Basic]"
  - "Join clause [LINQ in Visual Basic]"
  - "Group Join clause [Visual Basic]"
  - "joining [LINQ in Visual Basic]"
  - "queries [LINQ in Visual Basic], how-to topics"
ms.assetid: 5b00a478-035b-41c6-8918-be1a97728396
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Combine Data with LINQ by Using Joins (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic には、コレクション間で共通する値に基づいて複数のコレクションの内容を結合できる、`Join` クエリ句と `Group Join` クエリ句があります。  これらの値を*キー*値と呼びます。  リレーショナル データベースの考え方に慣れている開発者の場合は、実質的に、`Join` 句を INNER JOIN、`Group Join` 句を LEFT OUTER JOIN と考えることができます。  
  
 このトピックでは、`Join` クエリ句と `Group Join` クエリ句を使用してデータを結合する方法の例を示して説明します。  
  
## プロジェクトの作成とサンプル データの追加  
  
#### サンプル データと型を含むプロジェクトを作成するには  
  
1.  このトピックのサンプルを実行するには、Visual Studio を開き、新しい Visual Basic コンソール アプリケーション プロジェクトを追加します。  Visual Basic で作成された Module1.vb ファイルをダブルクリックします。  
  
2.  このトピックのサンプルでは、次のコード例の `Person` 型、`Pet` 型、およびデータを使用します。  このコードを、Visual Basic で作成された既定の `Module1` モジュール内にコピーしてください。  
  
     [!code-vb[VbLINQHowTos#1](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#1)]  
    [!code-vb[VbLINQHowTos#2](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#2)]  
  
## Join 句を使用した内部結合の実行  
 内部結合は、2 つのコレクションのデータを結合します。  指定したキー値が一致する項目が含まれます。  どちらのコレクションの項目でも、他方のコレクションの中に一致する項目がない項目は除外されます。  
  
 Visual Basic の LINQ には、内部結合を実行するためのオプションとして、暗黙的な結合と明示的な結合という 2 つのオプションがあります。  
  
 暗黙的な結合では、結合させるコレクションを `From` 句に指定し、一致するキー フィールドを `Where` 句で識別します。  Visual Basic は、2 つのコレクションを、特定のキー フィールドに基づいて暗黙的に結合します。  
  
 結合で使用するキー フィールドを明確に指定する場合は、`Join` 句を使用することで、明示的な結合を指定できます。  この場合でも、`Where` 句を使用して、クエリ結果をフィルター処理できます。  
  
#### Join 句を使用して内部結合を実行するには  
  
1.  次のコードをプロジェクトの `Module1` モジュールに追加すると、暗黙的な内部結合と明示的な内部結合の両方の例を確認できます。  
  
     [!code-vb[VbLINQHowTos#4](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#4)]  
  
## Group Join 句を使用した左外部結合の実行  
 左外部結合では、結合の左側にあるコレクションのすべての項目と、結合の右側にあるコレクションの中の一致する値を持つ項目だけを含めます。  結合の右側のコレクションの項目のうち、左側のコレクションの中に一致する項目がない項目は、クエリ結果から除外されます。  
  
 `Group Join` 句は、実質的に LEFT OUTER JOIN を実行します。  一般に LEFT OUTER JOIN として知られているものと `Group Join` 句が返すものとの違いは、`Group Join` 句では、結合の右側のコレクションから得た結果を、左側のコレクションの項目ごとにグループ化することです。  リレーショナル データベースでは、LEFT OUTER JOIN で返される結果はグループ化されません。クエリ結果には、結合の両方のコレクションから得た一致する項目が含まれます。  この場合、結合の左側のコレクションの項目は、右側のコレクションの一致する項目ごとに繰り返し出現します。  次の手順を完了すると、この結果がどのようになるかを確認できます。  
  
 グループ化されたクエリ結果の項目を返すようにクエリを拡張することで、`Group Join` 句の結果をグループ化されていない結果として取得できます。  これを行うには、グループ化されたコレクションの `DefaultIfEmpty` メソッドでクエリを実行する必要があります。  これにより、右側のコレクションから得た結果に一致する項目がない場合でも、結合の左側のコレクションの項目がクエリ結果に含まれることが保証されます。  クエリにコードを追加することで、結合の右側のコレクションに一致する値がない場合の既定の結果値を指定できます。  
  
#### Group Join 句を使用して左外部結合を実行するには  
  
1.  グループ化された左外部結合とグループ化されていない左外部結合の例を両方とも確認するには、次のコードをプロジェクトの `Module1` モジュールに追加します。  
  
     [!code-vb[VbLINQHowTos#3](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#3)]  
  
## 複合キーを使用した結合の実行  
 結合するコレクションの値を一致させるときに、`Join` 句または `Group Join` 句の中で `And` キーワードを使用することで、複数のキー フィールドを識別できます。  `And` キーワードは、指定されたすべてのキー フィールドが、結合する項目で一致する必要があることを指定します。  
  
#### 複合キーを使用して結合を実行するには  
  
1.  複合キーを使用する結合の例を確認するには、次のコードをプロジェクトの `Module1` モジュールに追加します。  
  
     [!code-vb[VbLINQHowTos#5](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#5)]  
  
## コードの実行  
  
#### コード例を実行するためにコードを追加するには  
  
1.  このトピックのコード例を実行するには、プロジェクト内の`Module1` モジュールの `Sub Main` を、次のコードに置き換えます。  
  
     [!code-vb[VbLINQHowTos#6](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/visualbasic/VbLINQHowTos/Module1.vb#6)]  
  
2.  F5 キーを押して、コード例を実行します。  
  
## 参照  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Join Clause](../../../../visual-basic/language-reference/queries/join-clause.md)   
 [Group Join Clause](../../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [From Clause](../../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)   
 [LINQ によるデータ変換 \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)