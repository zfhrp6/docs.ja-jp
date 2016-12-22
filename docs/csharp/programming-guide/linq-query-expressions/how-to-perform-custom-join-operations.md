---
title: "方法 : カスタム結合操作を実行する (C# プログラミング ガイド) | Microsoft Docs"
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
  - "カスタム結合 [C#]"
  - "結合 [C#], カスタム"
  - "クエリ [C# での LINQ], 結合"
  - "クエリ式 [C# での LINQ], 結合"
ms.assetid: a05e2ab1-410d-4a1d-8ada-af93539682c9
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : カスタム結合操作を実行する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`join` 句では実行できない結合操作を実行する方法を次の例に示します。  クエリ式の `join` 句は、最も一般的な種類の結合操作である等結合に制限され、また、この目的に合わせて最適化されています。  一般に、等結合を実行する場合は、`join` 句を使用すると、最適なパフォーマンスが得られます。  
  
 ただし、次のような場合は `join` 句を使用できません。  
  
-   非等値の式の述部に結合が使用される場合 \(非等結合\)  
  
-   複数の等値または非等値の式の述部に結合が使用される場合  
  
-   結合操作の前に右側 \(内部\) シーケンス用の一時的な範囲変数を導入する必要がある場合  
  
 等結合ではない結合を実行するには、複数の `from` 句を使用して各データ ソースを個別に導入します。  次に、`where` 句の述部式を各ソースの範囲変数に適用します。  この式は、メソッド呼び出しの形式にすることもできます。  
  
> [!NOTE]
>  このようなカスタム結合操作を、複数の `from` 句を使用して内部コレクションにアクセスすることと混同しないでください。  詳細については、「[join 句](../../../csharp/language-reference/keywords/join-clause.md)」を参照してください。  
  
## 使用例  
 次の例の最初のメソッドは、単純なクロス結合を示しています。  クロス結合では、非常に大きな結果セットが生成されることがあるため、使用には注意が必要です。  ただし、ソース シーケンスを作成し、このソース シーケンスに対して追加のクエリを実行する場合には、クロス結合が便利です。  
  
 2 番目のメソッドでは、左側のカテゴリの一覧にカテゴリ ID があるすべての商品のシーケンスが生成されます。  `let` 句と `Contains` メソッドを使用して、一時配列を作成しています。  クエリの前に配列を作成し、最初の `from` 句を削除することもできます。  
  
 [!code-cs[csProgGuideLINQ#64](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_1.cs)]  
  
## 使用例  
 次の例のクエリでは、一致するキーに基づいて 2 つのシーケンスを結合する必要がありますが、内部 \(右側\) のシーケンスの場合、join 句自体より前にシーケンスを取得することはできません。  `join` 句を使用してこの結合を実行した場合は、`Split` メソッドを要素ごとに呼び出す必要があります。  複数の `from` 句を使用することにより、クエリでメソッドを繰り返し呼び出すことのオーバーヘッドを回避できます。  ただし、`join` は最適化されているため、この例の場合は複数の `from` 句を使用するよりも処理はやはり速くなります。  結果は、主に、メソッド呼び出しにかかる負荷によって決まります。  
  
 [!code-cs[csProgGuideLINQ#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-perform-custom-join-operations_2.cs)]  
  
## コードのコンパイル  
  
-   [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 以降を対象とする [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] コンソール アプリケーション プロジェクトを作成します。  既定では、プロジェクトには、System.Core.dll への参照と、System.Linq 名前空間に対する `using` ディレクティブが含まれます。  
  
-   `Program` クラスを前の例のコードで置き換えます。  
  
-   「[How to: Join Content from Dissimilar Files \(LINQ\)](../Topic/How%20to:%20Join%20Content%20from%20Dissimilar%20Files%20\(LINQ\).md)」の手順に従って、データ ファイル \(scores.csv と names.csv\) を設定します。  
  
-   F5 キーを押して、プログラムをコンパイルおよび実行します。  
  
-   任意のキーを押して、コンソール ウィンドウを終了します。  
  
## 参照  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [join 句](../../../csharp/language-reference/keywords/join-clause.md)   
 [Join Operations](../../../visual-basic/programming-guide/concepts/linq/join-operations.md)   
 [方法 : join 句の結果の順序を指定する](../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)