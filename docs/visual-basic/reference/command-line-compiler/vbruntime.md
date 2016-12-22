---
title: "/vbruntime | Microsoft Docs"
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
  - "vbruntime"
  - "/vbruntime"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "vbruntime compiler option [Visual Basic]"
  - "-vbruntime compiler option [Visual Basic]"
  - "/vbruntime compiler option [Visual Basic]"
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /vbruntime
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コンパイラが、Visual Basic ランタイム ライブラリを参照しないで、または特定のランタイム ライブラリを参照してコンパイルを実行するよう指定します。  
  
## 構文  
  
```  
/vbruntime:{ - | + | * | path }  
```  
  
## 引数  
 \-  
 Visual Basic ランタイム ライブラリを参照しないでコンパイルします。  
  
 \+  
 既定の Visual Basic ランタイム ライブラリを参照してコンパイルします。  
  
 \*  
 Visual Basic ランタイム ライブラリを参照しないでコンパイルし、Visual Basic ランタイム ライブラリのコア機能をアセンブリに埋め込みます。  
  
 `path`  
 指定したライブラリ \(DLL\) を参照してコンパイルします。  
  
## 解説  
 `/vbruntime` コンパイラ オプションを使用すると、コンパイラが Visual Basic ランタイム ライブラリを参照しないでコンパイルを実行するように指定できます。  Visual Basic ランタイム ライブラリを参照しないでコンパイルする場合、Visual Basic のランタイム ヘルパーへの呼び出しを生成するコード構成要素または言語構成要素にエラーや警告がログ記録されます   \(*Visual Basic のランタイム ヘルパー*は、特定の言語セマンティクスの実行時に呼び出される Microsoft.VisualBasic.dll で定義される関数です\)。  
  
 `/vbruntime+` オプションを使用すると、`/vbruntime` スイッチを指定しない場合と同じ動作になります。  `/vbruntime+` オプションにより、前の `/vbruntime` スイッチをオーバーライドできます。  
  
 `My` の型のほとんどのオブジェクトは `vbruntime:``/vbruntime-` か`path` オプションを使用すると、は使用できません。  
  
## Visual Basic ランタイムのコア機能の埋め込み  
 `/vbruntime*` オプションを使用すると、ランタイム ライブラリを参照しないでコンパイルできます。  代わりに、Visual Basic ランタイム ライブラリのコア機能がユーザー アセンブリに埋め込まれます。  Visual Basic ランタイムが含まれていないプラットフォームでアプリケーションを実行このオプションを使用できます。  
  
 次のランタイム メンバーが埋め込まれます。  
  
-   <xref:Microsoft.VisualBasic.CompilerServices.Conversions> クラス  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> メソッド  
  
-   <xref:Microsoft.VisualBasic.Constants.vbBack> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCr> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbCrLf> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbFormFeed> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbLf> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNewLine> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullChar> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbNullString> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbTab> 定数  
  
-   <xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 定数  
  
-   `My` の型のオブジェクト  
  
 `/vbruntime*` オプションを使用してコンパイルするときに、コア機能と共に埋め込まれない Visual Basic ランタイム ライブラリのメンバーをコードで参照している場合、コンパイラによって、メンバーが使用できないことを示すエラーが返されます。  
  
## 指定したライブラリの参照  
 `path` 引数を使用すると、既定の Visual Basic ランタイム ライブラリの代わりにカスタム ランタイム ライブラリへの参照を使用してコンパイルできます。  
  
 `path` 引数の値が DLL の絶対パスの場合、コンパイラはそのファイルをランタイム ライブラリとして使用します。  `path` 引数の値が DLL の絶対パスではない場合、Visual Basic コンパイラは指定された DLL をまず現在のフォルダーで検索します。  次に、[\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) コンパイラ オプションを使用して指定したパスを検索します。  `/sdkpath` コンパイラ オプションを使用しない場合、コンパイラは指定した DLL を .NET Framework フォルダー \(`%systemroot%\Microsoft.NET\Framework\versionNumber`\) で検索します。  
  
## 使用例  
 `/vbruntime` オプションを使用し、カスタム ライブラリを参照してコンパイルする方法を次の例に示します。  
  
```  
vbc /vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## 参照  
 [Visual Basic Core – New compilation mode in Visual Studio 2010 SP1 \(VB コア \- Visual Studio 2010 SP1 の新しいコンパイル モード\)](http://blogs.msdn.com/b/vbteam/archive/2011/01/10/vb-core-new-compilation-mode-in-visual-studio-2010-sp1.aspx)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)