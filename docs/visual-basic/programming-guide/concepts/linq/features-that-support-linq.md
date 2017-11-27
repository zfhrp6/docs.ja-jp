---
title: "LINQ をサポートする Visual Basic の機能"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
caps.latest.revision: "51"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42465dbb168b7961792aec6b3c2bb7ae8f0a3355
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ をサポートする Visual Basic の機能
名前[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]をサポートしているクエリの構文と他の言語が言語内で直接構築 Visual Basic でのテクノロジを指します。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]、外部データ ソースに対してクエリを新しい言語を習得する必要はありません。 Visual Basic を使用して、リレーショナル データベース、XML ストア、またはオブジェクト内のデータのクエリを行うことができます。 この統合言語クエリ機能の有効に構文エラーとタイプ セーフのコンパイル時にチェックします。 この統合は、Visual Basic で豊富な多様なクエリを書き込むために知っておく必要があるのほとんどを既に把握しているようにもなります。  
  
 次のセクションでは、概要ドキュメント、コード例については、およびサンプル アプリケーションの読み取りを開始するために十分な詳細情報での LINQ をサポートする言語構成要素について説明します。 どの言語機能は一体統合言語クエリを有効にする詳細な説明を検索するリンクをクリックすることもできます。 開始点としては、[チュートリアル: Visual Basic でのクエリを記述](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)です。  
  
## <a name="query-expressions"></a>クエリ式  
 Visual Basic でのクエリ式は、SQL または XQuery のような宣言型の構文で表現できます。 コンパイル時に、クエリ構文は、LINQ プロバイダーの標準クエリ演算子の拡張メソッドの実装に対するメソッド呼び出しに変換されます。 アプリケーションのコントロールである標準クエリ演算子のスコープ内で適切な名前空間を指定することによって、`Imports`ステートメントです。 Visual Basic のクエリ式の構文は、このようになります。  
  
 [!code-vb[VbLINQVbFeatures#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_1.vb)]  
  
 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)です。  
  
## <a name="implicitly-typed-variables"></a>暗黙的に型指定された変数  
 明示的に宣言して、変数を初期化するときに、型を指定する、代わりに、コンパイラが推論型を割り当てるを有効にできます。 これを呼びます*ローカル型推論*です。  
  
 変数の型が推論される厳密に型指定、型を明示的に指定した変数と同じようにします。 ローカル型推論は、メソッドの本体内のローカル変数を定義するときにのみ機能します。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)です。  
  
 次の例は、ローカル型推論を示しています。 この例を使用するに設定する必要があります`Option Infer`に`On`です。  
  
 [!code-vb[VbLINQVbFeatures#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_2.vb)]  
  
 ローカル型推論では、このセクションで後で説明し、LINQ クエリのために必要な匿名型を作成することです。  
  
 例では、次の LINQ、型の推論場合`Option Infer`か`On`または`Off`です。 場合、コンパイル時エラーが発生した`Option Infer`は`Off`と`Option Strict`は`On`します。  
  
 [!code-vb[VbLINQVbFeatures#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_3.vb)]  
  
## <a name="object-initializers"></a>オブジェクト初期化子  
 オブジェクト初期化子は、クエリの結果を格納する匿名型を作成するときに、クエリ式で使用されます。 これらも使用できますのクエリの外部で名前付きの型のオブジェクトを初期化します。 オブジェクト初期化子を使用すると、コンス トラクターを明示的に呼び出さずに 1 行でオブジェクトを初期化できます。 という名前のクラスがある場合`Customer`を持つパブリック`Name`と`Phone`プロパティ、他のプロパティと共にこのような方法で、オブジェクト初期化子を使用できます。  
  
 [!code-vb[VbLINQVbFeatures#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_4.vb)]  
  
 詳細については、次を参照してください。[オブジェクト初期化子: 名前付きおよび匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)です。  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型は、一時的に一連のプロパティをクエリ結果に追加する要素にグループ化する便利な手段を提供します。 これにより、要素の名前付きのデータ型を定義することがなく、任意の順序でのクエリで使用できるフィールドの任意の組み合わせを選択できます。  
  
 *匿名型*はコンパイラによって動的に構築します。 型の名前は、コンパイラによって割り当てられ、新しいコンパイルのたびに変わることがありますがします。 そのため、名前を直接使用することはできません。 匿名型は、次のように初期化されます。  
  
 [!code-vb[VbLINQVbFeatures#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_5.vb)]  
  
 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
## <a name="extension-methods"></a>拡張メソッド  
 拡張メソッドを使用すると、データ型またはインターフェイスの定義の外部にメソッドを追加できます。 この機能では、実際には、新しいメソッドを実際には、型を変更することがなく既存の型に追加することができます。 標準クエリ演算子は自体が提供する拡張メソッドのセット[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]を実装する任意の型のクエリ機能<xref:System.Collections.Generic.IEnumerable%601>します。 他の拡張機能に<xref:System.Collections.Generic.IEnumerable%601>含める<xref:System.Linq.Enumerable.Count%2A>、 <xref:System.Linq.Enumerable.Union%2A>、および<xref:System.Linq.Enumerable.Intersect%2A>です。  
  
 次の拡張メソッドに印刷メソッドの追加、<xref:System.String>クラスです。  
  
 [!code-vb[VbLINQVbFeatures#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_6.vb)]  
  
 通常のインスタンス メソッドと同様に、メソッドが呼び出されます<xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_7.vb)]  
  
 詳細については、「[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」を参照してください。  
  
## <a name="lambda-expressions"></a>ラムダ式  
 ラムダ式は、計算して、単一の値を返す名前のない関数です。 名前付きの関数とは異なり、ラムダ式の定義し、同時に実行します。 次の例では、4 が表示されます。  
  
 [!code-vb[VbLINQVbFeatures#8](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_8.vb)]  
  
 変数名にラムダ式の定義を割り当てるでき、名前を使用して、関数を呼び出すことができます。 次の例では、4 も表示されます。  
  
 [!code-vb[VbLINQVbFeatures#12](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_9.vb)]  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ラムダ式の多くは、標準クエリ演算子の基になります。 コンパイラなど、基本的なクエリのメソッドで定義されている計算をキャプチャするラムダ式を作成する`Where`、 `Select`、 `Order By`、 `Take While`、およびその他。  
  
 たとえば、次のコードは、学生のリストからすべてのスキルの限られた受講者を返すクエリを定義します。  
  
 [!code-vb[VbLINQVbFeatures#9](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_10.vb)]  
  
 クエリの定義は次の例は、の引数を指定する 2 つのラムダ式を使用して次のようなコードにコンパイル`Where`と`Select`です。  
  
 [!code-vb[VbLINQVbFeatures#10](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_11.vb)]  
  
 使用していずれかのバージョンを実行することができます、`For Each`ループ。  
  
 [!code-vb[VbLINQVbFeatures#11](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/features-that-support-linq_12.vb)]  
  
 詳しくは、「[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
