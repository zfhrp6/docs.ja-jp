---
title: 'オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 612b1dcea0f776dfd4580803e76f2785e7d28da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655637"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)
オブジェクト初期化子を使用すると、1 つの式を使用して、複雑なオブジェクトのプロパティを指定できます。 名前付きの型と匿名型のインスタンスの作成に使用できます。  
  
## <a name="declarations"></a>宣言  
 匿名の名前付きの型のインスタンスの宣言はほとんど同じように確認できますが、その効果が同じではありません。 各カテゴリには、独自の機能と制限があります。 次の例は、宣言し、名前付きクラスのインスタンスを初期化するための便利な方法を示しています。 `Customer`、オブジェクト初期化子リストを使用しています。 キーワードの後に、クラスの名前が指定されていることを確認`New`です。  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 匿名型には、使用可能な名前がありません。 そのため、匿名型のインスタンス化では、クラス名を含めることはできません。  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 要件および 2 つの宣言の結果は同じです。 `namedCust`、`Customer`を持つクラス、`Name`プロパティが既に存在し、宣言は、そのクラスのインスタンスを作成します。 `anonymousCust`、コンパイラと呼ばれる文字列の 1 つのプロパティを持つ新しいクラスを定義する`Name`、し、そのクラスの新しいインスタンスを作成します。  
  
## <a name="named-types"></a>名前付きの型  
 オブジェクト初期化子は、型のコンス トラクターを呼び出すし、単一のステートメントでの一部またはすべてのプロパティの値を設定する簡単な方法を提供します。 コンパイラは、ステートメントの適切なコンス トラクターを呼び出します: 引数が何も表示されない場合、既定のコンス トラクターまたは 1 つまたは複数の引数が送信される場合にパラメーター化されたコンス トラクターです。 その後、指定したプロパティは初期化子リストに示されている順序で初期化されます。  
  
 初期化子リストで各初期化は、クラスのメンバーに初期値の割り当てで構成されます。 名前と、メンバーのデータ型は、クラスが定義されているときに決定されます。 次の例で、`Customer`クラスが存在し、必要がありますにはメンバー名前付け`Name`と`City`文字列値を受け入れることができます。  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 また、次のコードを使用して、同じ結果を取得できます。  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 これらの各宣言は次の例は、作成、`Customer`既定のコンス トラクターを使用して、オブジェクトし、の初期値を指定し、`Name`と`City`プロパティを使用して、 `With`ステートメント。  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 場合、`Customer`クラスには、の値を送信することができますをパラメーター化されたコンス トラクターが含まれています。 `Name`、たとえば、もを宣言して初期化、`Customer`次の方法でオブジェクト。  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 次のコードに示すように、すべてのプロパティを初期化する必要はありません。  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 ただし、初期化リストを空にすることはできません。 初期化されていないプロパティは、既定値を保持します。  
  
### <a name="type-inference-with-named-types"></a>名前付きの型と型の推論  
 宣言のコードを短縮する`cust1`オブジェクト初期化子とローカル型推論を結合します。 これにより、省略すること、`As`変数の宣言内の句。 変数のデータ型は、割り当てによって作成されるオブジェクトの型から推論されます。 次の例では、型で`cust6`は`Customer`します。  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>名前付きの型についての解説  
  
-   クラスのメンバーは、オブジェクト初期化子リストで複数回初期化できません。 宣言`cust7`エラーが発生します。  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   メンバーは、そのリング自体または別のフィールドを初期化するために使用できます。 メンバーにアクセスしてそれが初期化される前に、次の宣言と同様に場合`cust8`既定値が使用されます。 オブジェクト初期化子を使用する宣言が処理されるときに発生する最初の手順がある適切なコンス トラクターが呼び出されることに注意してください。 その後、初期化子リスト内の各フィールドが初期化されます。 既定値を次の例で`Name`に割り当てられた`cust8`で初期化される値が割り当てられていると`cust9`です。  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     次の例は、パラメーター化されたコンス トラクターから`cust3`と`cust4`を宣言および初期化する`cust10`と`cust11`です。  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   オブジェクト初期化子が入れ子にすることができます。 次の例では、`AddressClass`は 2 つのプロパティを持つクラスである`City`と`State`、および`Customer`クラスには、`Address`のインスタンスであるプロパティ`AddressClass`です。  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   初期化リストを空にすることはできません。  
  
-   初期化されているインスタンスは、Object 型のすることはできません。  
  
-   クラスのメンバーの初期化中には、共有メンバー、読み取り専用のメンバー、定数、またはメソッドの呼び出しをすることはできません。  
  
-   クラスのメンバーの初期化中は、インデックス付きまたは修飾ことはできません。 次の例では、コンパイラ エラーが発生します。  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型では、オブジェクト初期化子を使用して、明示的に定義していない新しい型と名前のインスタンスを作成します。 代わりに、コンパイラは、オブジェクト初期化子リストで指定されているプロパティに従って型を生成します。 型の名前が指定されていないため、呼びます、*匿名型*です。 たとえば、前に、次の宣言を比較`cust6`です。  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 唯一の違いが構文的に後の名前が指定されていないことは`New`データ型。 ただし、動作は大きく異なります。 コンパイラは 2 つのプロパティを持つ新しい匿名型を定義`Name`と`City`、し、値を指定して、そのインスタンスを作成します。 型の推論の種類を決定する`Name`と`City`文字列である例です。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラによって生成され、コンパイルするたびに異なる場合があります。 コードがや使用しない匿名型の名前に依存します。  
  
 使用することはできません型の名前が使用できないため、`As`を宣言する句`cust13`です。 その型を推論する必要があります。 遅延バインディングを使用しない場合は、ローカル変数に匿名型の使用を制限します。  
  
 匿名型には、重要なサポートが提供されます。[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 クエリ内で匿名型の使用に関する詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)です。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型についての解説  
  
-   通常、匿名型の宣言でのプロパティのほとんどまたはすべてにキーのプロパティがあり、キーワードを入力して示される`Key`プロパティ名の前にします。  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     キー プロパティの詳細については、次を参照してください。[キー](../../../../visual-basic/language-reference/modifiers/key.md)です。  
  
-   ような名前付きの型、初期化子リスト匿名型の定義は、少なくとも 1 つのプロパティを宣言する必要があります。  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   匿名型のインスタンスが宣言されると、コンパイラは、一致する匿名型の定義を生成します。 名前とプロパティのデータ型は、インスタンスの宣言からが取得され、定義に、コンパイラによって含まれています。 プロパティがないという名前し、名前付きの型とは異なり、事前に定義されています。 その型が推論されます。 使用して、プロパティのデータ型を指定することはできません、`As`句。  
  
-   匿名型は、その他のいくつかの方法で、名前とそのプロパティの値を確立できますも。 たとえば、匿名型のプロパティには、名前と、変数、または名前の値と別のオブジェクトのプロパティの値の両方がかかります。  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     匿名型のプロパティを定義するためのオプションの詳細については、次を参照してください。[する方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)  
 [方法 : オブジェクト初期化子を使用してオブジェクトを宣言する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
