---
title: "/nowarn | Microsoft Docs"
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
  - "nowarn compiler option [Visual Basic]"
  - "/nowarn compiler option [Visual Basic]"
  - "-nowarn compiler option [Visual Basic]"
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /nowarn
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

警告を生成するコンパイラの機能が表示されないようにします。  
  
## 構文  
  
```  
/nowarn[:numberList]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`numberList`|省略可能です。  コンパイラが省略する警告の ID 番号をコンマ区切りで指定したリストです。  警告の ID が指定されていない場合、すべての警告が省略されます。|  
  
## 解説  
 `/nowarn` オプションを指定すると、コンパイラは警告を生成しません。  個別の警告を省略するには、`/nowarn` オプションに、コロンに続けて警告の ID を 指定します。  警告番号が複数ある場合は、コンマで区切ります。  
  
 必要なのは、警告 ID の数値を指定することだけです。  たとえば、使用されていないローカル変数の警告である BC42024 を省略するには、`/nowarn:42024` と指定します。  
  
 警告の ID 番号の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」 を参照してください。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/nowarn を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  すべての警告を無効にするには、**\[すべての警告を表示しない\]** チェック ボックスをオンにします。<br />     または<br />     特定の警告を無効にするには、警告の隣にあるドロップダウン リストの **\[なし\]** をクリックします。|  
  
## 使用例  
 `T2.vb` をコンパイルし、警告を表示しないようにする場合のコード例です。  
  
```  
vbc /nowarn t2.vb  
```  
  
## 使用例  
 次のコードでは、`T2.vb` をコンパイルし、使われていないローカル変数の警告 \(42024\) を表示しません。  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)