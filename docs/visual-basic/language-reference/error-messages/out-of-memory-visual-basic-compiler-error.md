---
title: "Out of memory (Visual Basic Compiler Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc2004"
  - "bc2004"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC2004"
ms.assetid: 6bc0939c-e279-4875-a91c-f4076860b5b9
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Out of memory (Visual Basic Compiler Error)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

メモリが不足しています。  
  
 **Error ID:** BC2004  
  
### このエラーを解決するには  
  
-   不要なアプリケーション、ドキュメント、およびソース ファイルを閉じます。  
  
-   不要なコントロールおよびフォームを削除して、同時に読み込まれる数を減らします。  
  
-   `Public` 変数の数を減らします。  
  
-   ディスクの空き容量を調べてください。  
  
-   追加のメモリを取り付けるかメモリの再割り当てを実行して、利用可能な RAM の容量を増やします。  
  
-   必要なくなった場合にメモリが解放されていることを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)