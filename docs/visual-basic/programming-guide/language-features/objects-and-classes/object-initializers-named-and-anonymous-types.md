---
title: "Object Initializers: Named and Anonymous Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.ObjectInitializer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "object initializers [Visual Basic]"
  - "anonymous types [Visual Basic], object initializers"
  - "initializing properties [Visual Basic]"
  - "initializers [Visual Basic]"
  - "named types [Visual Basic]"
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Object Initializers: Named and Anonymous Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オブジェクト初期化子を使用すると、1 つの式で複雑なオブジェクトのプロパティを指定できます。  名前付きの型および匿名型のインスタンスの作成に使用できます。  
  
## Declarations  
 名前付きの型と匿名型のインスタンスの宣言はほとんど同じように見えますが、その効果は同じではありません。  それぞれのカテゴリに、固有の機能と制限があります。  次の例では、オブジェクト初期化子リストを使用して、名前付きのクラス `Customer` のインスタンスを宣言して初期化する簡単な方法を示します。  クラスの名前は、`New` キーワードの後で指定します。  
  
 [!code-vb[VbVbalrObjectInit#1](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_1.vb)]  
  
 匿名型には、使用できる名前はありません。  したがって、匿名型のインスタンス化には、クラス名を含めることはできません。  
  
 [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_2.vb)]  
  
 2 つの宣言の要件と結果は同じではありません。  `namedCust` の場合は、`Name` プロパティを持つ `Customer` クラスが既に存在している必要があり、宣言ではそのクラスのインスタンスが作成されます。  `anonymousCust` の場合は、コンパイラが 1 つのプロパティつまり `Name` という名前の文字列を持つ新しいクラスを定義し、そのクラスの新しいインスタンスを作成します。  
  
## 名前付きの型  
 オブジェクト初期化子は、1 つのステートメントで型のコンストラクターを呼び出して一部または全部のプロパティの値を設定する、簡単な方法を備えています。  コンパイラは、ステートメントに適したコンストラクターを呼び出します。つまり、引数がない場合は既定のコンストラクターを使用し、引数が 1 つでもある場合はパラメーター化されたコンストラクターを使用します。  その後、初期化子リストで指定されている順序で、指定したプロパティが初期化されます。  
  
 初期化子リストでの各初期化では、クラスのメンバーに初期値が代入されます。  メンバーの名前とデータ型は、クラスが定義されるときに決定されます。  次の例では、`Customer` クラスが存在し、文字列値を受け付ける `Name` および `City` という名前のメンバーを持っている必要があります。  
  
 [!code-vb[VbVbalrObjectInit#3](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_3.vb)]  
  
 または、次のコードを使用して同じ結果を得ることもできます。  
  
 [!code-vb[VbVbalrObjectInit#4](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_4.vb)]  
  
 これらの各宣言は、次の例と同等です。この例では、既定のコンストラクターを使用して `Customer` オブジェクトを作成した後、`With` ステートメントを使用して `Name` プロパティと `City` プロパティの初期値を指定しています。  
  
 [!code-vb[VbVbalrObjectInit#5](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_5.vb)]  
  
 `Customer` クラスに、`Name` の値を指定できるようにするパラメーター化されたコンストラクターが含まれる場合は、たとえば、次のような方法で `Customer` オブジェクトを宣言して初期化することもできます。  
  
 [!code-vb[VbVbalrObjectInit#6](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_6.vb)]  
  
 次のコードで示すように、すべてのプロパティを初期化する必要はありません。  
  
 [!code-vb[VbVbalrObjectInit#7](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_7.vb)]  
  
 ただし、初期化リストは空にできません。  初期化しないプロパティは既定値のままになります。  
  
### 名前付きの型での型の推論  
 オブジェクト初期化子とローカル型の推論を組み合わせることで、`cust1` を宣言するためのコードを短縮できます。  この方法を使用すると、変数宣言での `As` 句を省略できます。  変数のデータ型は、代入によって作成されるオブジェクトの型から推論されます。  次の例では、`cust6` の型は `Customer` です。  
  
 [!code-vb[VbVbalrObjectInit#8](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_8.vb)]  
  
### 名前付きの型についての解説  
  
-   オブジェクト初期化子リストでクラスのメンバーを 2 回以上初期化することはできません。  `cust7` の宣言はエラーになります。  
  
     [!code-vb[VbVbalrObjectInit#9](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_9.vb)]  
  
-   メンバーは、それ自体または別のフィールドの初期化に使用できます。  次の例での `cust8` の宣言のように、初期化する前のメンバーにアクセスすると、既定値が使用されます。  オブジェクト初期化子を使用する宣言が処理されるとき、最初に行われるのは、適切なコンストラクターの呼び出しです。  その後、初期化子リストの個別のフィールドが初期化されます。  次の例では、`cust8` には `Name` の既定値が代入され、`cust9` には初期化された値が代入されます。  
  
     [!code-vb[VbVbalrObjectInit#10](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_10.vb)]  
  
     次の例では、`cust3` と `cust4` のパラメーター化されたコンストラクターを使用して、`cust10` と `cust11` を宣言および初期化しています。  
  
     [!code-vb[VbVbalrObjectInit#11](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_11.vb)]  
  
-   オブジェクト初期化子は入れ子にできます。  次の例では、`AddressClass` は 2 つのプロパティ `City` と `State` を持つクラスであり、`Customer` クラスには `AddressClass` のインスタンスである `Address` プロパティがあります。  
  
     [!code-vb[VbVbalrObjectInit#12](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_12.vb)]  
  
-   初期化リストは空にできません。  
  
-   Object 型のインスタンスを初期化することはできません。  
  
-   初期化するクラスのメンバーとして、共有メンバー、読み取り専用メンバー、定数、またはメソッド呼び出しを指定することはできません。  
  
-   インデックス付きのクラス メンバーまたは修飾されたクラス メンバーは初期化できません。  次の例では、コンパイラ エラーが発生します。  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## 匿名型  
 匿名型は、オブジェクト初期化子を使用して、明示的に定義および名前付けされていない新しい型のインスタンスを作成します。  コンパイラは、オブジェクト初期化子リストで指定されているプロパティに従って型を生成します。  型の名前が指定されないので、*匿名型*と呼ばれます。  たとえば、次の宣言と、前に示した `cust6` の宣言を比較してください。  
  
 [!code-vb[VbVbalrObjectInit#13](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_13.vb)]  
  
 構文上の違いは、データ型の `New` の後に名前の指定がないことだけです。  しかし、処理はまったく異なります。  コンパイラは、2 つのプロパティ `Name` と `City` を持つ新しい匿名型を定義し、指定された値でその型のインスタンスを作成します。  型の推論により、この例での `Name` と `City` の型は文字列に決まります。  
  
> [!CAUTION]
>  匿名型の名前は、コンパイラによって生成されるので、コンパイルのたびに変わる可能性があります。  コードで、匿名型の名前を使用したり名前に依存したりすることはできません。  
  
 型の名前を使用できないので、`As` 句を使用して `cust13` を宣言することはできません。  型は推論される必要があります。  遅延バインディングを使用しない場合、これによりローカル変数に対する匿名型の使用は制限されます。  
  
 匿名型は、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリのサポートにとって重要です。  クエリでの匿名型の使用の詳細については、「[Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」および「[Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)」を参照してください。  
  
### 匿名型についての解説  
  
-   通常、匿名型の宣言におけるすべて、またはほとんどすべてのプロパティはキー プロパティであり、プロパティ名の前に `Key` キーワードを付けることで指定します。  
  
     [!code-vb[VbVbalrObjectInit#14](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_14.vb)]  
  
     キー プロパティの詳細については、「[Key](../../../../visual-basic/language-reference/modifiers/key.md)」を参照してください。  
  
-   名前付きの型と同様に、匿名型の定義の初期化子リストでは、少なくとも 1 つのプロパティを宣言する必要があります。  
  
     [!code-vb[VbVbalrObjectInit#2](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_2.vb)]  
  
-   匿名型のインスタンスを宣言すると、コンパイラは一致する匿名型の定義を生成します。  プロパティの名前とデータ型はインスタンスの宣言から取得され、コンパイラによって定義に組み込まれます。  名前付きの型とは異なり、事前にプロパティに名前が設定され、プロパティが定義されることはありません。  型は推論されます。  `As` 句を使用して、プロパティのデータ型を指定することはできません。  
  
-   匿名型では、プロパティの名前と値を設定する方法は他にもいくつかあります。  たとえば、匿名型のプロパティは、変数の名前と値、または別のオブジェクトのプロパティの名前と値を取得できます。  
  
     [!code-vb[VbVbalrObjectInit#15](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/visualbasic/object-initializers-name_15.vb)]  
  
     匿名型のプロパティを定義するオプションの詳細については、「[方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)」を参照してください。  
  
## 参照  
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)   
 [Key](../../../../visual-basic/language-reference/modifiers/key.md)   
 [How to: Declare an Object by Using an Object Initializer](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)