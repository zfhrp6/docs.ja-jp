---
title: "SimplifiedChinese と VbStrConv.TraditionalChinese を組み合わせることはできません。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# SimplifiedChinese と VbStrConv.TraditionalChinese を組み合わせることはできません。
アプリケーションが `VbStrConv` 列挙型メンバー `SimplifiedChinese` と `TraditionalChinese` を結合しようとしていますが、これらは相互に排他的です。  
  
### このエラーを解決するには  
  
-   `VbStrConv.SimplifiedChinese` または `VbStrConv.TraditionalChinese` のいずれかを削除します。  
  
## 参照  
 <xref:System.Globalization>   
 [NOTINBUILD VbStrConv 列挙型](http://msdn.microsoft.com/ja-jp/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [.NET Framework ベースの国際対応アプリケーションの概要](/visual-studio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)