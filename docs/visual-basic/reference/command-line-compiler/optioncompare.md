---
title: "/optioncompare | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optioncompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "optioncompare compiler option [Visual Basic]"
  - "-optioncompare compiler option [Visual Basic]"
  - "/optioncompare compiler option [Visual Basic]"
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /optioncompare
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列比較の方法を指定します。  
  
## 構文  
  
```  
/optioncompare:{binary | text}  
```  
  
## 解説  
 `/optioncompare` の指定には 2 つの形式があります。バイナリ モードの文字列比較を使用するときは `/optioncompare:binary` を指定し、テキスト モードの文字列比較を使用するときは `/optioncompare:text` を指定します。  既定では、コンパイラは `/optioncompare:binary` を使用します。  
  
 Microsoft Windows では、バイナリの並べ替え順序の判別にコード ページが使用されます。  通常、バイナリの並べ替え順序は次のようになります。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 テキスト ベースの文字列比較は、大文字と小文字を区別しない、システムのロケールで決められたテキストの並べ替え順序に基づいて行われます。  通常、テキストの並べ替え順序は次のようになります。  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### Visual Studio IDE で \/optioncompare を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  **\[Option Compare\]** ボックスの値を変更します。  
  
### プログラムで \/optioncompare を設定するには  
  
-   [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) を参照してください。  
  
## 使用例  
 P`rojFile.vb` をコンパイルし、バイナリ モードで文字列比較を行う場合のコード例です。  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)