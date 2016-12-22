---
title: "Operator Statement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.operator"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "operators [Visual Basic]"
  - "procedures, operator"
  - "Narrowing keyword, conversion operators"
  - "Visual Basic code, operators"
  - "Widening keyword, conversion operators"
  - "syntax, Operator procedures"
  - "operators [Visual Basic], overloading"
  - "overloaded operators"
  - "operator overloading"
  - "operator procedures"
  - "Operator statement"
  - "CType function, Operator statement"
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator Statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クラスまたは構造体に演算子プロシージャを定義する演算子記号、オペランド、およびコードを宣言します。  
  
## 構文  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## 指定項目  
 `attrlist`  
 省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。  
  
 `Public`  
 必ず指定します。  この演算子プロシージャのアクセス レベルが [Public](../../../visual-basic/language-reference/modifiers/public.md) であることを示します。  
  
 `Overloads`  
 省略可能です。  [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md) を参照してください。  
  
 `Shared`  
 必ず指定します。  この演算子プロシージャが [Shared](../../../visual-basic/language-reference/modifiers/shared.md) プロシージャであることを示します。  
  
 `Shadows`  
 省略可能です。  [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) を参照してください。  
  
 `Widening`  
 `Narrowing` を指定した場合を除き、変換演算子には必ず指定します。  この演算子プロシージャが [Widening](../../../visual-basic/language-reference/modifiers/widening.md) 変換を定義することを示します。  このヘルプ ページの「拡大変換と縮小変換」を参照してください。  
  
 `Narrowing`  
 `Widening` を指定した場合を除き、変換演算子には必ず指定します。  この演算子プロシージャが [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) 変換を定義することを示します。  このヘルプ ページの「拡大変換と縮小変換」を参照してください。  
  
 `operatorsymbol`  
 必ず指定します。  この演算子プロシージャが定義する演算子の記号または識別子を指定します。  
  
 `operand1`  
 必ず指定します。  単項演算子 \(変換演算子を含む\) の単一オペランドまたは二項演算子の左オペランドの名前および型を指定します。  
  
 `operand2`  
 二項演算子では必ず指定します。  二項演算子の右オペランドの名前と型を指定します。  
  
 `operand1` および `operand2` の構文と指定項目は、以下のとおりです。  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|指定項目|Description|  
|----------|-----------------|  
|`ByVal`|省略可能ですが、指定項目は常に [ByVal](../../../visual-basic/language-reference/modifiers/byval.md) で渡します。|  
|`operandname`|必ず指定します。  このオペランドを表す変数の名前を指定します。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`operandtype`|`Option Strict` が `On` である場合を除き、省略可能です。  このオペランドのデータ型を指定します。|  
  
 `type`  
 `Option Strict` が `On` である場合を除き、省略可能です。  この演算子プロシージャによって返される値のデータ型を指定します。  
  
 `statements`  
 省略可能です。  演算子プロシージャが実行するステートメントのブロックを指定します。  
  
 `returnvalue`  
 必ず指定します。  演算子プロシージャから呼び出し元のコードに返す値を指定します。  
  
 `End` `Operator`  
 必ず指定します。  この演算子プロシージャの定義を終了します。  
  
## 解説  
 `Operator` は、クラスまたは構造体の中でのみ使用できます。  つまり、演算子の*宣言コンテキスト*をソース ファイル、名前空間、モジュール、インターフェイス、プロシージャ、またはブロックにすることはできません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 すべての演算子は `Public Shared` にする必要があります。  どちらのオペランドにも `ByRef`、`Optional`、または `ParamArray` を指定することはできません。  
  
 演算子の記号または識別子を使って戻り値を返すことはできません。  `Return` ステートメントを使用し、値を指定する必要があります。  `Return` ステートメントは、プロシージャ内の任意の位置で何回でも指定できます。  
  
 `Overloads` キーワードを使うかどうかに関係なく、この方法で演算子を定義することは*演算子オーバーロード*と呼ばれます。  次の表は、定義できる演算子の一覧です。  
  
|種類|演算子|  
|--------|---------|  
|単項式|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|変換 \(単項\)|`CType`|  
  
 二項演算の一覧に示した `=` 演算子は、代入演算子ではなく比較演算子です。  
  
 `CType` を定義するときは、`Widening` または `Narrowing` を指定する必要があります。  
  
## 一致したペア  
 特定の演算子を一致したペアとして定義する必要があります。  ペアの一方の演算子を定義する場合には、もう一方の演算子も定義する必要があります。  一致するペアを以下に示します。  
  
-   `=` と `<>`  
  
-   `>` と `<`  
  
-   `>=` と `<=`  
  
-   `IsTrue` と `IsFalse`  
  
## データ型の制限  
 定義する演算子には、定義先のクラスまたは構造体が伴っている必要があります。  つまり、そのクラスまたは構造体が以下の要素のデータ型として指定される必要があります。  
  
-   単項演算子のオペランド。  
  
-   二項演算子の少なくとも 1 つのオペランド。  
  
-   変換演算子のオペランドまたは戻り値の型。  
  
 一部の演算子には、次のようなデータ型の制限もあります。  
  
-   `IsTrue` 演算子および `IsFalse` 演算子を定義する場合は、両方が `Boolean` 型を返す必要があります。  
  
-   `<<` 演算子および `>>` 演算子を定義する場合は、両方が `operand2` の `operandtype` に`Integer` 型を指定する必要があります。  
  
 戻り値の型は、どちらかのオペランドの型と同じである必要はありません。  たとえば、`=` または `<>` などの比較演算子は、オペランドが両方とも `Boolean` ではない場合でも、`Boolean` を返すことができます。  
  
## 論理演算子およびビット処理演算子  
 `And`、`Or`、`Not`、および `Xor` の各演算子は、Visual Basic では論理演算またはビット単位の演算を実行できます。  ただし、このような演算子の 1 つをクラスまたは構造体に定義する場合は、ビット単位の演算だけを定義できます。  
  
 `AndAlso` 演算子は、`Operator` ステートメントには直接定義できません。  ただし、以下の条件が満たされる場合は、`AndAlso` を使用できます。  
  
-   `AndAlso` に使用するオペランド型と同じ型で `And` を定義した。  
  
-   `And` からの戻り値として、定義先のクラスまたは構造体と同じ型を指定した。  
  
-   `And` を定義したクラスまたは構造体に `IsFalse` 演算子を定義した。  
  
 同様に、`Or` を同じオペランドで定義し、クラスまたは構造体の戻り値の型を使用し、クラスまたは構造体に `IsTrue` を定義した場合に、`OrElse` を使用できます。  
  
## 拡大変換と縮小変換  
 *拡大変換*は実行時に常に成功しますが、*縮小変換*は実行時に失敗することがあります。  詳細については、「[Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 変換プロシージャを `Widening` で宣言する場合、プロシージャ コードではエラーを生成しないでください。  これは、次のことを意味します。  
  
-   `type` 型の有効な値を常に返す必要がある。  
  
-   生成される可能性のあるすべての例外およびその他のエラー条件を処理する必要がある。  
  
-   呼び出したプロシージャから返されたエラーはコードで処理する必要がある。  
  
 変換プロシージャでエラーが起こる可能性がある場合、つまり変換プロシージャで未処理の例外が起こる可能性がある場合は、そのプロシージャを `Narrowing` で宣言する必要があります。  
  
## 使用例  
 次のコード例は、`Operator` ステートメントを使用して、`And`、`Or`、`IsFalse`、および `IsTrue` の各演算子の演算子プロシージャを持つ構造体の外枠を定義します。  `And` および `Or` は、`abc` 型の 2 つのオペランドと `abc` 型の戻り値を持ちます。  `IsFalse` および `IsTrue` は、`abc` 型の単一オペランドを持ち、`Boolean` 型を返します。  このように定義すると、呼び出し元のコードは、`And`、`AndAlso`、`Or`、および `OrElse` を `abc` 型のオペランドと一緒に使用できます。  
  
 [!code-vb[VbVbalrStatements#44](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/operator-statement_1.vb)]  
  
## 参照  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)   
 [How to: Call an Operator Procedure](../Topic/How%20to:%20Call%20an%20Operator%20Procedure%20\(Visual%20Basic\).md)   
 [How to: Use a Class that Defines Operators](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)