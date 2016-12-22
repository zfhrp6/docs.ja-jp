---
title: "Enumerations and Name Qualification (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations, enumerations"
  - "Imports statement, namespace declarations"
  - "declaring namespaces, enumerations"
  - "name collisions"
  - "ambiguous names, enumerations"
  - "enumerations [Visual Basic], name qualification"
  - "names, avoiding conflicts"
  - "namespaces, declaring"
  - "naming conflicts, enumerations"
  - "naming conflicts, qualifying names"
  - "declaring enumerations"
  - "references, enumeration members"
  - "naming conventions, naming conflicts"
  - "declarations, namespaces"
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Enumerations and Name Qualification (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

通常、列挙型のメンバーを参照する場合は、その列挙型の名前で修飾する必要があります。  たとえば、列挙型 `Days` のメンバー `Sunday` を参照するには、次の構文を使います。  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## Imports ステートメントの使用  
 次の例に示すように、コードの名前空間宣言セクションに `Imports` ステートメントを追加すると、完全限定名を使わなくても済むようになります。  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports` ステートメントは、参照されるプロジェクトおよびアセンブリから、およびステートメントが使用されるモジュールと同じプロジェクト内から、名前空間の名前をインポートします。  このステートメントを追加すると、次のように、修飾子を付けずに列挙型のメンバーを参照できるようになります。  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 関連する定数を列挙型にまとめると、同じ定数名を異なるコンテキストで使うことができます。  たとえば、列挙型 `Days` と列挙型 `WorkDays` の両方で、曜日の定数に対して同じ名前を使用できます。  列挙型で `Imports` ステートメントを使う場合は、あいまいな参照にならないように注意する必要があります。  次に例を示します。  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 `Monday` が `Days` と `Workdays` の両方の列挙型のメンバーになっている場合、このコードはコンパイラ エラーになります。  定数を個別に参照するときにあいまいな参照を回避するには、定数名を列挙型で修飾します。  次のコードは、列挙型 `Days` と列挙型 `WorkDays` の定数 `Saturday` を参照します。  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## 参照  
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)