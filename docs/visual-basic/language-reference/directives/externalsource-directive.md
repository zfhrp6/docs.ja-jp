---
title: "#ExternalSource Directive | Microsoft Docs"
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
  - "#Externalsource"
  - "#ExternalSource"
  - "vb.ExternalSource"
  - "Externalsource"
  - "vb.#ExternalSource"
  - "ExternalSource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ExternalSource directive (#ExternalSource)"
  - "#ExternalSource directive"
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: 160
caps.handback.revision: 160
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #ExternalSource Directive
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ソース コードの特定行とソース外部のテキストと間の対応付けを指定します。  
  
## 構文  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## 指定項目  
 `StringLiteral`  
 外部ソースのパス。  
  
 `IntLiteral`  
 外部ソースの最初の行の行番号。  
  
 `LogicalLine`  
 外部ソースでエラーが発生する行。  
  
 `#End ExternalSource`  
 `#ExternalSource` ブロックを終了します。  
  
## 解説  
 このディレクティブは、コンパイラとデバッガーだけに使用されます。  
  
 ソース ファイルには、外部ソース ディレクティブを含めることができます。ソース ディレクティブは、ソース ファイル内のコードの特定行と、.aspx ファイルなど、ソース外部のテキストとの対応付けを指定します。  指定されたソース コードでコンパイル中にエラーが発生した場合、エラーは外部ソースからのものであると示されます。  
  
 外部ソース ディレクティブは、コンパイルには影響を与えず、入れ子になることもありません。  これらのディレクティブは、アプリケーションの内部で使用するためだけに用意されています。  
  
## 参照  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)