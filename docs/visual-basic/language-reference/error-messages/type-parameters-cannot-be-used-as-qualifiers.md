---
title: "Type parameters cannot be used as qualifiers | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32098"
  - "bc32098"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32098"
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Type parameters cannot be used as qualifiers
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プログラミング要素を修飾する文字列に型パラメーターが含まれています。  
  
 型パラメーターは、ジェネリック型を作成するときに渡す型に関する要件を表します。  型パラメーターは、特定の定義済みの型を表しません。  修飾文字列には、コンパイル時に定義されている要素だけを含める必要があります。  
  
 このエラーは、次のようなステートメントで発生します。  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 **Error ID:** BC32098  
  
### このエラーを解決するには  
  
1.  型パラメーターを修飾文字列から削除するか、定義済みの型に置き換えます。  
  
2.  修飾するプログラミング要素を見つけるために、構築型を使用する必要がある場合は、そのためのプログラム ロジックを追加する必要があります。  
  
## 参照  
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)