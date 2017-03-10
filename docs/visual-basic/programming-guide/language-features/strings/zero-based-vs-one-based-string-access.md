---
title: "Zero-based vs. One-based String Access in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], indexing"
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Zero-based vs. One-based String Access in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] と [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] における、文字列内の文字へのアクセス方法の違いについて説明します。  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] では常に、文字列内の文字へのアクセスに 0 から始まるインデックス番号が使用されます。これに対して [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、関数によってインデックス番号が 0 から始まる場合と 1 から始まる場合があります。  
  
## 1 から始まるインデックス番号  
 インデックス番号が 1 から始まる [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の関数の例に、`Mid` 関数があります。  この関数の引数では、文字列内の部分文字列の開始位置を 1 から始まるインデックス番号で示します。  一方、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] の <xref:System.String.Substring%2A?displayProperty=fullName> メソッドの引数では、同じ開始位置を 0 から始まるインデックス番号で示します。  つまり、文字列 "ABCDE" の各文字の番号は、`Mid` 関数では 1、2、3、4、5 になるのに対し、<xref:System.String.Substring%2A?displayProperty=fullName> メソッドでは 0、1、2、3、4 になります。  
  
## 0 から始まるインデックス番号  
 インデックス番号が 0 から始まる [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の関数の例に、`Split` 関数があります。  この関数は文字列を分割し、部分文字列を格納した配列を返します。  [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] の <xref:System.String.Split%2A?displayProperty=fullName> メソッドも文字列を分割し、部分文字列を格納した配列を返します。  `Split` 関数と <xref:System.String.Split%2A> メソッドは [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] の配列を返すため、インデックス番号はどちらも 0 から始まる必要があります。  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:System.String.Substring%2A>   
 <xref:System.String.Split%2A>   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)