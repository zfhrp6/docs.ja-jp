---
title: "Arrays declared as structure members cannot be declared with an initial size | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31043"
  - "bc31043"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31043"
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Arrays declared as structure members cannot be declared with an initial size
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

構造体内の配列が初期サイズを指定して宣言されました。  構造体要素を初期化できません。配列サイズの宣言は、初期化処理の一種です。  
  
 **Error ID:** BC31043  
  
### このエラーを解決するには  
  
1.  構造体内の配列を、サイズの初期化が行われない動的配列として定義します。  
  
2.  特定のサイズの配列が必要な場合は、コードの実行時に [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) を使用して、動的配列を再定義できます。  次に例を示します。  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## 参照  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)