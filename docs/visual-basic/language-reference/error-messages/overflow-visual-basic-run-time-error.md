---
title: "Overflow (Visual Basic Run-Time Error) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrERRID_Overflow"
dev_langs: 
  - "VB"
ms.assetid: c6a23279-3086-412a-bcff-ff8ed2cb8c6f
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Overflow (Visual Basic Run-Time Error)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

代入対象の制限を超える値を代入しようとしたため、オーバーフローが発生しました。  
  
### このエラーを解決するには  
  
1.  代入、計算、およびデータ型変換の結果がその型で使用できる変数の範囲を超えていないかどうかを確認し、超えていた場合は、より広い範囲の値を格納できる型の変数に値を代入します。  
  
2.  プロパティへの代入がプロパティの許容範囲内に収まっていることを確認します。  
  
3.  強制的に整数型に変換される計算で使用されている数が、整数型の範囲を超える結果を持たないことを確認します。  
  
## 参照  
 <xref:System.Int32.MaxValue?displayProperty=fullName>   
 <xref:System.Double.MaxValue?displayProperty=fullName>   
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)