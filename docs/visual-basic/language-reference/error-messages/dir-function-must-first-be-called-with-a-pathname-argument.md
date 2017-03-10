---
title: "&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrDIR_IllegalCall"
dev_langs: 
  - "VB"
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# &#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Dir` 関数の最初の呼び出しに `PathName` 引数が記述されていません。  `Dir` の最初の呼び出しには `PathName` を記述する必要がありますが、`Dir` の以降の呼び出しでは次のアイテムを取得するためのパラメーターを記述する必要はありません。  
  
### このエラーを解決するには  
  
1.  関数の呼び出しに `PathName` 引数を指定します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>