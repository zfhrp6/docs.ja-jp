---
title: "/optimize | Microsoft Docs"
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
  - "optimize compiler option [Visual Basic]"
  - "/optimize compiler option [Visual Basic]"
  - "optimization, enabling"
  - "-optimize compiler option [Visual Basic]"
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /optimize
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラの最適化を有効または無効にします。  
  
## 構文  
  
```  
/optimize[ + | - ]  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`+`  &#124; `-`|省略可能です。  `/optimize-` オプションを指定すると、コンパイラの最適化は無効になります。  `/optimize+` オプションを指定すると、最適化は有効になります。  既定では、最適化は無効です。|  
  
## 解説  
 コンパイラを最適化すると、出力ファイルのサイズが小さくなり、動作が速くなり、処理の効率が向上します。  ただし、最適化を行うと出力ファイルにおいてコードの配置が変更されるので、`/optimize+` を指定するとデバッグは困難になります。  
  
 `/target:module` でアセンブリに生成されたすべてのモジュールは、アセンブリと同じ `/optimize` の設定を使用する必要があります。  詳細については、「[\/target](../../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。  
  
 `/optimize` オプションと `/debug` オプションを組み合わせることができます。  
  
||  
|-|  
|Visual Studio 統合開発環境で \/optimize を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。<br />     詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[詳細\]** をクリックします。<br />4.  **\[最適化を有効にする\]** チェック ボックスを変更します。|  
  
## 使用例  
 `T2.vb` をコンパイルし、コンパイラの最適化を有効にする場合のコード例です。  
  
```  
vbc t2.vb /optimize  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)