---
title: "Alias Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.Alias"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Alias keyword"
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Alias Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

外部プロシージャが DLL の中では別の名前で宣言されていることを示すキーワードです。  
  
## 解説  
 `Alias` キーワードは、次のコンテキストで使用します。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 次の例では、`Alias` キーワードを使用して advapi32.dll の関数 \(`GetUserNameA`\) の名前を指定し、この例の中ではこの関数の代わりに `getUserName` を使用しています。  関数 `getUserName` はサブ `getUser` で呼び出され、現在のユーザーの名前を表示します。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## 参照  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)