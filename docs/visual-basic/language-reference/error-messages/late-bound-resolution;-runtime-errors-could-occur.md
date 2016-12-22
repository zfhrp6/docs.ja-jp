---
title: "Late bound resolution; runtime errors could occur | Microsoft Docs"
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
  - "vbc42017"
  - "BC42017"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42017"
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Late bound resolution; runtime errors could occur
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)に宣言された変数に、オブジェクトが割り当てられています。  
  
 変数を `Object` 型で宣言した場合、コンパイラは*遅延バインディング*を実行する必要がありますが、これによって実行時に余分な処理が発生します。  また、アプリケーションがランタイム エラーを起こす可能性もあります。  たとえば、<xref:System.Windows.Forms.Form> を `Object` 変数に割り当ててから <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> プロパティにアクセスしようとすると、<xref:System.Windows.Forms.Form> クラスが `NameTable` プロパティを公開していないので、ランタイムによって <xref:System.MemberAccessException> がスローされます。  
  
 変数を特定の型に宣言すると、コンパイラはコンパイル時に*事前バインディング*を実行できます。  これによって、パフォーマンスが向上し、特定の型のメンバーへのアクセスの制御が可能になります。また、コードも読みやすくなります。  
  
 既定では、このメッセージは警告です。  警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic) を参照してください。  
  
 **Error ID:** BC42017  
  
### このエラーを解決するには  
  
-   可能であれば、変数を特定の型に宣言してください。  
  
## 参照  
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)