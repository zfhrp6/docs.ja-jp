---
title: "This array is fixed or temporarily locked (Visual Basic) | Microsoft Docs"
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
  - "vbrID10"
dev_langs: 
  - "VB"
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# This array is fixed or temporarily locked (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このエラーでは以下の原因が考えられます。  
  
-   固定サイズの配列の要素数を変更するために `ReDim` を使用しています。  
  
-   モジュール レベルの動的配列を再定義しようとしていますが、その配列の要素の 1 つがプロシージャに引数として渡されています。  要素が引数として渡された場合、その配列はロックされ、プロシージャ内の参照パラメーターのメモリが解放されなくなります。  
  
-   配列を含む `Variant` 変数に値を代入しようとしましたが、その `Variant` は現在ロックされています。  
  
### このエラーを解決するには  
  
1.  `ReDim` を使用して元の配列を固定ではなく動的として宣言するか \(配列がプロシージャ内で宣言されている場合\)、要素数を指定せずに宣言します \(配列がモジュール レベルで宣言されている場合\)。  
  
2.  その要素を渡す必要があるのかどうかを確認します。これは、要素がモジュール内のすべてのプロシージャから参照できるためです。  
  
3.  `Variant` がロックされている原因を判断し、解決します。  
  
## 参照  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)