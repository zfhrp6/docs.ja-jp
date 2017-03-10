---
title: "/optionstrict | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optionstrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optionstrict compiler option [Visual Basic]"
  - "optionstrict compiler option [Visual Basic]"
  - "/optionstrict compiler option [Visual Basic]"
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# /optionstrict
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

暗黙の型変換を制限するための、厳密な型の意味を適用します。  
  
## 構文  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## 引数  
 `+` &#124; `-`  
 省略可能です。  `/optionstrict+` を指定すると、暗黙の型変換が制限されます。  このオプションの既定値は `/optionstrict-` です。  `/optionstrict+` オプションは、`/optionstrict` と同じ動作になります。  寛容な型指定規則では、どちらも使用できます。  
  
 `custom`  
 必ず指定します。  厳密な言語規則が守られていない場合に警告します。  
  
## 解説  
 `/optionstrict+` を指定すると、拡張型変換だけが暗黙のうちに行われます。  10 進型 \(`Decimal`\) のオブジェクトを整数型 \(Integer\) のオブジェクトに代入するなど、縮小による暗黙の型変換はエラーとして報告されます。  
  
 暗黙の縮小変換で警告を生成するには、`/optionstrict:custom` を使用します。  特定の警告を無視するには `/nowarn:numberlist`、特定の警告をエラーとして扱うようにするには `/warnaserror:numberlist` を使用します。  
  
### Visual Studio IDE で \/optionstrict を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  **\[Option Strict\]** ボックス内の値を変更します。  
  
### プログラムで \/optionstrict を設定するには  
  
-   [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) を参照してください。  
  
## 使用例  
 厳密な型指定規則を使用して `Test.vb` をコンパイルする場合のコード例です。  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [\/warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)