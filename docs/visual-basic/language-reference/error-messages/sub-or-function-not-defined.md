---
title: "Sub or Function not defined (Visual Basic) | Microsoft Docs"
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
  - "vbrID35"
dev_langs: 
  - "VB"
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Sub or Function not defined (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Sub` または `Function` を呼び出すには、事前に定義しておく必要があります。  このエラーでは以下の原因が考えられます。  
  
-   プロシージャ名のスペルが間違っています。  
  
-   **\[参照設定\]** ダイアログ ボックスで参照を明示的に追加していないプロジェクトのプロシージャを呼び出しています。  
  
-   呼び出し元のプロシージャから参照できないプロシージャを指定しました。  
  
-   指定されたライブラリまたはコード リソースにない Windows ダイナミック リンク ライブラリ \(DLL: dynamic\-link library\) ルーチンまたは Macintosh コード リソース ルーチンを宣言しました。  
  
### このエラーを解決するには  
  
1.  プロシージャ名のスペルが正しいことを確認します。  
  
2.  **\[参照設定\]** ダイアログ ボックスで、呼び出そうとしているプロシージャを含むプロジェクトの名前を探します。  名前が表示されていない場合は、**\[参照\]** をクリックして探します。  プロジェクト名の左にあるチェック ボックスをオンにして、**\[OK\]** をクリックします。  
  
3.  ルーチンの名前を確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)