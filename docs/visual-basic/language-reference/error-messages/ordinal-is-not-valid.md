---
title: "Ordinal is not valid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID452"
dev_langs: 
  - "VB"
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Ordinal is not valid
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ダイナミック リンク ライブラリ \(DLL: dynamic\-link library\) の呼び出しで、`#num` 構文を使用して、プロシージャ名の代わりに数値を使用するように指定されています。  このエラーでは以下の原因が考えられます。  
  
-   `#num` 式の序数への変換に失敗しました。  
  
-   指定した `#num` は、DLL 内の関数を指定しません。  
  
-   タイプ ライブラリに無効な宣言があるため、無効な除数が内部で使用されています。  
  
### このエラーを解決するには  
  
1.  式が有効な数値を表していることを確認するか、プロシージャを名前で呼び出します。  
  
2.  `#num` が DLL 内の有効な関数を指定していることを確認します。  
  
3.  コードをコメント アウトすることによって、問題を起こしているプロシージャ呼び出しを特定します。  プロシージャの `Declare` ステートメントを作成し、問題をタイプ ライブラリ販売元に報告します。  
  
## 参照  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)