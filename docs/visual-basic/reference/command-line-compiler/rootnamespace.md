---
title: "/rootnamespace | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rootnamespace"
  - "rootnamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/rootnamespace compiler option [Visual Basic]"
  - "-rootnamespace compiler option [Visual Basic]"
  - "rootnamespace compiler option [Visual Basic]"
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /rootnamespace
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

すべての型宣言の名前空間を指定します。  
  
## 構文  
  
```  
/rootnamespace:namespace  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`namespace`|現在のプロジェクトのすべての型宣言を含める名前空間の名前。|  
  
## 解説  
 Visual Studio 実行可能ファイル \(Devenv.exe\) を使用して Visual Studio 統合開発環境で作成されたプロジェクトをコンパイルする場合、`/rootnamespace` を使用して <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> プロパティの値を指定します。  詳細については、「[Devenv コマンド ライン スイッチ](/visual-studio/ide/reference/devenv-command-line-switches)」を参照してください。  
  
 出力ファイルの名前空間の名前を確認するには、共通言語ランタイムの MSIL 逆アセンブラー \(I`ldasm.exe`\) を使用します。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/rootnamespace を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[アプリケーション\]** タブをクリックします。<br />3.  **\[ルート名前空間\]** ボックス内の値を変更します。|  
  
## 使用例  
 `In.vb` をコンパイルし、すべての型宣言を名前空間 `mynamespace` に含める場合のコード例です。  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe \(IL 逆アセンブラー\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)