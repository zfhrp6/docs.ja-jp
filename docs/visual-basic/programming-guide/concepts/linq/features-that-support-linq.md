---
title: "Visual Basic Features That Support LINQ | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic, LINQ features"
  - "LINQ [Visual Basic], features supporting LINQ"
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 49
---
# Visual Basic Features That Support LINQ
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] という名前は、Visual Basic のテクノロジを指します。これはクエリ構文とその他の言語構成要素を言語内で直接サポートします。  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] があると、外部データ ソースに対してクエリを実行するために新しい言語を学習する必要がなくなります。  Visual Basic を使用して、リレーショナル データベース、XML ストア、またはオブジェクト内のデータのクエリを行うことができます。  このようにクエリ機能を言語に統合することで、コンパイル時に構文エラーやタイプ セーフかどうかをチェックできるようになります。  また、この統合によって、豊富かつ変化に富むクエリを Visual Basic で記述するために必要な知識を事前に与えられることにもなります。  
  
 以下のセクションでは、LINQ をサポートする言語構成要素について詳しく説明します。これを読むと、入門ドキュメント、コード例、およびサンプル アプリケーションについて読み始めることができるようになります。  リンクをクリックして、言語機能が一体となって統合言語クエリを可能にするしくみに関する詳しい説明を参照することもできます。  「[チュートリアル: Visual Basic でクエリを記述する](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)」から読み始めることをお勧めします。  
  
## クエリ式  
 Visual Basic のクエリ式は、SQL や XQuery のクエリ式に似た宣言構文で表すことができます。  コンパイル時に、クエリの構文が LINQ プロバイダーの標準クエリ演算子拡張メソッドの実装に対するメソッド呼び出しに変換されます。  アプリケーションは、`Imports` ステートメントを使用して適切な名前空間を指定することで、どの標準クエリ演算子をスコープ内に入れるかを制御します。  Visual Basic クエリ式の構文は次のようになります。  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 詳細については、「[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)」を参照してください。  
  
## 暗黙的に型指定される変数  
 変数を宣言して初期化するときに変数の型を明示的に指定する代わりに、コンパイラが型を推論して割り当てるようにできます。  これは、*ローカル型推論*と呼ばれます。  
  
 型が推論される変数は、明示的に型を指定した変数と同じように厳密に型指定されます。  ローカル型推論は、メソッド本体内でローカル変数を定義している場合にのみ機能します。  詳細については、「[Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)」および「[Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。  
  
 ローカル型推論の例を次に示します。  この例を使用するには、`Option Infer` を `On` に設定する必要があります。  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 ローカル型の推論はこのセクションで後述LINQ クエリで必要な匿名型を作成することもできます。  
  
 次の LINQ の例では、型の推論は `Option Infer` が `On` か `Off` かにかかわらず実行されます。  `Option Infer` が `Off` で、`Option Strict` が `On` の場合は、コンパイル時のエラーが発生します。  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## オブジェクト初期化子  
 オブジェクト初期化子は、クエリの結果を格納するために匿名型を作成する必要があるときにクエリ式で使用されます。  また、クエリ外部の名前付きの型のオブジェクトを初期化するためにも使用できます。  オブジェクト初期化子を使用することにより、コンストラクターを明示的に呼び出すことなく、オブジェクトを 1 行で初期化することができます。  パブリック プロパティ `Name` および `Phone` や、他にもいくつかのプロパティを持つ `Customer` という名前のクラスがあるとします。オブジェクト初期化子を次のように使用することができます。  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 詳細については、「[Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)」を参照してください。  
  
## 匿名型  
 匿名型を使用すると、一連のプロパティをクエリ結果に含める要素に一時的にグループ化できるので便利です。  これにより、要素に名前付きのデータ型を定義せずに、クエリで使用できるフィールドを任意の組み合わせおよび任意の順序で選択できるようになります。  
  
 *匿名型*はコンパイラによって動的に構築されます。  型の名前はコンパイラによって割り当てられます。これはコンパイルを実行するたびに変わる場合があります。  したがって、名前を直接使用することはできません。  匿名型は次の方法で初期化されます。  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 詳細については、「[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
## 拡張メソッド  
 拡張メソッドを使用することにより、定義の外側からデータ型またはインターフェイスにメソッドを追加できます。  この機能を使用すると、既存の型を実際に変更しなくても、その型に新しいメソッドを実質的に追加できます。  標準クエリ演算子自体は、<xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型で [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリ機能を実現する拡張メソッドのセットです。<xref:System.Collections.Generic.IEnumerable%601> の拡張メソッドとしては他にも、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Union%2A>、および <xref:System.Linq.Enumerable.Intersect%2A> があります。  
  
 次の拡張メソッドは、印刷メソッドを <xref:System.String> クラスに追加します。  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 メソッドは、<xref:System.String> の通常のインスタンス メソッドのように呼び出されます。  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 詳細については、「[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」を参照してください。  
  
## ラムダ式  
 ラムダ式は、計算を実行して単一の値を返す、名前を持たない関数です。  名前付きの関数とは異なり、ラムダ式は定義と実行を同時に行うことができます。  次の例は 4 を表示します。  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 ラムダ式の定義を変数名に代入した後、名前を使用して関数を呼び出すことができます。  次の例も 4 を表示します。  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] では、ラムダ式は、多数の標準クエリ演算子の基礎になっています。  コンパイラは、ラムダ式を作成して、`Where`、`Select`、`Order By`、`Take While` などの基本的なクエリ メソッドに定義された計算を取り込みます。  
  
 たとえば、次のコードは学生のリストから 4 年生をすべて返すクエリを定義します。  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 クエリ定義は次の例のようなコードにコンパイルされます。ここでは 2 つのラムダ式を使用して、`Where` および `Select` の引数を指定します。  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 どちらの形式も `For Each` ループを使用して実行できます。  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 詳細については、「[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
## 参照  
 [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md)   
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ と文字列](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [C\# Features That Support LINQ](../../../../csharp/programming-guide/concepts/linq/features-that-support-linq.md)   
 [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)