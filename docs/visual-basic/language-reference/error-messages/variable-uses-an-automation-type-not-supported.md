---
title: "Variable uses an Automation type not supported in Visual Basic | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID458"
dev_langs: 
  - "VB"
ms.assetid: bde4f4da-493b-452c-b6e4-1d370edba4cd
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# Variable uses an Automation type not supported in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

タイプ ライブラリまたはオブジェクト ライブラリで定義されている変数を使おうとしましたが、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でサポートされていないデータ型が含まれています。  
  
### このエラーを解決するには  
  
-   [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で認識される型の変数を使用します。  
  
     または  
  
-   `FileGet` または `FileGetOBject` の使用時にこのエラーが発生する場合は、使おうとしているファイルが `FilePut` または `FilePutObject` によって書き込みが行われたことを確認します。  
  
## 参照  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)