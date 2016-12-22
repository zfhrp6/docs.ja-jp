---
title: "&#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct | Microsoft Docs"
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
  - "vbc32500"
  - "bc32500"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32500"
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;attribute&gt;&#39; cannot be applied because the format of the GUID &#39;&lt;number&gt;&#39; is not correct
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`COMClassAttribute` 属性ブロックで、グローバル一意識別子 \(GUID: Globally Unique Identifier\) の形式として有効でない GUID が指定されています。  `COMClassAttribute` では、GUID を使用してクラス、インターフェイス、および作成イベントを一意に識別します。  
  
 GUID は 16 バイトで構成され、前の 8 バイトは数値、後の 8 バイトはバイナリです。  GUID は uuidgen.exe などの Microsoft ユーティリティで生成され、空間および時間内で一意であることが保証されています。  
  
 **Error ID:** BC32500  
  
### このエラーを解決するには  
  
1.  COM オブジェクトを識別するために必要な正しい GUID を決定します。  
  
2.  `COMClassAttribute` 属性ブロックに示される GUID 文字列が正しくコピーされていることを確認します。  
  
## 参照  
 <xref:System.Guid>   
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)