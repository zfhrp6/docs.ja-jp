---
title: "Bad file name or number | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID52"
dev_langs: 
  - "VB"
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Bad file name or number
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定されたファイルにアクセスしようとしたときにエラーが発生しました。  このエラーでは以下の原因が考えられます。  
  
-   `FileOpen` ステートメントで指定されていない名前または番号を持つファイルを参照しているか、`FileOpen`ステートメントで指定されたファイルが後で閉じられました。  
  
-   ステートメントが、範囲外の番号を持つファイルを参照しています。  
  
-   ステートメントが、無効な名前または番号を持つファイルを参照しています。  
  
### このエラーを解決するには  
  
1.  ファイル名が `FileOpen` ステートメントで指定されていることを確認します。  `FileClose` ステートメントを引数なしで呼び出した場合は、すべての開いているファイルを誤って閉じてしまった可能性があります。  
  
2.  コードがファイル番号をアルゴリズムによって生成している場合は、番号が有効であることを確認します。  
  
3.  ファイル名がオペレーティング システムの規約に準拠していることを確認します。  
  
## 参照  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)