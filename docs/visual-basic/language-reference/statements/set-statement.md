---
title: "Set Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Set"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "property procedures, Set statements"
  - "Set statement"
  - "Set statement, syntax"
  - "write-only properties"
  - "properties [Visual Basic], write-only"
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Set Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

値をプロパティに代入するための `Set` プロパティ プロシージャを宣言します。  
  
## 構文  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## 指定項目  
 `attributelist`  
 省略可能です。  「[属性リスト](../../../visual-basic/language-reference/statements/attribute-list.md)」を参照してください。  
  
 `accessmodifier`  
 省略可能です。このプロパティの `Get` ステートメントか `Set` ステートメントの一方に指定できます。  次のいずれかになります。  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 「[Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。  
  
 `value`  
 必ず指定します。  このパラメーターには、プロパティの新しい値が格納されます。  
  
 `datatype`  
 `Option Strict` が `On` の場合は、必ず指定します。  `value` パラメーターのデータ型を指定します。  指定するデータ型は、この `Set` ステートメントを宣言するプロパティのデータ型と同じにする必要があります。  
  
 `statements`  
 省略可能です。  `Set` プロパティ プロシージャの呼び出し時に実行される 1 つ以上のステートメントを指定します。  
  
 `End Set`  
 必ず指定します。  `Set` プロパティ プロシージャの定義を終了します。  
  
## 解説  
 `ReadOnly` のマークが付けられたプロパティを除き、すべてのプロパティは `Set` プロパティ プロシージャを持つ必要があります。  `Set` プロシージャは、プロパティの値を設定するために使用されます。  
  
 プロパティに保存する値が代入ステートメントで指定された場合、Visual Basic は自動的にプロパティの `Set` プロシージャを呼び出します。  
  
 Visual Basic は、プロパティの割り当ての際に、パラメーターを `Set` プロシージャに渡します。  `Set` のパラメーターを指定しないと、統合開発環境 \(IDE: Integrated Development Environment\) では `value` というパラメーターが暗黙的に使用されます。  このパラメーターには、プロパティに代入する値が含まれています。  通常、この値はプライベートなローカル変数に格納しますが、`Get` プロシージャを呼び出せばいつでも値を取得できます。  
  
 プロパティ宣言の本体には、プロパティの `Get` プロシージャと `Set` プロシージャのみを [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) ステートメントと `End Property` ステートメントの間に記述できます。  それ以外のプロシージャを含めることはできません。  特に、プロパティの現在の値を含めることはできません。  現在の値をどちらかのプロパティ プロシージャの内部に含めると他のプロパティ プロシージャから値にアクセスできなくなるため、この値はプロパティの外部に格納する必要があります。  通常は、プロパティと同じレベルで [Private](../../../visual-basic/language-reference/modifiers/private.md) 変数を宣言し、この中に現在の値を格納します。  `Set` プロシージャが適用されるプロパティには、このプロシージャを内部に定義する必要があります。  
  
 `Set` ステートメント内で `accessmodifier` を使ってアクセス レベルを設定しない限り、既定で `Set` プロシージャのアクセス レベルは、それが含まれるプロパティと同じになります。  
  
## 規則  
  
-   **アクセス レベルの混在。**読み書き可能なプロパティを定義する場合、必要であれば `Get` プロシージャと `Set` プロシージャのどちらか一方にだけ、プロパティとは異なるアクセス レベルを指定できます。  これを指定する場合は、プロシージャにプロパティよりも制限の高いアクセス レベルを指定する必要があります。  たとえば、プロパティを `Friend` で宣言する場合、`Set` プロシージャを `Private` で宣言できますが、`Public` では宣言できません。  
  
     `WriteOnly` プロパティを宣言している場合は、`Set` プロシージャはプロパティ全体を表します。  別のアクセス レベルを `Set` に宣言するとプロパティに 2 つのアクセス レベルを設定することになるので、このような宣言はできません。  
  
## \[動作\]  
  
-   **プロパティ プロシージャからの制御の戻り。** `Set` プロシージャから呼び出し元のコードに制御が戻るとき、プロパティに格納する値を渡したステートメントの直後から実行が続行されます。  
  
     `Set` プロパティ プロシージャは、[Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) または [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) を使って呼び出し元に戻ることができます。  
  
     `Exit Property` ステートメントおよび `Return` ステートメントは、プロパティ プロシージャを直ちに終了します。  プロシージャの任意の場所に、`Exit Property` ステートメントと `Return` ステートメントを何度でも定義できます。また、`Exit Property` ステートメントと `Return` ステートメントを混在して使用できます。  
  
## 使用例  
 `Set` ステートメントを使って、プロパティの値を設定するコード例を次に示します。  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## 参照  
 [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md)   
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)