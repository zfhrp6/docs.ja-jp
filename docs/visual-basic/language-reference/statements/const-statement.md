---
title: "Const Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Const"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Const statement [Visual Basic]"
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# Const Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

1 つ以上の定数を宣言および定義します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## 指定項目  
 `attributelist`  
 省略可能です。  このステートメントで宣言されるすべての定数に適用される属性のリストです。  [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md)が山かっこ \("`<`" および "`>`"\) で囲まれている点に注意してください。  
  
 `accessmodifier`  
 省略可能です。  これらの定数にアクセスできるコードを指定するために使います。  [Public](../../../visual-basic/language-reference/modifiers/public.md)、[Protected](../../../visual-basic/language-reference/modifiers/protected.md)、[Friend](../../../visual-basic/language-reference/modifiers/friend.md)、`Protected Friend`、または [Private](../../../visual-basic/language-reference/modifiers/private.md) を指定できます。  
  
 `Shadows`  
 省略可能です。  基本クラス内のプログラミング要素を宣言し直して隠ぺいする場合に使用します。  「[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。  
  
 `constantlist`  
 必ず指定します。  このステートメントで宣言する定数のリストです。  
  
 `constant` `[ ,` `constant` `... ]`  
  
 `constant` の構文と指定項目は次のとおりです。  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|指定項目|Description|  
|----------|-----------------|  
|`constantname`|必ず指定します。  定数の名前を指定します。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`datatype`|`Option Strict` が `On` の場合は、必ず指定します。  定数のデータ型を指定します。|  
|`initializer`|必ず指定します。  コンパイル時に評価して、定数に代入される式です。|  
  
## 解説  
 決して変わらない値がアプリケーションにある場合は、名前付き定数を定義してリテラル値の代わりに使用できます。  名前は値よりも覚えるのが簡単です。  定数を一度定義すると、コード内の多くの場所でそれを使用できます。  その後のバージョンで値を定義し直すことが必要になった場合も、`Const` ステートメントを変更するだけで済みます。  
  
 `Const` は、モジュール レベルまたはプロシージャ レベルでのみ使用できます。  つまり、変数の*宣言コンテキスト*は、クラス、構造体、モジュール、プロシージャ、またはブロックであることが必要で、ソース ファイル、名前空間、インターフェイスでは宣言できません。  詳細については、「[Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。  
  
 ローカル定数 \(プロシージャ内\) のアクセス レベルは、既定で public になります。このような定数にはアクセス修飾子を指定できません。  クラスおよびモジュールのメンバー定数 \(プロシージャ外\) のアクセス レベルは、既定で private になります。また、構造体のメンバー定数の既定のアクセスレベルは public です。  アクセス修飾子を使用してこれらのアクセス レベルを調整できます。  
  
## 規則  
  
-   **宣言コンテキスト。**モジュール レベルで宣言された、プロシージャの外側にある定数を*メンバー定数*といいます。定数を宣言しているクラス、構造体、またはモジュールのメンバーです。  
  
     プロシージャ レベルで宣言された定数を*ローカル定数*といいます。つまり、それを宣言しているプロシージャまはたブロックに対してローカルという意味です。  
  
-   **属性。**属性を適用できるのはメンバー定数だけで、ローカル定数には適用できません。  属性はアセンブリのメタデータに情報を提供しますが、これはローカル定数などの一時的な格納領域には意味がありません。  
  
-   **修飾子。**既定では、すべての定数が `Shared` であり、`Static` であり、また `ReadOnly` になります。  定数を宣言するとき、これらのどのキーワードも指定できません。  
  
     プロシージャ レベルでは、ローカル定数の宣言に `Shadows` またはアクセス修飾子を指定できません。  
  
-   **複数の定数。**同じ宣言ステートメントに複数の定数を宣言するには、各定数ごとに `constantname` の指定項目を指定します。  複数の定数を指定するときは、コンマ \(,\) で区切ります。  
  
## データ型のルール  
  
-   **データ型。** `Const` ステートメントでは、変数のデータ型を宣言できます。  任意のデータ型、または列挙型の名前を指定できます。  
  
-   **既定の型。** `datatype` を指定しない場合、定数のデータ型は `initializer` のデータ型になります。  `datatype` と `initializer` の両方を指定する場合は、`initializer` のデータ型を `datatype` と互換性のあるものにする必要があります。  `datatype` と `initializer` のどちらも指定しない場合、既定のデータ型は `Object` になります。  
  
-   **異なる型。**複数の定数に異なるデータ型を指定するには、宣言する各変数に対して `As` 句を別々に指定します。  ただし、共通の `As` 句を使って複数の定数を同じ型にすることはできません。  
  
-   **初期化。**すべての定数の値を、`constantlist` で初期化する必要があります。  定数に代入するための式を指定するには、`initializer` を使用します。  式にはリテラル、他の定義済みの定数、および定義済みの列挙体のメンバーを自由に組み合わせることができます。  算術演算子と論理演算子を使って、各要素を組み合わせることもできます。  
  
     `initializer` では、変数または関数は使用できません。  ただし、`CByte` や `CShort` などの変換キーワードは使用できます。  また、`AscW` も使用できます。この場合には、定数の `String` 引数、または `Char` 引数を指定して、コンパイル時に計算できるようにします。  
  
## \[動作\]  
  
-   **スコープ。**ローカル定数には、そのプロシージャまたはブロックの内部からのみアクセスできます。  メンバー定数にはそのクラス、構造体、またはモジュール内の任意の場所からアクセスできます。  
  
-   **修飾。**クラス、構造体、またはモジュールの外部のコードで使用する場合は、その名前でメンバー定数の名前を修飾する必要があります。  プロシージャやブロックの外部のコードは、その内部にあるローカル定数を参照できません。  
  
## 使用例  
 `Const` ステートメントを使って、リテラル値の代わりに使用する定数を宣言するコード例は、次のとおりです。  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/const-statement_1.vb)]  
  
## 使用例  
 データ型が `Object` である定数を定義すると、Visual Basic コンパイラはそれを `Object` 型ではなく、`initializer` 型にします。  次の例では、定数 `naturalLogBase` のランタイム型は `Decimal` です。  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/const-statement_2.vb)]  
  
 この例では、`CStr` を使用して <xref:System.Type> を `String` に変換できないため、[GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md) から返された <xref:System.Type> オブジェクトの <xref:System.Type.ToString%2A> メソッドが使用されます。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Constants and Enumerations](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Constants and Enumerations](../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)