---
title: "オブジェクト初期化子: 名前付きで匿名型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ObjectInitializer
dev_langs:
- VB
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d684ad4f3dd47dc7400ea401a94660af832ef866
ms.lasthandoff: 03/13/2017

---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>オブジェクト初期化子: 名前付きの型と匿名型 (Visual Basic)
オブジェクト初期化子を使用すると、1 つの式を使用して、複雑なオブジェクトのプロパティを指定できます。 名前付きの型と匿名型のインスタンスを作成して、使用できます。  
  
## <a name="declarations"></a>宣言  
 名前付きで匿名型のインスタンスの宣言はほとんど同じように確認できますが、その効果が同じではありません。 各カテゴリには、独自の機能と制限があります。 次の例を宣言し、名前付きクラスのインスタンスを初期化するための便利な方法を示しています。 `Customer`、オブジェクト初期化子リストを使用しています。 キーワードの後に、クラスの名前が指定されていることに注意してください。`New`します。  
  
 [!code-vb[VbVbalrObjectInit&#1;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_1.vb)]  
  
 匿名型には、使用可能な名前がありません。 そのため、匿名型のインスタンス化では、クラス名を含めることはできません。  
  
 [!code-vb[VbVbalrObjectInit&#2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
 要件と&2; つの宣言の結果は同じです。 `namedCust`、`Customer`を持つクラス、`Name`プロパティが既に存在し、宣言は、そのクラスのインスタンスを作成します。 `anonymousCust`、コンパイラと呼ばれる文字列の&1; つのプロパティを使用する新しいクラスを定義`Name`、し、そのクラスの新しいインスタンスを作成します。  
  
## <a name="named-types"></a>名前付きの型  
 オブジェクト初期化子は、型のコンス トラクターを呼び出すし、単一のステートメントでの一部またはすべてのプロパティの値を設定する簡単な方法を提供します。 コンパイラは、ステートメントの適切なコンス トラクターを呼び出します。 既定のコンス トラクターの引数が何も表示されない場合、または&1; つまたは複数の引数を渡す場合にパラメーター化されたコンス トラクターです。 その後、指定したプロパティは、初期化子リストに示されている順序で初期化されます。  
  
 初期化子リスト内の各初期化は、クラスのメンバーへの初期値の割り当てで構成されます。 クラスが定義されている場合、名前と、メンバーのデータ型が決まります。 次の例で、`Customer`クラスが存在し、あるメンバーという名前の必要があります`Name`と`City`文字列の値を受け取ることができます。  
  
 [!code-vb[VbVbalrObjectInit&#3;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_3.vb)]  
  
 または、次のコードを使用して、同じ結果を取得できます。  
  
 [!code-vb[VbVbalrObjectInit&4;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_4.vb)]  
  
 これらの宣言は次の例は、作成に相当する`Customer`既定のコンス トラクターを使用して、オブジェクトし、の初期値を指定、`Name`と`City`プロパティを使用して、`With`ステートメントです。  
  
 [!code-vb[VbVbalrObjectInit&#5;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_5.vb)]  
  
 場合、`Customer`クラスには、パラメーター化されたコンス トラクター値を送信することができますにはが含まれています。 `Name`、なども宣言して初期化、`Customer`次の方法でオブジェクト。  
  
 [!code-vb[VbVbalrObjectInit&6;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_6.vb)]  
  
 次のコードに示すように、すべてのプロパティを初期化する必要はありません。  
  
 [!code-vb[VbVbalrObjectInit&#7;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_7.vb)]  
  
 ただし、初期化リストを空にすることはできません。 初期化されていないプロパティは、既定値を保持します。  
  
### <a name="type-inference-with-named-types"></a>名前付きの型と型の推論  
 宣言のコードを短く`cust1`オブジェクト初期化子とローカル型推論を結合します。 これは、省略することにより、`As`変数の宣言内の句。 変数のデータ型は、代入によって作成されるオブジェクトの型から推論されます。 次の例の種類で`cust6`は`Customer`です。  
  
 [!code-vb[VbVbalrObjectInit&#8;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_8.vb)]  
  
### <a name="remarks-about-named-types"></a>名前付きの型についての解説  
  
-   クラスのメンバーには、オブジェクト初期化子リストに&1; つ以上の時間を初期化できません。 宣言`cust7`エラーが発生します。  
  
     [!code-vb[VbVbalrObjectInit&#9;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_9.vb)]  
  
-   メンバーは、そのリング自体または別のフィールドを初期化するために使用できます。 初期化された、次の宣言と同様にする前に、メンバーがアクセスされる場合`cust8`既定値が使用されます。 オブジェクト初期化子を使用する宣言が処理されるときに最初に行われるが適切なコンス トラクターが呼び出されることに注意してください。 その後は、初期化子リスト内の各フィールドが初期化されます。 既定値を次の例で`Name`が割り当てられている`cust8`、しで初期化された値を割り当てる`cust9`します。  
  
     [!code-vb[VbVbalrObjectInit&#10;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_10.vb)]  
  
     次の例は、パラメーター化されたコンス トラクターから`cust3`と`cust4`を宣言して初期化`cust10`と`cust11`です。  
  
     [!code-vb[VbVbalrObjectInit&#11;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_11.vb)]  
  
-   オブジェクト初期化子が入れ子にすることができます。 次の例で`AddressClass`を&2; つのプロパティを持つクラスは、`City`と`State`、および`Customer`クラスには、`Address`のインスタンスであるプロパティ`AddressClass`します。  
  
     [!code-vb[VbVbalrObjectInit&#12;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_12.vb)]  
  
-   初期化リストを空にすることはできません。  
  
-   初期化中のインスタンスは、Object 型のすることはできません。  
  
-   クラスのメンバーの初期化中には、共有メンバー、読み取り専用のメンバー、定数、またはメソッドの呼び出しをすることはできません。  
  
-   クラスのメンバーの初期化中は、インデックス付きまたは修飾ことはできません。 次の例では、コンパイラ エラーが発生します。  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型では、オブジェクト初期化子を使用して、明示的に定義していない新しい型と名前のインスタンスを作成します。 代わりに、コンパイラは、オブジェクト初期化子リストに指定されているプロパティに従って型を生成します。 型の名前が指定されていないためと呼びます、*匿名型*します。 たとえば、前に、次の宣言を比較`cust6`します。  
  
 [!code-vb[VbVbalrObjectInit&#13;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_13.vb)]  
  
 唯一の違いが構文的に後に名前が指定されていないことは`New`データ型にします。 ただし、動作は大きく異なります。 コンパイラは次の&2; つのプロパティを持つ新しい匿名型を定義`Name`と`City`、し、値を指定して、そのインスタンスを作成します。 型の推定の種類を決定する`Name`と`City`文字列の例です。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラによって生成され、コンパイルするたびに異なる場合があります。 コード使用したり、避けて、匿名型の名前に依存します。  
  
 型の名前を使用できないために使用できません、`As`を宣言する句`cust13`します。 その型を推論する必要があります。 遅延バインディングを使用しない場合は、ローカル変数に匿名型の使用を制限します。  
  
 匿名型の重要なサポートは提供[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]クエリ。 クエリ内で匿名型の使用に関する詳細については、次を参照してください。[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)と[Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。  
  
### <a name="remarks-about-anonymous-types"></a>匿名型についての解説  
  
-   通常、匿名型の宣言におけるプロパティのほとんどまたはすべてでは、キーワードを入力して示されるキー プロパティ`Key`プロパティ名の前にします。  
  
     [!code-vb[VbVbalrObjectInit&#14;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_14.vb)]  
  
     キー プロパティの詳細については、次を参照してください。[キー](../../../../visual-basic/language-reference/modifiers/key.md)します。  
  
-   このような名前付きの型、初期化子リスト匿名型の定義は、少なくとも&1; つのプロパティを宣言する必要があります。  
  
     [!code-vb[VbVbalrObjectInit&#2;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_2.vb)]  
  
-   匿名型のインスタンスを宣言すると、コンパイラは、一致する匿名型の定義を生成します。 名前とプロパティのデータ型インスタンスの宣言から取得され、定義のコンパイラでは追加します。 プロパティがないという名前し、名前付きの型とは異なり、事前に定義されています。 その型が推論されます。 使用して、プロパティのデータ型を指定することはできません、`As`句。  
  
-   匿名型は、その他のいくつかの方法で、名前とそのプロパティの値を確立できますもします。 たとえば、匿名型のプロパティには、名前と、変数、または名前の値と別のオブジェクトのプロパティの値の両方がかかります。  
  
     [!code-vb[VbVbalrObjectInit&#15;](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/object-initializers-named-and-anonymous-types_15.vb)]  
  
     匿名型のプロパティを定義するためのオプションの詳細については、次を参照してください。[方法: 匿名型の宣言におけるプロパティ名の推論と型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [方法: 匿名型の宣言におけるプロパティ名と型の推論](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [キー](../../../../visual-basic/language-reference/modifiers/key.md)   
 [方法 : オブジェクト初期化子を使用してオブジェクトを宣言する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
