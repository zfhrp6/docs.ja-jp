---
title: "/removeintchecks | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "removeintchecks"
  - "/removeintchecks"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "removeintchecks compiler option [Visual Basic]"
  - "/removeintchecks compiler option [Visual Basic]"
  - "-removeintchecks compiler option [Visual Basic]"
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /removeintchecks
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

整数演算のオーバーフロー エラー チェックのオンとオフを切り替えます。  
  
## 構文  
  
```  
/removeintchecks[+ | -]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`+`  &#124; `-`|省略可能です。  `/removeintchecks-` オプションはコンパイラはオーバーフロー エラーのすべての整数の計算を確認します。  既定値は `/removeintchecks-` です。<br /><br /> `/removeintchecks` または `/removeintchecks+` を指定すると、エラー チェックは行われず、整数の計算時間が短縮されます。  ただし、エラー チェックを行わないと、データ型の容量がオーバーフローしてもエラーが通知されず、誤った結果が格納される場合があります。|  
  
||  
|-|  
|Visual Studio 統合開発環境で \/removeintchecks を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[詳細\]** をクリックします。<br />4.  **\[整数オーバーフローのチェックを解除\]** ボックスの値を変更します。|  
  
## 使用例  
 `Test.vb` をコンパイルし、整数のオーバーフロー エラー チェックをオフにする場合のコード例を次に示します。  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)