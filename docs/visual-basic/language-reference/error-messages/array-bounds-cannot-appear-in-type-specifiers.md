---
title: "Array bounds cannot appear in type specifiers | Microsoft Docs"
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
  - "vbc30638"
  - "bc30638"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30638"
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Array bounds cannot appear in type specifiers
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

配列のサイズをデータ型指定子の中で宣言することはできません。  
  
 **Error ID:** BC30638  
  
### このエラーを解決するには  
  
-   型の後ではなく、変数名の直後で配列のサイズを指定します。次に例を示します。  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   配列を定義し、必要な要素の数で初期化します。次に例を示します。  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## 参照  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)