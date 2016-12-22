---
title: "Property let procedure not defined and property get procedure did not return an object | Microsoft Docs"
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
  - "vbrID451"
dev_langs: 
  - "VB"
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Property let procedure not defined and property get procedure did not return an object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティ、メソッド、および演算の中には、`Collection` にしか適用できないものがあります。  コレクションにしか適用できない演算またはプロパティが、コレクション以外のオブジェクトに対して指定されています。  
  
### このエラーを解決するには  
  
1.  オブジェクト名およびプロパティ名のスペルを確認するし、オブジェクトが `Collection` オブジェクトであることを確認します。  
  
2.  コレクションにオブジェクトを追加するのに使用した `Add` メソッドの構文が正しく、各識別子のスペルが正しいことを確認します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Collection>