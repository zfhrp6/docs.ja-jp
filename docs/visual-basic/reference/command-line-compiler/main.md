---
title: "/main | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "main compiler option [Visual Basic]"
  - "/main compiler option [Visual Basic]"
  - "-main compiler option [Visual Basic]"
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /main
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Sub Main` プロシージャを含むクラスまたはモジュールを指定します。  
  
## 構文  
  
```  
/main:location  
```  
  
## 引数  
 `location`  
 必ず指定します。  プログラムの起動時に呼び出される `Sub Main` プロシージャを含むクラスまたはモジュールの絶対パス名です。  "**\/main:module**" または "**\/main:namespace.module**" の形式で指定します。  
  
## 解説  
 実行可能ファイルまたは Windows 実行可能プログラムを作成するときは、このオプションを使用します。  **\/main** オプションを省略すると、コンパイラは、すべてのパブリック クラスおよびモジュールで有効な共有 `Sub Main` を検索します。  
  
 `Main` プロシージャのさまざまな形式に関しては、「[Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)」を参照してください。  
  
 <xref:System.Windows.Forms.Form> を継承するクラスが `location` に指定され、そのクラスに `Main` プロシージャが存在しなかった場合は、アプリケーションを起動する既定の `Main` プロシージャがコンパイラによって提供されます。  これにより、開発環境で作成したコードをコマンド ラインでコンパイルできるようになります。  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/main_1.vb)]  
  
### Visual Studio 統合開発環境で \/main を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
     詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[アプリケーション\]** タブをクリックします。  
  
3.  **\[アプリケーション フレームワークを有効にする\]** チェック ボックスがオンになっていないことを確認してください。  
  
4.  **\[スタートアップ オブジェクト\]** ボックス内の値を変更します。  
  
## 使用例  
 `T2.vb` および `T3.vb` をコンパイルし、`Sub Main` プロシージャが `Test2` クラスにあることを指定する場合のコード例です。  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/ja-jp/9d030b60-e148-4366-a462-69532f02294c)   
 [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)