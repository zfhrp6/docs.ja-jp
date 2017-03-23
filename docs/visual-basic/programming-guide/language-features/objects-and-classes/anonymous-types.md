---
title: "Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.AnonymousType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "anonymous types [Visual Basic], about anonymous types"
  - "anonymous types [Visual Basic]"
  - "types [Visual Basic], anonymous"
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
caps.latest.revision: 46
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 46
---
# Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic では匿名型がサポートされています。匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。  クラスは、コンパイラによって生成されます。  このクラスには使用可能な名前がなく、<xref:System.Object> から直接継承します。また、オブジェクトの宣言時に指定したプロパティを格納します。  データ型の名前が指定されないので、*匿名型*と呼ばれます。  
  
 次の例では、`product` を、`Name` と `Price` という 2 つのプロパティを持つ匿名型のインスタンスとして宣言して作成します。  
  
 [!code-vb[VbVbalrAnonymousTypes#1](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_1.vb)]  
  
 *クエリ式*では、匿名型を使用して、クエリによって選択されたデータの列を結合します。  特定のクエリで選択される列を予測できないので、結果の型を事前に定義することはできません。  匿名型を使用すると、任意の数の列を任意の順序で選択するクエリを記述できます。  コンパイラによって、指定したプロパティと指定した順序と一致するデータ型が作成されます。  
  
 次の例では、`products` は、多数のプロパティを持つ製品オブジェクトの一覧です。  `namePriceQuery` 変数は、実行すると `Name` と `Price` という 2 つのプロパティを持つ匿名型のインスタンスのコレクションが返されるクエリの定義を保持します。  
  
 [!code-vb[VbVbalrAnonymousTypes#2](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_2.vb)]  
  
 `nameQuantityQuery` 変数は、実行すると `Name` と `OnHand` という 2 つのプロパティを持つ匿名型のインスタンスのコレクションが返るクエリの定義を保持します。  
  
 [!code-vb[VbVbalrAnonymousTypes#3](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_3.vb)]  
  
 匿名型に対してコンパイラが作成するコードの詳細については、「[Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)」を参照してください。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラによって生成されるので、コンパイルするたびに変更される可能性があります。  プロジェクトの再コンパイル時に変更される可能性があるので、コード内で匿名型の名前を使用したり、依存したりすることは避けてください。  
  
## 匿名型の宣言  
 匿名型のインスタンスの宣言では、型のプロパティを指定する初期化子リストを使用します。  匿名型の宣言時には、プロパティだけを指定でき、メソッドやイベントなどのその他のクラス要素は指定できません。  次の例の `product1` は、`Name` と `Price` という 2 つのプロパティを持つ匿名型のインスタンスです。  
  
 [!code-vb[VbVbalrAnonymousTypes#4](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_4.vb)]  
  
 プロパティを主要なプロパティとして指定した場合は、それらのプロパティを使用して、2 つの匿名型のインスタンスの等価性を比較できます。  ただし、主要なプロパティの値は変更できません。  詳細については、このトピックで後述する「主要なプロパティ」のセクションを参照してください。  
  
 匿名型のインスタンスの宣言は、オブジェクト初期化子による名前付きの型のインスタンスの宣言に似ています。  
  
 [!code-vb[VbVbalrAnonymousTypes#5](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_5.vb)]  
  
 匿名型のプロパティを指定する他の方法の詳細については、「[方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)」を参照してください。  
  
## 主要なプロパティ  
 主要なプロパティは、次に示す点で、主要ではないプロパティとは根本的に異なります。  
  
-   2 つのインスタンスが等価かどうかを決定する際は、主要なプロパティの値だけが比較されます。  
  
-   主要なプロパティの値は読み取り専用であり、変更できません。  
  
-   主要なプロパティの値だけが、コンパイラによって生成される匿名型用のハッシュ コードのアルゴリズムに含まれます。  
  
### 等価比較  
 匿名型のインスタンスは、同じ匿名型のインスタンスである場合のみ、等価になることができます。  コンパイラは、2 つのインスタンスが次の条件に適合する場合、同型のインスタンスとみなします。  
  
-   同一のアセンブリの中で宣言されている。  
  
-   プロパティの名前と推論された型が同じであり、同じ順序で宣言されている。  名前の比較では、大文字と小文字が区別されません。  
  
-   各インスタンスで、同じプロパティが主要なプロパティとしてマークされている。  
  
-   各宣言内の少なくとも 1 つのプロパティが、主要なプロパティである。  
  
 主要なプロパティを持たない匿名型のインスタンスは、自身に対してのみ等価です。  
  
 [!code-vb[VbVbalrAnonymousTypes#6](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_6.vb)]  
  
 同じ匿名型の 2 つのインスタンスは、主要なプロパティの値が等しければ、等価です。  次の例は、等価性のテスト方法を示しています。  
  
 [!code-vb[VbVbalrAnonymousTypes#7](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_7.vb)]  
  
### 読み取り専用値  
 キー プロパティの値は変更できません。  たとえば、前の例の `prod8` の場合、`Name` フィールドと `Price` フィールドは `read-only` ですが、`OnHand` は変更できます。  
  
 [!code-vb[VbVbalrAnonymousTypes#8](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_8.vb)]  
  
## クエリ式の匿名型  
 クエリ式では、常に匿名型を作成する必要があるわけではありません。  可能な場合は、既存の型を使用して列データを保持します。  これは、クエリでデータ ソースからレコード全体が返された、または各レコードから 1 つのフィールドだけが返された場合に発生します。  次のコード例では、`customers` は、`Customer` クラスのオブジェクトのコレクションです。  このクラスには多くのプロパティがあり、その中の 1 つ以上を、任意の順序でクエリ結果に含めることができます。  最初の 2 つの例では、クエリで名前付きの型の要素が選択されるため、匿名型は必要ありません。  
  
-   `cust.Name` が文字列なので、`custs1` には文字列のコレクションが格納されます。  
  
     [!code-vb[VbVbalrAnonymousTypes#30](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_9.vb)]  
  
-   `customers` の各要素は `Customer` オブジェクトであり、クエリによって要素全体が選択されたので、`custs2` には `Customer` オブジェクトのコレクションが格納されます。  
  
     [!code-vb[VbVbalrAnonymousTypes#31](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_10.vb)]  
  
 ただし、適切な名前付きの型を常に使用できるとは限りません。  ある目的のために顧客と住所を、別の目的で顧客 ID と所在地を、さらに別の目的で顧客名、住所、および注文履歴を選択する必要があるとします。  匿名型を使用すると、結果を保持するための新しい名前付きの型を先に宣言しなくても、任意のプロパティを任意の順序で組み合わせて選択できます。  プロパティのコンパイルのたびに、コンパイラによって匿名型が作成されます。  次のクエリでは、`customers` 内の各 `Customer` オブジェクトから、顧客の名前と ID 番号だけを選択します。  したがって、コンパイラは、これら 2 つのプロパティだけを格納する匿名型を作成します。  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_11.vb)]  
  
 匿名型のプロパティの名前とデータ型は、両方とも、`Select` の引数である `cust.Name` と `cust.ID` から取得されます。  クエリによって作成される匿名型のプロパティは、常に主要なプロパティになります。  次の `For Each` ループの中で `custs3` が実行された場合、結果は、`Name` と `ID` という 2 つの主要なプロパティを持つ匿名型のインスタンスのコレクションになります。  
  
 [!code-vb[VbVbalrAnonymousTypes#33](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_12.vb)]  
  
 `custs3` で表されるコレクション内の要素は厳密に型指定されるので、IntelliSense を使用して、使用可能なプロパティのナビゲーションとそれらの型の検証を実行できます。  
  
 詳細については、「[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)」を参照してください。  
  
## 匿名型を使用するかどうかの決定  
 オブジェクトを匿名クラスのインスタンスとして作成する前に、それが最善の選択肢かどうかを考慮します。  たとえば、関連するデータを格納する一時的なオブジェクトを作成するときに、クラス全体に格納されている可能性があるその他のフィールドやメソッドを必要としない場合、匿名型は適切なソリューションです。  宣言ごとに異なるプロパティを選択する、またはプロパティの順序を変更する場合にも、匿名型は便利です。  ただし、プロジェクトに、固定された順序の同じプロパティを持つ複数のオブジェクトが含まれている場合は、クラス コンストラクターと名前付きの型を使用する方が簡単に宣言できます。  たとえば、適切なコンストラクターを使用すると、`Product` クラスの複数のインスタンスの宣言は、匿名型の複数のインスタンスの宣言より簡単です。  
  
 [!code-vb[VbVbalrAnonymousTypes#9](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_13.vb)]  
  
 名前付きの型で有利なもう 1 つの点は、プロパティ名のタイプミスをコンパイラが検出できることです。  前の例では、`firstProd2`、`secondProd2`、および `thirdProd2` は、同じ匿名型のインスタンスであることを意図しています。  ただし、`thirdProd2` を次のいずれかの方法で誤って宣言した場合、その型は、`firstProd2` および `secondProd2` の型と一致しなくなります。  
  
 [!code-vb[VbVbalrAnonymousTypes#10](../../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/anonymous-types_14.vb)]  
  
 さらに重要なのは、匿名型の使用に関しては、名前付きの型には適用されない制約があることです。  `firstProd2`、`secondProd2`、および `thirdProd2` は、同じ匿名型のインスタンスです。  ただし、共有される匿名型の名前は、コード内で型名が必要とされる場所には使用不可であり、記述できません。  たとえば、匿名型を使用してメソッド シグネチャを定義したり、別の変数またはフィールドを宣言したりすることはできません。また、型宣言の中では匿名型を使用できません。  結果として、匿名型は、メソッド間で情報を共有する必要がある場合には適していません。  
  
## 匿名型の定義  
 コンパイラは、匿名型のインスタンスの宣言に応答して、指定されたプロパティを含む新しいクラス定義を作成します。  
  
 匿名型に、少なくとも 1 つの主要なプロパティが含まれている場合、定義は、<xref:System.Object> から継承された 3 つのメンバー \(<xref:System.Object.Equals%2A>、<xref:System.Object.GetHashCode%2A>、および <xref:System.Object.ToString%2A>\) をオーバーライドします。  等価性をテストし、ハッシュ コード値を決定するために生成されるコードは、主要なプロパティだけを考慮します。  匿名型に主要なプロパティが含まれていない場合は、<xref:System.Object.ToString%2A> だけがオーバーライドされます。  明示的に名前を付けられた匿名型のプロパティは、これらの生成されるメソッドと競合することはできません。  つまり、`.Equals`、`.GetHashCode`、または `.ToString` を使用してプロパティに名前を付けることはできません。  
  
 少なくとも 1 つの主要なプロパティを持つ匿名型の定義は、<xref:System.IEquatable%601?displayProperty=fullName> インターフェイスも実装します \(`T` は匿名型の型です\)。  
  
 コンパイラによって作成されるコードと、オーバーライドされたメソッドの機能については、「[Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)」を参照してください。  
  
## 参照  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Anonymous Type Definition](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)