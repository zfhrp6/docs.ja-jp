---
title: "&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc32025"
  - "vbc32025"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32025"
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`#Region` ブロックは、クラス、モジュール、または名前空間のレベルで宣言する必要があります。  折りたたみ可能なコード ブロックは、複数のプロシージャを含めることができますが、プロシージャの内部で開始または終了することはできません。  
  
 **Error ID:** BC32025  
  
### このエラーを解決するには  
  
1.  直前のプロシージャが、`End Function` ステートメントまたは `End Sub` ステートメントによって正しく終了していることを確認します。  
  
2.  `#Region` ディレクティブおよび `#End Region` ディレクティブが同じコード ブロック内にあることを確認します。  
  
## 参照  
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)