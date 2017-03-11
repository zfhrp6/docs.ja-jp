---
title: "Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42104"
  - "BC42104"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42104"
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数 '\<variablename\>' は、値が割り当てられる前に参照によって使用されています。null 参照の例外が実行時に発生する可能性があります。  
  
 アプリケーション コードの実行経路の中に、値を割り当てる前に変数を読み込むことになる経路が少なくとも 1 つあります。  
  
 変数に値が一度も割り当てられない場合は、そのデータ型の既定値が格納されます。  参照データ型の既定値は、[Nothing](../../../visual-basic/language-reference/nothing.md) です。  `Nothing` の値を持つ参照変数を読み込むと、状況によっては <xref:System.NullReferenceException> が発生する可能性があります。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42104  
  
### このエラーを解決するには  
  
-   制御フローのロジックを調べて、変数を読み込むステートメントに制御が渡されるよりも前に、有効な値が格納されることを確認します。  
  
-   変数が常に有効な値を持つための確実な方法の 1 つは、変数を宣言時に初期化することです。  「[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)」の「初期化」を参照してください。  
  
## 参照  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [変数のトラブルシューティング](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)