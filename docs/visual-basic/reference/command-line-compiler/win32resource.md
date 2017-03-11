---
title: "/win32resource | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/win32resource"
  - "win32resource"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/win32resource compiler option [Visual Basic]"
  - "-win32resource compiler option [Visual Basic]"
  - "win32resource compiler option [Visual Basic]"
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# /win32resource
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Win32 リソース ファイルを出力ファイルに挿入します。  
  
## 構文  
  
```  
/win32resource:filename  
```  
  
## 引数  
 `filename`  
 出力ファイルに加えるリソース ファイルの名前です。  ファイル名に空白が含まれている場合は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 Win32 リソース ファイルは、Microsoft Windows リソース コンパイラ \(RC\) を使って作成できます。  
  
 Win32 リソースには、ヘルプが **\[エクスプローラー\]**でアプリケーションを識別するバージョンやビットマップ \(アイコン\) の情報を含めることができます。  `/win32resource` を指定しない場合、コンパイラはアセンブリのバージョンに基づいてバージョン情報を生成します。  `/win32resource` オプションと `/win32icon` オプションは相互に排他的です。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] リソース ファイルを参照するには「[\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)」、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] リソース ファイルを参照するには「[\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)」を確認してください  
  
> [!NOTE]
>  `/win32resource` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 `In.vb` をコンパイルし、Win32 リソース ファイル `Rf.res` をアタッチする場合のコード例です。  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)