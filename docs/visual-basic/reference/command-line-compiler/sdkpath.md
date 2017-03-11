---
title: "/sdkpath | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "sdkpath"
  - "/sdkpath"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-sdkpath compiler option [Visual Basic]"
  - "/sdkpath compiler option [Visual Basic]"
  - "sdkpath compiler option [Visual Basic]"
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /sdkpath
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Mscorlib.dll と Microsoft.VisualBasic.dll の場所を指定します。  
  
## 構文  
  
```  
/sdkpath:path  
```  
  
## 引数  
 `path`  
 Mscorlib.dll および Microsoft.VisualBasic.dll のコンパイルに使用するバージョンを格納するディレクトリ。  このパスは、読み込まれるまで検査されません。  ディレクトリ名に空白が含まれている場合は、文字列を二重引用符 \(" "\) で囲みます。  
  
## 解説  
 このオプションを指定すると、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のコンパイラは既定の場所以外から Mscorlib.dll および Microsoft.VisualBasic.dll の各ファイルを読み込みます。  `/sdkpath`  オプションは [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md) と組み合わせて使用するよう設計されています。  [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] は、これらのサポート ライブラリの別バージョンを使用して、デバイスで見つからない型や言語機能を使用することを回避します。  
  
> [!NOTE]
>  `/sdkpath` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  `/sdkpath` オプションは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] デバイス プロジェクトが読み込まれている場合に設定されます。  
  
 `/vbruntime` コンパイラ オプションを使用すると、コンパイラが Visual Basic ランタイム ライブラリを参照しないでコンパイルを実行するように指定できます。  詳細については、「[\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)」を参照してください。  
  
## 使用例  
 次のコードは、C ドライブ上の [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] の既定のインストール ディレクトリにある Mscorlib.dll のバージョンと Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] で `Myfile.vb` をコンパイルします。  通常は、最新のバージョンの [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] を使用します。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)   
 [\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)