---
title: "Too many files | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID67"
dev_langs: 
  - "VB"
ms.assetid: 2ff203e2-bba6-43ae-b72f-8e92a881c98f
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Too many files
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

オペレーティング システムの制限を超える数のファイルがルート ディレクトリに作成されているか、CONFIG.SYS ファイルの **files\=** 設定で指定された数を超えるファイルが開かれています。  
  
### このエラーを解決するには  
  
1.  プログラムでルート ディレクトリ内のファイルに対して、開く、閉じる、または保存の操作を行っている場合は、サブディレクトリが使用されるようにプログラムを変更します。  
  
2.  CONFIG.SYS ファイルの **files\=** 設定で指定するファイルの数を増やし、コンピューターを再起動します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)