---
title: "How to: Declare a Structure (Visual Basic) | Microsoft Docs"
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
  - "declarations, structures"
  - "structure statements"
  - "statements [Visual Basic], structure"
  - "structures, declaring"
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare a Structure (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

構造体宣言は、[Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) で開始し、`End` `Structure` ステートメントで終了します。  この 2 つのステートメントの間に、少なくとも 1 つの*要素*を宣言する必要があります。  要素にはすべてのデータ型を使用できますが、少なくとも 1 つは、非共有変数または非共有で非カスタムのイベントのいずれかである必要があります。  
  
 構造体の宣言で構造体の要素を初期化することはできません。  構造体型の変数を宣言するときは、変数をとおして要素にアクセスすることにより、要素に値を代入します。  
  
 構造体とクラスとの違いに関する詳細については、「[Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)」を参照してください。  
  
 デモの目的で、従業員の名前、内線番号、および給与を追跡する状況を考えてみます。  構造体により、単一の変数でこれを行うことができます。  
  
### 構造体を宣言するには  
  
1.  構造体の開始ステートメントと終了ステートメントを作成します。  
  
     [Public](../../../../visual-basic/language-reference/modifiers/public.md) キーワード、[Protected](../../../../visual-basic/language-reference/modifiers/protected.md) キーワード、[Friend](../../../../visual-basic/language-reference/modifiers/friend.md) キーワード、または [Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを使用して、構造体のアクセス レベルを指定できます。または既定の `Public` に設定できます。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  構造体の本体に要素を追加します。  
  
     構造体は、少なくとも 1 つの要素を持つ必要があります。  すべての要素を宣言し、それぞれのアクセス レベルを指定する必要があります。  キーワードを指定せずに [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用する場合、アクセシビリティは既定で `Public` になります。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     上の例の `salary` フィールドは、`Private` です。つまり、含まれているクラスからでも、構造体の外部ではアクセスできません。  ただし、`giveRaise` プロシージャは `Public` であるため、構造体以外から呼び出すことができます。  同様に、構造体以外から `salaryReviewTime` イベントを発生させることができます。  
  
     変数、`Sub` プロシージャ、およびイベントに加え、定数、`Function` プロシージャ、およびプロパティも構造体で定義できます。  *既定のプロパティ*としてプロパティを 1 つ指定できます。ただし、少なくとも 1 つの引数を指定する必要があります。  イベントは [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` プロシージャを使用して処理できます。  詳細については、「[How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)」を参照してください。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [User\-Defined Data Type](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)