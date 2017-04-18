---
title: "Visual Basic の LINQ をサポートする機能 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: 51
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3bca15a07a88195589b9c9de5f9842eea42912f1
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-features-that-support-linq"></a>LINQ をサポートする Visual Basic の機能
名前[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]サポートしているクエリの構文を言語内で直接その他の言語構造は、Visual Basic での技術を参照します。 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]、外部データ ソースに対してクエリを新しい言語を習得する必要はありません。 リレーショナル データベース、XML ストア、またはオブジェクトのデータを照会するには、Visual Basic を使用します。 この統合言語クエリ機能のにより、コンパイル時の構文エラーと型の安全性をチェックします。 この統合は、Visual Basic で豊富なさまざまなクエリを記述しておく必要があるのほとんどを既に理解しているようにもなります。  
  
 次のセクションでは、概要ドキュメント、コード例については、およびサンプル アプリケーションの読み取りを開始するために十分な詳細情報で LINQ をサポートする言語構成要素について説明します。 また、どの言語機能が連携する統合言語クエリを有効にするのより詳細な説明を検索するリンクをクリックします。 開始するが最適[チュートリアル: Visual Basic でクエリを記述](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)します。  
  
## <a name="query-expressions"></a>クエリ式  
 Visual Basic のクエリ式は、SQL や XQuery などのような宣言型の構文で表現できます。 コンパイル時に、クエリの構文は、標準クエリ演算子の拡張メソッドの LINQ プロバイダーの実装に対するメソッド呼び出しに変換されます。 標準クエリ演算子がスコープ内で適切な名前空間を指定することによって、アプリケーションを制御、`Imports`ステートメントです。 Visual Basic のクエリ式の構文は、次のようにはなります。  
  
 [!code-vb[VbLINQVbFeatures&#1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。  
  
## <a name="implicitly-typed-variables"></a>暗黙的に型指定された変数  
 明示的に宣言して、変数を初期化するときに、型を指定する、代わりに、型をコンパイラが有効にできます。 これとして参照は*ローカル型推論*します。  
  
 変数の型は推論される厳密に型指定、型を明示的に指定した変数と同じようにします。 ローカル型推論は、メソッドの本文内のローカル変数を定義するときにのみ機能します。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
 次の例では、ローカル型推論を示しています。 この例を使用するに設定する必要があります`Option Infer`に`On`します。  
  
 [!code-vb[VbLINQVbFeatures&#2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 ローカル型推論では、このセクションで後で説明し、LINQ クエリに必要な匿名型を作成することです。  
  
 場合は次の LINQ の例では型の推定が発生した`Option Infer`か`On`または`Off`です。 コンパイル時エラーが発生`Option Infer`は`Off`と`Option Strict`は`On`です。  
  
 [!code-vb[VbLINQVbFeatures&#3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>オブジェクト初期化子  
 オブジェクト初期化子は、クエリの結果を保持するために匿名型を作成するときに、クエリ式で使用されます。 これらも使用できますクエリの外部で名前付きの型のオブジェクトを初期化します。 オブジェクト初期化子を使用するは、明示的にコンス トラクターを呼び出さずに、1 行でオブジェクトを初期化します。 という名前のクラスがある場合`Customer`を持つパブリック`Name`と`Phone`プロパティとその他のプロパティでは、この方法でオブジェクト初期化子を使用できます。  
  
 [!code-vb[VbLINQVbFeatures&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型は、クエリ結果に追加する要素にプロパティのセットを一時的にグループ化する便利な手段を提供します。 これにより、要素の名前付きのデータ型を定義することがなく任意の順序で、クエリで使用できるフィールドの任意の組み合わせを選択できます。  
  
 *匿名型*はコンパイラによって動的に構築します。 型の名前は、コンパイラによって割り当てられ、新しいコンパイルのたびに変更があります。 そのため、名前は直接使用できません。 匿名型は、次のように初期化されます。  
  
 [!code-vb[VbLINQVbFeatures&#5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)します。  
  
## <a name="extension-methods"></a>拡張メソッド  
 拡張メソッドを使用すると、データ型またはインターフェイスの元の定義の外部にメソッドを追加できます。 この機能では、実際には、新しいメソッドを実際には、型を変更しなくても既存の型に追加することができます。 標準クエリ演算子自体が提供する拡張メソッドのセット[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] <xref:System.Collections.Generic.IEnumerable%601>.</xref:System.Collections.Generic.IEnumerable%601>を実装する任意の型のクエリ機能 他の拡張機能に<xref:System.Collections.Generic.IEnumerable%601>含める<xref:System.Linq.Enumerable.Count%2A>、 <xref:System.Linq.Enumerable.Union%2A>、 <xref:System.Linq.Enumerable.Intersect%2A>.</xref:System.Linq.Enumerable.Intersect%2A> </xref:System.Linq.Enumerable.Union%2A> </xref:System.Linq.Enumerable.Count%2A> </xref:System.Collections.Generic.IEnumerable%601>  
  
 次の拡張メソッドでは、印刷メソッドを<xref:System.String>クラス</xref:System.String>に追加します。  
  
 [!code-vb[VbLINQVbFeatures&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 <xref:System.String>::</xref:System.String>の通常のインスタンス メソッドのように、メソッドが呼び出されます  
  
 [!code-vb[VbLINQVbFeatures&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 詳細については、次を参照してください。[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)します。  
  
## <a name="lambda-expressions"></a>ラムダ式  
 ラムダ式は、計算して、単一の値を返す名前のない関数です。 名前付きの関数とは異なり、ラムダ式の定義し、同時に実行します。 次の例では、4 を表示します。  
  
 [!code-vb[VbLINQVbFeatures&#8;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 変数名にラムダ式の定義を割り当てるでき、名前を使用して、関数を呼び出すことができます。 次の例では、4 も表示されます。  
  
 [!code-vb[VbLINQVbFeatures&#12;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]ラムダ式には、標準クエリ演算子の多くが基本となります。 コンパイラなど、基本的なクエリ メソッドで定義されている計算をキャプチャするラムダ式を作成する`Where`、 `Select`、 `Order By`、 `Take While`、およびその他。  
  
 たとえば、次のコードでは、学生の一覧から上級生を返すクエリを定義します。  
  
 [!code-vb[VbLINQVbFeatures&#9;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 クエリ定義は次の例は、2 つのラムダ式を使用して引数を指定する次のようなコードにコンパイル`Where`と`Select`です。  
  
 [!code-vb[VbLINQVbFeatures&#10;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 いずれかのバージョンを使用して実行できる、`For Each`ループします。  
  
 [!code-vb[VbLINQVbFeatures&#11;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 詳細については、次を参照してください。[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)   
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
