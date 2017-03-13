---
title: "/netcf | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/netcf"
  - "netcf"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-netcf compiler option [Visual Basic]"
  - "netcf compiler option [Visual Basic]"
  - "/netcf compiler option [Visual Basic]"
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /netcf
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] を対象とするようにコンパイラを設定します。  
  
## 構文  
  
```  
/netcf  
```  
  
## 解説  
 `/netcf` オプションでは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] コンパイラが完全な [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] ではなく [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] を対象にします。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] だけで使用できる言語機能は無効になります。  
  
 `/netcf` オプションは [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md) と組み合わせて使用するよう設計されています。  `/netcf` によって無効になる言語機能は、`/sdkpath` の対象となるファイルで使用できる言語機能と同じです。  
  
> [!NOTE]
>  `/netcf` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  `/netcf` オプションは、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] デバイス プロジェクトが読み込まれている場合に設定されます。  
  
 `/netcf` オプションは、次の言語機能を変更します。  
  
-   プログラムの実行を終了する [End \<keyword\> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) キーワードが無効になります。  次のプログラムは、`/netcf` なしでコンパイルおよび実行可能ですが、`/netcf` を指定するとコンパイル時に失敗します。  
  
     [!code-vb[VbVbalrCompiler#34](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_1.vb)]  
  
-   すべての形式の遅延バインディング。  認識されている遅延バインディングのシナリオと同じ状況になると、コンパイル時エラーが発生します。  次のプログラムは、`/netcf` なしでコンパイルおよび実行可能ですが、`/netcf` を指定するとコンパイル時に失敗します。  
  
     [!code-vb[VbVbalrCompiler#35](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_2.vb)]  
  
-   [Auto](../../../visual-basic/language-reference/modifiers/auto.md)、[Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)、[Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) 修飾子が無効になります。  [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) ステートメントの構文も `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` に変更されます。  `/netcf` によるコンパイルへの影響を、次のコードで示します。  
  
     [!code-vb[VbVbalrCompiler#36](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/netcf_3.vb)]  
  
-   [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で削除された Visual Basic 6.0 のキーワードを使用すると、`/netcf` を使用した場合に別のエラーが発生します。  これにより、次のキーワードに対するエラー メッセージが影響を受けます。  
  
    -   `Open`  
  
    -   `Close`  
  
    -   `Put`  
  
    -   `Print`  
  
    -   `Write`  
  
    -   `Input`  
  
    -   `Lock`  
  
    -   `Unlock`  
  
    -   `Seek`  
  
    -   `Width`  
  
    -   `Name`  
  
    -   `FreeFile`  
  
    -   `EOF`  
  
    -   `Loc`  
  
    -   `LOF`  
  
    -   `Line`  
  
## 使用例  
 次のコードは、C ドライブ上の [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] の既定のインストール ディレクトリにある Mscorlib.dll のバージョンと Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] で `Myfile.vb` をコンパイルします。  通常は、最新のバージョンの [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] を使用します。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)