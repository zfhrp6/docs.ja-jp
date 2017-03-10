---
title: "Type &#39;&lt;typename&gt;&#39; has no constructors | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30251"
  - "vbc30251"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30251"
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Type &#39;&lt;typename&gt;&#39; has no constructors
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型が `Sub New()` の呼び出しをサポートしません。  コンパイラまたはバイナリ ファイルが破損していることが原因の 1 つとして考えられます。  
  
 **Error ID:** BC30251  
  
### このエラーを解決するには  
  
1.  型が別のプロジェクトまたは参照ファイル内にある場合は、プロジェクトまたはファイルを再インストールします。  
  
2.  型が同じプロジェクト内にある場合は、型を含むアセンブリを再コンパイルします。  
  
3.  エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラを再インストールします。  
  
4.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
## 参照  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [ご意見](/visual-studio/ide/talk-to-us)