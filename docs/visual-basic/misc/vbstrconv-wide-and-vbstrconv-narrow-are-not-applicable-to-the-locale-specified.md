---
title: "VbStrConv.Wide および VbStrConv.Narrow は、指定されたロケールに適用できません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_WideNarrowNotApplicable"
ms.assetid: 5811098c-b124-4caf-8a2b-f81f12f1d5f5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide および VbStrConv.Narrow は、指定されたロケールに適用できません
アプリケーションは `VbStrConv` 列挙型のメンバー `Wide` または `Narrow` を使おうとしていますが、これらのメンバーは指定されたロケールには適用できません。  
  
### このエラーを解決するには  
  
1.  `VbStrConv.Wide` または `VbStrConv.Narrow` のいずれかを削除します。  
  
## 参照  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 列挙型](http://msdn.microsoft.com/ja-jp/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [.NET Framework ベースの国際対応アプリケーションの概要](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)