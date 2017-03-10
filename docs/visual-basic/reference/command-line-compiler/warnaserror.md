---
title: "/warnaserror (Visual Basic) | Microsoft Docs"
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
  - "warnaserror compiler option [Visual Basic]"
  - "/warnaserror compiler option [Visual Basic]"
  - "-warnaserror compiler option [Visual Basic]"
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /warnaserror (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラは、最初に発生した警告をエラーとして扱います。  
  
## 構文  
  
```  
/warnaserror[+ | -][:numberList]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|\+ &#124; \-|省略可能です。  既定では `/warnaserror-` が有効になっていて、警告が通知されても出力ファイルは生成されます。  `/warnaserror`  オプションは `/warnaserror+` と同じ機能を持ち、警告をエラーとして扱います。|  
|`numberList`|省略可能です。  `/warnaserror` オプションを適用する警告の ID 番号を、コンマで区切って指定したリストです。  警告 ID の指定を省略すると、`/warnaserror` オプションはすべての警告に適用されます。|  
  
## 解説  
 `/warnaserror` オプションは、すべての警告をエラーとして扱います。  通常は警告として通知されるメッセージが、エラーとして通知されるようになります。  同じ警告が 2 回以上通知された場合、2 回目以降は警告として報告されます。  
  
 既定では `/warnaserror-` が有効になっており、警告のメッセージが表示されるだけです。  `/warnaserror`  オプションは `/warnaserror+` と同じ機能を持ち、警告をエラーとして扱います。  
  
 エラーと見なす警告の番号をコンマ区切りで指定することにより、一部の特定の警告だけをエラーとして扱うこともできます。  
  
> [!NOTE]
>  `/warnaserror` オプションを使って、警告の表示方法を制御することはできません。  警告を出さないようにするには、[\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) オプションを使用します。  
  
||  
|-|  
|\/warnaserror を設定して、Visual Studio IDE のすべての警告をエラーとして扱うには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[すべての警告を表示しない\]** チェック ボックスがオフになっていることを確認します。<br />4.  **\[すべての警告をエラーとして扱う\]** チェック ボックスをオンにします。|  
  
||  
|-|  
|\/warnaserror を設定して、Visual Studio IDE の特定の警告をエラーとして扱うには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[すべての警告を表示しない\]** チェック ボックスがオフになっていることを確認します。<br />4.  **\[すべての警告をエラーとして扱う\]** チェック ボックスがオフになっていることを確認します。<br />5.  **\[通知\]** 列の、エラーとして扱う警告に隣接した **\[エラー\]** を選択します。|  
  
## 使用例  
 `In.vb` をコンパイルし、すべての警告の初回発生分をエラーとして表示するコード例は次のようになります。  
  
```  
vbc /warnaserror in.vb  
```  
  
## 使用例  
 `T2.vb` をコンパイルし、未使用のローカル変数に対する警告 \(42024\) だけをエラーとして扱うコードは次のようになります。  
  
```  
vbc /warnaserror:42024 t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)