---
title: "How to: Validate File Names and Paths in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "file names, validating"
  - "strings [Visual Basic], validating"
  - "Boolean values"
  - "paths, validating"
ms.assetid: f673462d-57b7-4120-b13a-6a7592f7ab2c
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Validate File Names and Paths in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

この例では、文字列がファイル名またはパスを表しているかどうかを示す `Boolean` 値を返します。  この検証処理では、ファイル システムで許可されていない文字が名前に含まれているかどうかを調べます。  
  
## 使用例  
 [!code-vb[VbVbcnRegEx#4](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-file-names-and-paths_1.vb)]  
  
 この例では、名前中のコロンの位置が正しくないとか、ディレクトリ名がない、または名前の長さがシステム定義の最大長を超えている、というチェックは行いません。  また、アプリケーションが指定の名前のファイル システム リソースにアクセスするアクセス許可を持っているかどうかのチェックも行いません。  
  
## 参照  
 <xref:System.IO.Path.GetInvalidPathChars%2A>   
 [Validating Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)