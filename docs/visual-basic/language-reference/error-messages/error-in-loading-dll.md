---
title: "Error in loading DLL (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID48"
dev_langs: 
  - "VB"
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Error in loading DLL (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ダイナミック リンク ライブラリ \(DLL: dynamic\-link library\) は、`Declare` ステートメントの `Lib` 句で指定されているライブラリです。  このエラーでは以下の原因が考えられます。  
  
-   ファイルが DLL 実行可能ではありません。  
  
-   ファイルが Microsoft Windows DLL ではありません。  
  
-   DLL が、存在しない別の DLL を参照しています。  
  
-   DLL または参照先の DLL が、パスで指定されたディレクトリにありません。  
  
### このエラーを解決するには  
  
-   ファイルがソース テキスト ファイルであり、DLL が実行可能でない場合は、ファイルをコンパイルし、DLL 実行可能形式にリンクする必要があります。  
  
-   ファイルが Microsoft Windows DLL でない場合は、Microsoft Windows と等価の DLL を入手します。  
  
-   DLL が、存在しない別の DLL を参照している場合は、参照される DLL を入手し、使用できる状態にします。  
  
-   DLL または参照先の DLL がパスで指定されたディレクトリにない場合は、参照先のディレクトリに DLL を移動します。  
  
## 参照  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)