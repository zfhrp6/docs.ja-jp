---
title: "Number of indices exceeds the number of dimensions of the indexed array | Microsoft Docs"
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
  - "bc30106"
  - "vbc30106"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30106"
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Number of indices exceeds the number of dimensions of the indexed array
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

配列要素へのアクセスに使用するインデックスの数は、配列のランク、つまり配列について宣言した次元の数と同じである必要があります。  
  
 **Error ID:** BC30106  
  
### このエラーを解決するには  
  
-   添字の合計数が配列のランクと同じになるまで、配列参照から添字を削除します。  次に例を示します。  
  
    ```  
    [Visual Basic]  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## 参照  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)