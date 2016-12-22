---
title: "Clipboard format is not valid | Microsoft Docs"
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
  - "vbrID460"
dev_langs: 
  - "VB"
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Clipboard format is not valid
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定されたクリップボード形式は、実行中のメソッドと互換性がありません。  このエラーでは以下の原因が考えられます。  
  
-   クリップボードの `GetText` メソッドまたは `SetText` メソッドを、`vbCFText` または `vbCFLink` 以外のクリップボード形式で使用している場合。  
  
-   クリップボードの `GetData` メソッドまたは `SetData` メソッドを、`vbCFBitmap`、`vbCFDIB`、または `vbCFMetafile` 以外のクリップボード形式で使用している場合。  
  
-   `DataObject` の `GetData` メソッドまたは `SetData` メソッドを、Microsoft Windows によって登録済み形式用に予約されている範囲 \(&HC000\-&HFFFF\) にあるクリップボード形式と一緒に使用しているが、その形式が Microsoft Windows に登録されていない場合。  
  
### このエラーを解決するには  
  
-   無効な形式を削除し、有効な形式を指定します。  
  
## 参照  
 [クリップボード : その他のデータ形式の追加](../Topic/Clipboard:%20Adding%20Other%20Formats.md)