---
title: "Structure Variables (Visual Basic) | Microsoft Docs"
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
  - "structures, variables"
  - "structures, structure variables"
  - "variables [Visual Basic], structure variables"
  - "structure variables"
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structure Variables (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

構造体を作成したら、その型でプロシージャ レベルの変数およびモジュール レベルの変数を宣言できます。  たとえば、コンピューター システムに関する情報を記録する構造体を作成するとします。  次に例を示します。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 これで、この型の変数を宣言できるようになります。  次に例を示します。  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  クラス内およびモジュール内では、[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用して宣言した構造体は既定でパブリック アクセスになります。  構造体をプライベートにする場合は、[Private](../../../../visual-basic/language-reference/modifiers/private.md) キーワードを使用して宣言します。  
  
## 構造体の値へのアクセス  
 構造体変数の要素で値を代入したり取得したりするには、オブジェクトのプロパティの設定や取得に使用する構文を指定します。  メンバー アクセス演算子 \(`.`\) は、構造体変数名と要素名の間に配置します。  `systemInfo` 型として既に宣言されている変数の要素にアクセスする例を次に示します。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## 構造体変数の代入  
 両方の変数の構造体が同じ型の場合は、ある変数を別の変数に代入できます。  これによって、一方の構造体のすべての要素が、もう一方の構造体の対応する要素にコピーされます。  次に例を示します。  
  
```  
yourSystem = mySystem  
```  
  
 構造体の要素が文字列型 \(`String`\) やオブジェクト型 \(`Object`\) などの参照型である場合は、データへのポインターがコピーされます。  上の例で、`systemInfo` にオブジェクト変数が含まれていたとすると、`mySystem` から `yourSystem` にはポインターがコピーされることになります。そのため、一方の構造体をとおしてオブジェクトのデータに変更を加えると、もう一方の構造体をとおしてアクセスする内容にも変更が反映されます。  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)