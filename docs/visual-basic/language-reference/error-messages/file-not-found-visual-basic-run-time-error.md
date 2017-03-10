---
title: "File not found (Visual Basic Run-Time Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID53"
dev_langs: 
  - "VB"
ms.assetid: 57addb16-6f9a-444d-8af8-dda52431daca
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# File not found (Visual Basic Run-Time Error)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定された場所にファイルがありませんでした。  このエラーでは以下の原因が考えられます。  
  
-   ステートメントが、存在しないファイルを参照しています。  
  
-   ダイナミック リンク ライブラリ \(DLL: dynamic\-link library\) 内のプロシージャを呼び出していますが、`Declare` ステートメントの `Lib` 句で指定されたライブラリが見つかりません。  
  
-   存在しないプロジェクトを開こうとしたか、存在しないテキスト ファイルを読み込もうとしました。  
  
### このエラーを解決するには  
  
1.  ファイル名のスペルとパスの指定を確認します。  
  
## 参照  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)