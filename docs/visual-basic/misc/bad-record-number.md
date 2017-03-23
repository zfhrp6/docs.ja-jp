---
title: "レコード番号が正しくありません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID63"
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# レコード番号が正しくありません
`a FileGet`、`FilePut`、`FileGetObject`、または `FilePutObject` ステートメント内のレコード番号が 0 以下です。  
  
### このエラーを解決するには  
  
1.  レコード番号の生成で使用される計算を確認します。 レコード番号が含まれている変数、またはレコード番号の計算で使用される変数のスペルを確認します。 モジュールで `Option Explicit On` を使用しない限り、スペル ミスの変数名は暗黙的に宣言され、0 に初期化されます。  
  
## 参照  
 [Option Explicit Statement](../../visual-basic/language-reference/statements/option-explicit-statement.md)