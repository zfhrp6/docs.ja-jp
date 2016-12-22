---
title: "Unicode (Visual Basic) | Microsoft Docs"
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
  - "vb.Unicode"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Unicode, external references"
  - "Declare statement, marshaling strings"
  - "Unicode keyword"
  - "Unicode, marshaling strings"
ms.assetid: 0021d5ff-3209-444e-8497-420f3e6ee075
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unicode (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

宣言される外部プロシージャの名前に関係なく、すべての文字列を Unicode 値にマーシャリングするように指定します。  
  
 プロジェクト外部で定義されたプロシージャを呼び出す場合、Visual Basic コンパイラは、そのプロシージャを正しく呼び出すために必要な情報にアクセスできません。  この情報には、プロシージャの場所、識別方法、呼び出しシーケンスと戻り値のデータ型、使用する文字列の文字セットが含まれます。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) は、外部プロシージャへの参照を作成し、この必須情報を提供します。  
  
 `Declare` ステートメントの `charsetmodifier` 部は、外部プロシージャの呼び出し時に文字列をマーシャリングするための文字セットの情報を提供します。  また、Visual Basic が外部ファイルで外部プロシージャ名を検索する方法にも影響します。  `Unicode` 修飾子を指定すると、Visual Basic はすべての文字列を Unicode 値にマーシャリングし、プロシージャの検索中にプロシージャ名を変更しなくなります。  
  
 文字セットの修飾子を指定しない場合は `Ansi` が既定値です。  
  
## 解説  
 `Unicode` 修飾子は次の構文で使用します。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## スマート デバイス開発者のためのメモ  
 このキーワードはサポートされていません。  
  
## 参照  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)   
 [Auto](../../../visual-basic/language-reference/modifiers/auto.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)