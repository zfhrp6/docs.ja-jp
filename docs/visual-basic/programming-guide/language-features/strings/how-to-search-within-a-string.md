---
title: "How to: Search Within a String (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "strings [Visual Basic], finding"
  - "strings [Visual Basic], searching"
  - "examples [Visual Basic], strings"
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Search Within a String (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

次のコード例では、<xref:System.String> オブジェクト上で <xref:System.String.IndexOf%2A> メソッドを呼び出して、最初に見つかった部分文字列のインデックスを報告します。  
  
## 使用例  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/visualbasic/how-to-search-within-a-s_1.vb)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System> 名前空間を指定する `Imports` ステートメントです。  詳細については、「[Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
## 信頼性の高いプログラミング  
 <xref:System.String.IndexOf%2A> メソッドは、最初に見つかった部分文字列の 1 番目の文字の場所を報告します。  インデックスは、0 から始まります。つまり、文字列の最初の文字はインデックス 0 になります。  
  
 <xref:System.String.IndexOf%2A> が部分文字列を検出できない場合は、\-1 が返されます。  
  
 <xref:System.String.IndexOf%2A> メソッドでは大文字と小文字が区別され、現在のカルチャが使用されます。  
  
 最適なエラー制御としては、文字列の検索を [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) 構造の `Try` ブロックで囲む方法があります。  
  
## 参照  
 <xref:System.String.IndexOf%2A>   
 [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)   
 [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)