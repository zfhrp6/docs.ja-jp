---
title: "/imports (Visual Basic) | Microsoft Docs"
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
  - "/imports compiler option [Visual Basic]"
  - "imports compiler option [Visual Basic]"
  - "-imports compiler option [Visual Basic]"
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /imports (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

指定のアセンブリから名前空間をインポートします。  
  
## 構文  
  
```  
/imports:namespaceList  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`namespaceList`|必ず指定します。  インポートする名前空間のコンマで区切られたリストです。|  
  
## 解説  
 `/imports` オプションを使用すると、現在のソース ファイルのセット内または参照先アセンブリで定義されたすべての名前空間がインポートされます。  
  
 `/imports` で指定する名前空間のメンバーは、コンパイルのすべてのソース コード ファイルで使用できます。  1 つのソース コード ファイルで名前空間を使用するには、[Imports Statement \(.NET Namespace and Type\)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) を使用します。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/imports を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[参照設定\]** タブをクリックします。<br />3.  **\[ユーザー インポートの追加\]** ボタンの横に名前空間の名前を入力します。<br />4.  **\[ユーザー インポートの追加\]** ボタンをクリックします。|  
  
## 使用例  
 `/imports:system` を指定するとコンパイルされる場合のコード例を次に示します。  
  
 [!code-vb[VbVbalrCompiler#21](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/imports_1.vb)]  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)