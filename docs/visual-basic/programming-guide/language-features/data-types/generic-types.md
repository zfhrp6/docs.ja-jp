---
title: "Visual Basic (Visual Basic) におけるジェネリック型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- generic interfaces
- data type arguments, defining
- generic delegates
- arguments [Visual Basic], data types
- Of keyword, using
- delegates, generic
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- procedures, generic
- generic procedures
- data types [Visual Basic], generic
- data types [Visual Basic], as parameters
- generics [Visual Basic], generic types
- data types [Visual Basic], as arguments
- generic classes, Visual Basic
- parameters, type
- type arguments
- interfaces, generic
- generics [Visual Basic]
- types [Visual Basic], generic
- parameters, generic
- generic structures
- generic classes
- type parameters
- data type arguments
- structures, generic
- parameters, data type
- collections, generic
- classes [Visual Basic], generic
- data type parameters, defining
- type arguments, defining
- arguments [Visual Basic], type
ms.assetid: 89f771d9-ecbb-4737-88b8-116b63c6cf4d
caps.latest.revision: 45
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
ms.openlocfilehash: 1f6c48ff7f72eb86526ed4d71e6259b7886aab25
ms.lasthandoff: 03/13/2017

---
# <a name="generic-types-in-visual-basic-visual-basic"></a>Visual Basic におけるジェネリック型 (Visual Basic)
*ジェネリック型* はさまざまなデータ型に対して同じ機能を実行するために必要な処理を行う、1 つのプログラミング要素です。 ジェネリック クラスまたはジェネリック プロシージャを定義すると、同じ機能を実行させる各データ型に対して、その機能を別々に定義する必要がありません。  
  
 これは、ヘッドの部分が交換可能な、ねじ回しのセットにたとえることができます。 回すねじを調べて、そのねじに合った正しいヘッド (マイナス、プラス、星型) を選択します。 ねじ回しのハンドルに正しいヘッドを挿入したら、ねじ回しを使ってまったく同じ作業 (ねじを回すこと) を行います。  
  
 ![汎用ツールとして設定されたスクリュー ドライバーのダイアグラム](../../../../visual-basic/programming-guide/language-features/data-types/media/genericscrewdriver.gif "GenericScrewDriver")  
汎用的な道具であるねじ回しのセット  
  
 ジェネリック型を定義する場合は、1 つ以上のデータ型でジェネリック型をパラメーター化します。 これにより、ジェネリック型を使用するコードで、データ型をコードの要件に合わせて変更できるようになります。 コードでは、1 つのジェネリックな要素から複数のプログラミング要素を宣言し、それぞれを異なるデータ型のセットに使用できます。 ただし、使用するデータ型が異なっていても、宣言した要素はどれも同じロジックを実行します。  
  
 たとえば、 `String`などの特定のデータ型を操作するキュー クラスを作成し、使用する必要があるとします。 クラスを宣言する<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>次の例を示します</xref:System.Collections.Generic.Queue%601?displayProperty=fullName>。  
  
 [!code-vb[VbVbalrDataTypes&#1;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_1.vb)]  
  
 このときに、 `stringQ` を使って、 `String` 値だけを扱うように指定できます。 `stringQ` は、 `String` 値を汎用的に扱うのではなく `Object` だけを扱うことを意味するので、遅延バインディングまたは型変換は行いません。 その結果、実行時間が短縮され、ランタイム エラーが減少します。  
  
 ジェネリック型の使用に関する詳細については、次を参照してください。[方法: ジェネリック クラスを使用して](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)します。  
  
## <a name="example-of-a-generic-class"></a>ジェネリック クラスの例  
 次の例は、ジェネリック クラスのスケルトン定義を示しています。  
  
 [!code-vb[VbVbalrDataTypes&#2;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_2.vb)]  
  
 このスケルトンでは、 `t` は *型パラメーター*です。これはプレースホルダーなので、このクラスを宣言するときにはデータ型で置き換えます。 コードの他の部分では、 `classHolder` をさまざまなデータ型で置き換えることにより、 `t`のさまざまなバージョンを宣言できます。 このようにして宣言した&2; つのクラスを次の例に示します。  
  
 [!code-vb[VbVbalrDataTypes&#3;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_3.vb)]  
  
 このステートメントでは、 *構成されるクラス*を宣言し、その中で型パラメーターを特定の型に置き換えています。 この置き換えは、構成されるクラスのコード全体に反映されます。 次の例は、 `processNewItem` の `integerClass`プロシージャがどのようなコードになるかを示しています。  
  
 [!code-vb[VbVbalrDataTypes&4;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_4.vb)]  
  
 完全な例では、次を参照してください。[方法: 機能を定義する、クラス、ことができます提供と同じ別のデータ型に](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)します。  
  
## <a name="eligible-programming-elements"></a>使用できるプログラミング要素  
 ジェネリック クラス、構造体、インターフェイス、プロシージャ、およびデリゲートを定義して使用することができます。 なお、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]いくつかのジェネリック クラス、構造、およびよく使用される一般的な要素を表すインターフェイスを定義します。 <xref:System.Collections.Generic?displayProperty=fullName>名前空間は、ディクショナリ、リスト、キュー、およびスタックを提供します</xref:System.Collections.Generic?displayProperty=fullName>。 独自のジェネリックな要素を定義する前に既に<xref:System.Collections.Generic?displayProperty=fullName>。</xref:System.Collections.Generic?displayProperty=fullName>で利用可能なかどうかを参照してください。  
  
 プロシージャは型ではありませんが、ジェネリック プロシージャを定義し、使用できます。 参照してください[Visual Basic におけるジェネリック プロシージャ](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)します。  
  
## <a name="advantages-of-generic-types"></a>ジェネリック型の利点  
 ジェネリック型は、それぞれが特定のデータ型を操作する複数のプログラミング要素を宣言するための基礎となります。 ジェネリック型の代わりになるものを以下に示します。  
  
1.  `Object` データ型を操作する単一の型。  
  
2.  型の *型固有* バージョンのセット。それぞれのバージョンは、個別にコーディングされ、 `String`、 `Integer`、または `customer`などのユーザー定義型などの特定のデータ型を操作します。  
  
 ジェネリック型には、これらの代替手段にはない次の利点があります。  
  
-   **タイプ セーフです。** ジェネリック型では、コンパイル時に型がチェックされます。 一方、 `Object` に基づく型はすべてのデータ型を受け入れるので、入力したデータ型が受け入れられる型かどうかをチェックするコードを記述する必要があります。 ジェネリック型を使うと、型の不一致は実行する前にコンパイラで検出できます。  
  
-   **パフォーマンスを改善。** それぞれが特定の&1; つのデータ型に特化されるので、データを *ボックス化* したり、 *unボックス化* したりする必要がありません。 `Object` に基づいて操作を実行する場合、入力したデータ型をボックス化して `Object` に変換したり、出力時にデータのボックス化を解除したりする必要があります。 ボックス化とボックス化解除は、パフォーマンスを低下させます。  
  
     また、 `Object` に基づく型は遅延バインディングでもあります。つまり、この型のメンバーにアクセスするには、実行時に余分なコードが必要になります。 これも、パフォーマンスを低下させます。  
  
-   **コードの統合。** ジェネリック型のコードの定義は、一度だけ行う必要があります。 1 つの型の一連の型固有バージョンでは、同じコードが各バージョンに複製されます。バージョンによって異なるのは、扱うデータ型だけです。 ジェネリック型では、すべての型固有バージョンが元のジェネリック型から生成されます。  
  
-   **コードの再利用をします。** 特定のデータ型に依存しないコードは、ジェネリックである場合に、さまざまなデータ型で再利用できます。 予期しなかったデータ型に再利用できることもあります。  
  
-   **IDE のサポート。** ジェネリック型から宣言した構成型を使用すると、コードの開発中に統合開発環境 (IDE) から提供されるサポートが増えます。 たとえば、IntelliSense は、コンストラクターまたはメソッドに対して引数の型固有のオプションを示します。  
  
-   **ジェネリックなアルゴリズム。** 型に依存しない抽象アルゴリズムは、ジェネリック型にすることをお勧めします。 <xref:System.IComparable>インターフェイスを使用すると、 <xref:System.IComparable>。</xref:System.IComparable>を実装する任意のデータ型を</xref:System.IComparable>使用して項目を並べ替えてジェネリック プロシージャなど、  
  
## <a name="constraints"></a>制約  
 ジェネリック型定義のコードはできる限り型に依存しない必要がありますが、なんらかのデータ型の機能がジェネリック型に必要な場合もあります。 たとえば、並べ替えまたは照合するために&2; つの項目を比較する場合は、そのデータ型必要があります実装、<xref:System.IComparable>インターフェイス</xref:System.IComparable>。 この要件を強制するには、 *制約* を型パラメーターに追加します。  
  
### <a name="example-of-a-constraint"></a>制約の例  
 次の例は、 <xref:System.IComparable>。</xref:System.IComparable>を実装する型引数が必要な制約が設定されたクラスのスケルトンの定義を示しています。  
  
 [!code-vb[VbVbalrDataTypes&#5;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_5.vb)]  
  
 後続のコードからクラスを作成しようとしました場合`itemManager`を実装しない型を指定して<xref:System.IComparable>、コンパイラはエラーです。</xref:System.IComparable> 。  
  
### <a name="types-of-constraints"></a>制約の種類  
 次の要件を任意に組み合わせて制約を指定できます。  
  
-   型引数は、1 つまたは複数のインターフェイスを実装する必要があります  
  
-   型引数は、クラスの型そのものであるか、最大&1; つのクラスを継承する必要があります  
  
-   型引数はパラメーターなしのコンストラクターを公開し、そのコンストラクターからオブジェクトを作成するコードで使用できる必要があります  
  
-   型引数は、 *参照型*である、または *値型*である必要があります  
  
 複数の要件を指定する場合は、コンマで区切られた *制約リスト* を中かっこ (`{ }`) で囲みます。 含めるをアクセス可能なコンス トラクターを必要とする、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)一覧のキーワードです。 参照型であることを必須とするには、 `Class` キーワードを追加し、値型であることを必須とするには、 `Structure` キーワードを追加します。  
  
 制約の詳細については、次を参照してください。[型リスト](../../../../visual-basic/language-reference/statements/type-list.md)します。  
  
### <a name="example-of-multiple-constraints"></a>複数の制約の例  
 次の例は、型パラメーターに制約リストがあるジェネリック クラスのスケルトン定義を示しています。 をこのクラスのインスタンスを作成したコードで型引数必要があります両方を実装、<xref:System.IComparable>と<xref:System.IDisposable>インターフェイスの参照型であるし、アクセス可能なパラメーターなしコンス トラクターを公開します。</xref:System.IDisposable> </xref:System.IComparable>  
  
 [!code-vb[VbVbalrDataTypes&6;](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/generic-types_6.vb)]  
  
## <a name="important-terms"></a>重要な用語  
 ジェネリック型に関連して、以下の新しい用語が使用されます。  
  
-   *ジェネリック型*。 宣言時に少なくとも&1; つのデータ型を指定するクラス、構造体、インターフェイス、プロシージャ、またはデリゲートの定義です。  
  
-   *型パラメーター*。 ジェネリック型定義で、型を宣言するときにデータ型の代わりに指定するプレースホルダーです。  
  
-   *型引数*。 構成型をジェネリック型から宣言するときに、型パラメーターを置き換える特定のデータ型です。  
  
-   *制約*。 型パラメーターに指定できる型引数を制限する条件です。 型引数が特定のインターフェイスを実装すること、特定のクラスであるか特定のクラスを継承すること、アクセス可能なパラメーターなしのコンストラクターを持つこと、または参照型または値型であることを強制できます。 このような制約は組み合わせて指定できますが、指定できるのは&1; つのクラスだけです。  
  
-   *構成型*。 型パラメーターに型引数を指定してジェネリック型から宣言されるクラス、構造体、インターフェイス、プロシージャ、またはデリゲートです。  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [として](../../../../visual-basic/language-reference/statements/as-clause.md)   
 [オブジェクトのデータ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [ジェネリックの共変性と反変性](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8)   
 [反復子](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)
