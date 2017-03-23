---
title: "Get Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Get"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Get statement, syntax"
  - "Get statement"
  - "properties [Visual Basic], read-only"
  - "read-only properties"
  - "Get keyword"
  - "property procedures, Get statements"
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Get Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロパティの値を取得するための `Get` プロパティ プロシージャを宣言します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`attributelist`|省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。|  
|`accessmodifier`|省略可能です。このプロパティの `Get` ステートメントか `Set` ステートメントの一方に指定できます。  次のいずれかになります。<br /><br /> -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。|  
|`statements`|省略可能です。  `Get` プロパティ プロシージャが呼び出されたときに実行する、1 つ以上のステートメントを指定します。|  
|`End Get`|必ず指定します。  この `Get` プロパティ プロシージャの定義を終了します。|  
  
## 解説  
 `WriteOnly` でマーク付けされていないすべてのプロパティに、`Get` プロパティ プロシージャが必要です。  `Get` プロシージャは、プロパティの現在の値を取得するために使用します。  
  
 式でプロパティの値が必要になると、Visual Basic が自動的にプロパティの `Get` プロシージャを呼び出します。  
  
 プロパティ宣言の本体には、プロパティの `Get` プロシージャと `Set` プロシージャのみを [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) ステートメントと `End Property` ステートメントの間に記述できます。  それ以外のプロシージャを含めることはできません。  特に、プロパティの現在の値を含めることはできません。  現在の値をどちらかのプロパティ プロシージャの内部に含めると他のプロパティ プロシージャから値にアクセスできなくなるため、この値はプロパティの外部に格納する必要があります。  通常は、プロパティと同じレベルで [Private](../../../visual-basic/language-reference/modifiers/private.md) 変数を宣言し、この中に現在の値を格納します。  `Get` プロシージャは、それが適用されるプロパティの内側に定義する必要があります。  
  
 `Get` プロシージャの既定のアクセス レベルは、`accessmodifier` を `Get` ステートメントで使用しない限り、その包含プロパティのアクセス レベルになります。  
  
## 規則  
  
-   **アクセス レベルの混在。**読み書き可能なプロパティを定義する場合、必要であれば `Get` プロシージャと `Set` プロシージャのどちらか一方にだけ、プロパティとは異なるアクセス レベルを指定できます。  これを指定する場合は、プロシージャにプロパティよりも制限の高いアクセス レベルを指定する必要があります。  たとえば、プロパティを `Friend` で宣言する場合、`Get` プロシージャを `Private` で宣言できますが、`Public` では宣言できません。  
  
     `ReadOnly` プロパティを定義する場合、プロパティは `Get` プロシージャだけで機能します。  `Get` に違うアクセス レベルを宣言すると、プロパティに 2 つのアクセス レベルを設定することになるため宣言できません。  
  
-   **戻り値の型。** [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)には、プロシージャが返す値のデータ型を宣言できます。  `Get` プロシージャは自動的にそのデータ型を返します。  任意のデータ型か、列挙体、構造体、クラス、またはインターフェイスの名前を指定できます。  
  
     `Property` ステートメントに `returntype` が指定されなければ、プロシージャは `Object` を返します。  
  
## \[動作\]  
  
-   **プロシージャから戻るときの動作** `Get` プロシージャから呼び出し元のコードに制御が戻るとき、プロパティ値を要求したステートメントの内部から実行が続行されます。  
  
     `Get` プロパティ プロシージャは [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md)を使って値を返すか、またはプロパティ名に戻り値を代入して値を返すことができます。  詳細については、「[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)」の "戻り値" を参照してください。  
  
     `Exit Property` ステートメントおよび `Return` ステートメントは、プロパティ プロシージャを直ちに終了します。  プロシージャの任意の場所に、`Exit Property` ステートメントと `Return` ステートメントを何度でも定義できます。また、`Exit Property` ステートメントと `Return` ステートメントを混在して使用できます。  
  
-   **戻り値。** `Get` プロシージャから値を返すには、プロパティ名に値を割り当てるか、または [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) に値を指定します。  `Return` ステートメントは `Get` プロシージャの戻り値を代入すると同時に、プロシージャを終了します。  
  
     プロパティ名に値を代入せずに `Exit Property` を使用すると、`Get` プロシージャは、そのプロパティのデータ型の既定値を返します。  詳細については、「[Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)」の "戻り値" を参照してください。  
  
     次の例は、読み取り専用の `quoteForTheDay` プロパティからプライベート変数 `quoteValue` に格納された値を返すための、2 つの方法を示しています。  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## 使用例  
 次の例は、`Get` ステートメントを使って、プロパティの値を返します。  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## 参照  
 [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)   
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Walkthrough: Defining Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)