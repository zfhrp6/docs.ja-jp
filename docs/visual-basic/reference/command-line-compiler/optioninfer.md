---
title: "/optioninfer | Microsoft Docs"
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
  - "/optioninfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optioninfer compiler option [Visual Basic]"
  - "/optioninfer compiler option [Visual Basic]"
  - "optioninfer compiler option [Visual Basic]"
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optioninfer
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

変数宣言でローカル型推論を使用できるようにします。  
  
## 構文  
  
```  
/optioninfer[+ | -]  
```  
  
## 引数  
  
|||  
|-|-|  
|用語|定義|  
|`+`  &#124; `-`|省略可能です。  `/optioninfer+` を指定してローカル型推論を有効にするか、または `/optioninfer-` を指定してローカル型推論をブロックします。  `/optioninfer` オプションは、何も値を指定しない場合、`/optioninfer+` と同じです。  `/optioninfer` スイッチが存在しない場合の既定値も `/optioninfer+` です。  既定値は、Vbc.rsp 応答ファイル内に設定されています。|  
  
> [!NOTE]
>  `/noconfig` オプションを使用すると、vbc.rsp に指定するのではなく、コンパイラの内部既定値を保持できます。  このオプションのコンパイラの既定値は `/optioninfer-` です。  
  
## 解説  
 ソース コード ファイルに [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) が含まれている場合、ステートメントは `/optioninfer` コマンド ライン コンパイラ設定をオーバーライドします。  
  
### Visual Studio IDE で \/optioninfer を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/ja-jp/983f3c18-832f-4666-afec-74b716ff3e0e)」を参照してください。  
  
2.  **\[コンパイル\]** タブで、**\[Option infer\]** ボックスの値を変更します。  
  
## 使用例  
 次のコードは、ローカル型推論を有効にした状態で `test.vb` をコンパイルします。  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](../Topic/Visual%20Basic%20Defaults,%20Projects,%20Options%20Dialog%20Box.md)   
 [\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](../Topic/Compile%20Page,%20Project%20Designer%20\(Visual%20Basic\).md)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [コマンド ラインからのビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)