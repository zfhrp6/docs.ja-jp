---
title: "/define (Visual Basic) | Microsoft Docs"
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
  - "-d compiler option [Visual Basic]"
  - "/d compiler option [Visual Basic]"
  - "-define compiler option [Visual Basic]"
  - "d compiler option [Visual Basic]"
  - "/define compiler option [Visual Basic]"
  - "define compiler option [Visual Basic]"
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /define (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

条件付きコンパイル定数を定義します。  
  
## 構文  
  
```  
/define:["]symbol[=value][,symbol[=value]]["] ' -or- /d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## 引数  
  
|||  
|-|-|  
|用語|定義|  
|`symbol`|必ず指定します。  定義する記号。|  
|`value`|省略可能です。  `symbol` に代入する値。  `value` が文字列の場合、これは引用符ではなく、バックスラッシュ\/引用符のシーケンス \(\\"\) で囲む必要があります。  値が指定されていない場合は、True として処理されます。|  
  
## 解説  
 `/define` オプションは、ソース ファイル内で `#Const` プリプロセッサ ディレクティブを使用するのと同じ効果を持ちます。ただし、`/define` で定義された定数は public で、プロジェクト内のすべてのファイルに適用されます。  
  
 このオプションで作成される記号を `#If`...`Then`...`#Else` ディレクティブで使用すると、ソース ファイルを条件付きでコンパイルできます。  
  
 `/d` は `/define` の省略形です。  
  
 記号の定義をコンマで区切ると、`/define` を使用して複数の記号を定義できます。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/define を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[詳細\]** をクリックします。<br />4.  **\[カスタム定数\]** ボックス内の値を変更します。|  
  
## 使用例  
 2 つの条件付きコンパイル定数を定義して使用する場合のコード例を次に示します。  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/visualbasic/define_1.vb)]  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)