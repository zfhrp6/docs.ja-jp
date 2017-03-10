---
title: "Auto (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Auto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Auto keyword, external references"
  - "Declare statement, marshaling strings"
  - "Auto keyword"
  - "Auto keyword, marshaling strings"
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Auto (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic で、宣言されている外部プロシージャの外部名に基づいた .NET Framework の規則に従って文字列をマーシャリングするよう指定します。  
  
 プロジェクト外部で定義されたプロシージャを呼び出す場合、Visual Basic コンパイラは、そのプロシージャを正しく呼び出すために必要な情報にアクセスできません。  この情報には、プロシージャの場所、識別方法、呼び出しシーケンスと戻り値のデータ型、使用する文字列の文字セットが含まれます。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) は、外部プロシージャへの参照を作成し、この必須情報を提供します。  
  
 `Declare` ステートメントの `charsetmodifier` は、外部プロシージャの呼び出し時に文字列をマーシャリングするための文字セットの情報を提供します。  また、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。  `Auto` 修飾子は、Visual Basic が .NET Framework の規則に従って文字列をマーシャリングすること、また、実行時プラットフォームの基本文字セットを確認し、最初の検索が失敗した場合には外部プロシージャ名を変更することを指定します。  詳細については、「[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)」の「文字セット」を参照してください。  
  
 文字セットの修飾子を指定しない場合は `Ansi` が既定値です。  
  
## 解説  
 `Auto` 修飾子は、次の場合に使用できます。  
  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## スマート デバイス開発者のためのメモ  
 このキーワードはサポートされていません。  
  
## 参照  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)