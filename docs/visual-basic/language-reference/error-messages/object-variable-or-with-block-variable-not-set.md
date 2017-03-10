---
title: "Object variable or With block variable not set | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID91"
dev_langs: 
  - "VB"
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# Object variable or With block variable not set
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

無効な変数が参照されています。  オブジェクト変数を作成するには、オブジェクト変数を宣言し、`Set` ステートメントを使用して有効な参照をオブジェクト変数に代入します。  同様に、 `With...End With` ブロックは `With` ステートメントのエントリ ポイントを実行して初期化する必要があります。  
  
### このエラーを解決するには  
  
1.  オブジェクト変数が有効なオブジェクトを参照していることを確認し、問題があればオブジェクトに対する参照を指定し直します。  
  
2.  `Nothing` に設定されたオブジェクト変数を使用していないことを確認します。  
  
3.  オブジェクトが記述されているオブジェクト ライブラリが \[`Add References`\] ダイアログ ボックスで選択されていることを確認します。  
  
4.  `With` ブロックが `With` ステートメントのエントリ ポイントを実行して初期化されていることを確認します。  
  
## 参照  
 [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md)