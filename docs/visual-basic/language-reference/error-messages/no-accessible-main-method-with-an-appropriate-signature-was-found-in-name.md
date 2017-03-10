---
title: "No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30737"
  - "vbc30737"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30737"
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コマンド ライン アプリケーションには、`Sub Main` を定義する必要があります。  `Main` は、クラス内で定義される場合には `Public Shared` として、モジュール内で定義される場合には `Public` として宣言される必要があります。  
  
 `Main` の詳細については、「[NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)」を参照してください。  
  
 **Error ID:** BC30737  
  
### このエラーを解決するには  
  
-   プロジェクトに `Public Sub Main` プロシージャを定義します。  クラス内で定義する場合にだけ `Shared` として宣言します。  
  
## 参照  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)