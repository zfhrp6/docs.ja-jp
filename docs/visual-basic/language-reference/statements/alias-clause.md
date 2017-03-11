---
title: "Alias Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Alias"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Alias keyword"
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Alias Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

外部プロシージャが DLL の中では別の名前で宣言されていることを示すキーワードです。  
  
## 解説  
 `Alias` キーワードは、次のコンテキストで使用します。  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 次の例では、`Alias` キーワードを使用して advapi32.dll の関数 \(`GetUserNameA`\) の名前を指定し、この例の中ではこの関数の代わりに `getUserName` を使用しています。  関数 `getUserName` はサブ `getUser` で呼び出され、現在のユーザーの名前を表示します。  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/alias-clause_1.vb)]  
  
## 参照  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)