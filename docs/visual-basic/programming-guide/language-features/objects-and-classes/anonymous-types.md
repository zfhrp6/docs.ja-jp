---
title: 匿名型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: 451fe45c9b5efbeb64b1066d6ba8e5f9b27300c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656257"
---
# <a name="anonymous-types-visual-basic"></a>匿名型 (Visual Basic)
Visual Basic では、匿名型は、使用すると、データ型のクラス定義を記述することがなくオブジェクトの作成をサポートします。 クラスは、コンパイラによって生成されます。 クラスの使用可能な名前を持たないから直接継承<xref:System.Object>オブジェクトの宣言で指定したプロパティが含まれます。 データ型の名前が指定されていないため、呼びます、*匿名型*です。  
  
 次の例を宣言し、変数を作成`product`を 2 つのプロパティを持つ匿名型のインスタンスとして`Name`と`Price`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 A*クエリ式*匿名型を使用して、クエリによって選択されたデータの列を結合します。 特定のクエリで選択される列を予測できないために、結果の型を事前に定義できません。 匿名型を使用すると、任意の順序で、列の任意の数を選択するクエリを記述できます。 コンパイラでは、指定されたプロパティおよび指定した順序と一致するデータ型を作成します。  
  
 次の例についてで`products`それぞれが多数のプロパティを持つ製品オブジェクトの一覧を示します。 変数`namePriceQuery`が実行されるときに、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`Price`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 変数`nameQuantityQuery`が実行されるときに、2 つのプロパティを持つ匿名型のインスタンスのコレクションを返すクエリの定義を保持`Name`と`OnHand`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 匿名型のためにコンパイラによって作成されたコードの詳細については、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)です。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラが生成され、コンパイルするたびに異なる場合があります。 コード必要がありますいないを使用してに依存したり、匿名型の名前のプロジェクトが再コンパイルするとき、名前が変わる可能性があります。  
  
## <a name="declaring-an-anonymous-type"></a>匿名型の宣言  
 匿名型のインスタンスの宣言は、型のプロパティを指定するのに、初期化子リストを使用します。 匿名型、いないその他のクラスなどの要素メソッドまたはイベントを宣言する場合は、プロパティのみを指定できます。 次の例では、`product1`を 2 つのプロパティを持つ匿名型のインスタンス:`Name`と`Price`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 プロパティをキー プロパティとして指定する場合は、2 つの匿名型のインスタンスの等価性を比較に使用できます。 ただし、キー プロパティの値を変更できません。 詳細については、このトピックの後半のキーのプロパティ セクションを参照してください。  
  
 オブジェクト初期化子を使用して名前付きの型のインスタンスを宣言するようが匿名型のインスタンスを宣言することに注意してください。  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 匿名型プロパティを指定するには、その他の方法の詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。  
  
## <a name="key-properties"></a>キー プロパティ  
 キー プロパティは、いくつかの基本的な方法でキー以外のプロパティと異なります。  
  
-   2 つのインスタンスが等しいかどうかを判断するためには、キー プロパティの値のみが比較されます。  
  
-   キー プロパティの値は、読み取り専用し、変更できません。  
  
-   のみ、コンパイラによって生成されたコードに対してハッシュ アルゴリズム、匿名型のキー プロパティの値が含まれています。  
  
### <a name="equality"></a>等価比較  
 匿名型のインスタンスは、同じ匿名型のインスタンスの場合のみ等しいと指定できます。 コンパイラは、次の条件を満たしている場合、同じ型のインスタンスとして 2 つのインスタンスを処理します。  
  
-   同じアセンブリ内で宣言されています。  
  
-   そのプロパティは、同じ名前では、同じ推定された型、および同じ順序で宣言されます。 名前の比較は区別されません。  
  
-   それぞれの同じプロパティがキー プロパティとしてマークされます。  
  
-   各宣言内の少なくとも 1 つのプロパティは、キー プロパティです。  
  
 キー プロパティを持たない匿名型のインスタンスが自身に対してのみです。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 同じ匿名型の 2 つのインスタンスは、主要なプロパティの値が等しい場合と同じです。 次の例では、等しいかどうかをテストする方法を示しています。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### <a name="read-only-values"></a>読み取り専用の値  
 キー プロパティの値を変更することはできません。 たとえば、`prod8`前の例で、`Name`と`Price`フィールドは`read-only`が`OnHand`変更できます。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## <a name="anonymous-types-from-query-expressions"></a>クエリ式からの匿名型  
 常に、クエリ式では、匿名型の作成を必要はありません。 可能な場合は、列のデータを保持するために既存の型を使用します。 これは、クエリ、データ ソースまたは各レコードから 1 つだけのフィールドからレコード全体が返されるときに発生します。 次のコード例で`customers`のオブジェクトのコレクションには、`Customer`クラスです。 クラスには、多数のプロパティと任意の順序で、クエリ結果のうちの 1 つ以上を含めることができます。 最初の 2 つの例については、匿名型はありません必要なため、クエリは、名前付きの型の要素を選択です。  
  
-   `custs1` に、文字列のコレクションを含む`cust.Name`文字列です。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `custs2` コレクションを格納`Customer`ため、オブジェクトの各要素`customers`は、`Customer`オブジェクト、および全体の要素は、クエリで選択します。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 ただし、適切な名前付きの型は常に使用できません。 顧客名と 1 つの目的、顧客 ID 番号および別の場所のアドレスと顧客の名前、アドレス、および 3 つ目の注文履歴を選択する場合があります。 匿名型を使用すると、最初に結果を保持する新しい名前付きの型を宣言しなくても、任意の順序で、プロパティの任意の組み合わせを選択できます。 代わりに、コンパイラは、プロパティのコンパイルごとの匿名型を作成します。 次のクエリでは各からのみ、顧客の名前と ID 番号が選択`Customer`オブジェクトに`customers`です。 そのため、コンパイラは、これら 2 つのプロパティのみを含んでいる匿名型を作成します。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 名前と匿名型のプロパティのデータ型の両方が引数から取得した`Select`、`cust.Name`と`cust.ID`です。 クエリによって作成される匿名型のプロパティは、常にキー プロパティです。 ときに`custs3`が、次に実行される`For Each`ループ、結果は、2 つのキー プロパティを持つ匿名型のインスタンスのコレクション`Name`と`ID`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 によって表されるコレクション内の要素`custs3`厳密に型指定し、使用可能なプロパティ内を移動し、それらの種類を確認するのには、IntelliSense を使用することができます。  
  
 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)です。  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>匿名型を使用するかどうかを決定します。  
 匿名クラスのインスタンスとしてオブジェクトを作成する前に、最適なオプションであるかどうかを検討してください。 たとえば、関連データを格納する一時オブジェクトを作成する、完全なクラスを含めることができるメソッドとフィールド、その他の必要があるない場合は、匿名型は良いソリューションです。 匿名型は、宣言ごとに異なるプロパティを選択をする場合、またはプロパティの順序を変更する場合にも便利です。 ただし、プロジェクトには、同じプロパティを持つ、一定の順序で複数のオブジェクトが含まれている場合でも宣言できますより簡単にクラス コンス トラクターを持つ名前付きの型を使用しています。 たとえば、適切なコンス トラクターがのいくつかのインスタンスを宣言しやすく、`Product`匿名型の複数のインスタンスを宣言するよりものクラスです。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 名前付きの型のもう 1 つの利点は、コンパイラがプロパティ名のタイプミスをキャッチできることです。 前の例で`firstProd2`、 `secondProd2`、および`thirdProd2`同じ匿名型のインスタンスにする対象としています。 ただし、する場合は誤って宣言`thirdProd2`、次の方法の 1 つは、その型とは異なるの`firstProd2`と`secondProd2`です。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 さらに、名前付きの型のインスタンスに適用されない匿名型の使用に関する制限事項があります。 `firstProd2`、 `secondProd2`、および`thirdProd2`、同じ匿名型のインスタンスであります。 ただし、共有の匿名型の名前を使用できないが、型名は、コードで、必要なことはできません。 たとえば、匿名型を使用して、別の変数またはフィールド、または任意の型宣言で宣言するメソッドのシグネチャを定義することはできません。 その結果、メソッドの間で情報を共有する必要があるとき匿名型は適していません。  
  
## <a name="an-anonymous-type-definition"></a>匿名型の定義  
 匿名型のインスタンスの宣言に応答してでは、コンパイラは、指定したプロパティを格納する新しいクラス定義を作成します。  
  
 匿名型には、少なくとも 1 つのキー プロパティが含まれている場合、定義によって上書きから継承した 3 つのメンバー <xref:System.Object>: <xref:System.Object.Equals%2A>、 <xref:System.Object.GetHashCode%2A>、および<xref:System.Object.ToString%2A>です。 等価性をテストし、ハッシュ コード値がキー プロパティだけを考慮を決定するために生成されるコード。 匿名型が含まれていないキーのプロパティでのみ<xref:System.Object.ToString%2A>はオーバーライドします。 匿名型のプロパティを明示的に指定されたこれらの生成されたメソッドと競合することはできません。 つまり、使用することはできません`.Equals`、 `.GetHashCode`、または`.ToString`プロパティの名前を付ける。  
  
 匿名型の定義には、少なくとも 1 つを持つキー プロパティも実装して、<xref:System.IEquatable%601?displayProperty=nameWithType>インターフェイス、場所`T`匿名型の型です。  
  
 詳細について、コンパイラとのオーバーライドされたメソッドの機能で作成したコードは、次を参照してください。[匿名の型定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)です。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト初期化子 : 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [匿名型の定義](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)
