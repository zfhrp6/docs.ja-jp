---
title: "Bad record length | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID59"
dev_langs: 
  - "VB"
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Bad record length
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このエラーでは以下の原因が考えられます。  
  
-   `FileGet`、`FileGetObject`、`FilePut`、または `FilePutObject` の各ステートメントで指定されたレコード変数の長さと、対応する `FileOpen` ステートメントで指定された長さが異なります。  
  
-   `FilePut` ステートメントまたは `FilePutObject` ステートメント内の変数が、可変長文字列であるか、可変長文字列を含んでいます。  
  
-   `FilePut` ステートメントまたは `FilePutObject` ステートメント内の変数が、`Variant` 型であるか、この型を含んでいます。  
  
### このエラーを解決するには  
  
1.  レコード変数の型を定義するユーザー定義型の固定長変数のサイズ合計が、`FileOpen` ステートメントの `Len` 句で指定された値と同じであることを確認します。  
  
2.  `FilePut` ステートメントまたは `FilePutObject` ステートメント内の変数が可変長の文字列であるか、可変長文字列を含む場合は、その可変長文字列の長さが、`FileOpen` ステートメントの `Len` 句で指定されたレコード長よりも 2 文字以上短いことを確認します。  
  
3.  `FilePut` ステートメントまたは `FilePutObject` ステートメント内の変数が `Variant` 型であるか、この型を含む場合は、その可変長文字列の長さが、`FileOpen` ステートメントの `Len` 句で指定されたレコード長よりも 4 バイト以上短いことを確認します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>   
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>