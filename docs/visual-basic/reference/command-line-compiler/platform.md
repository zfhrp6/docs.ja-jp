---
title: "/platform (Visual Basic) | Microsoft Docs"
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
  - "platform compiler option [Visual Basic]"
  - "/platform compiler option [Visual Basic]"
  - "-platform compiler option [Visual Basic]"
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: 34
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 34
---
# /platform (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

出力ファイルをどのプラットフォーム用の共通言語ランタイム \(CLR\) で実行するかを指定します。  
  
## 構文  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## 引数  
  
|||  
|-|-|  
|用語|定義|  
|`x86`|32 ビット x86 互換 CLR で実行されるように、アセンブリをコンパイルします。|  
|`x64`|AMD64 または EM64T 命令セットをサポートするコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`Itanium`|Itanium プロセッサ搭載のコンピューター上の 64 ビット CLR で実行されるように、アセンブリをコンパイルします。|  
|`arm`|ARM \(アドバンスト RISC マシン\) プロセッサ搭載のコンピューター上で実行されるように、アセンブリをコンパイルします。|  
|`anycpu`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。  アプリケーションは、Windows の 32 ビット バージョンでは 32 ビット アプリケーションとして、Windows の 64 ビット バージョンでは 64 ビット アプリケーションとして実行されます。  このフラグが既定値です。|  
|`anycpu32bitpreferred`|任意のプラットフォーム上で実行されるように、アセンブリをコンパイルします。  アプリケーションは、Windows の 32 ビット バージョンおよび 64 ビット バージョンの両方で、 32 ビット アプリケーションとして実行されます。  このフラグは、実行可能ファイル \(.EXE\) に対してのみ有効であり、[!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net-v45-md.md)] を要求します。|  
  
## 解説  
 出力ファイルの対象となるプロセッサの種類を指定するには、`/platform` オプションを使用します。  
  
 通常、Visual Basic で記述された .NET Framework アセンブリは、プラットフォームに関係なく、同じように実行されます。  ただし、プラットフォーム間で動作が異なる場合があります。  その一般的な例を次に示します。  
  
-   プラットフォームによってメンバーのサイズが変わる構造体 \(ポインター型など\)  
  
-   定数のサイズを含むポインター演算  
  
-   ハンドルに `Integer` ではなく <xref:System.IntPtr> を使用した不適切なプラットフォーム呼び出しまたは COM 宣言  
  
-   <xref:System.IntPtr> の `Integer` へのキャスト  
  
-   すべてのプラットフォームに存在するとは限らないコンポーネントを使用したプラットフォーム呼び出しまたは COM 相互運用機能の使用  
  
 コードの実行対象となるアーキテクチャをあらかじめ想定している場合には、**\/platform** オプションを使用することで、問題が軽減されることがあります。  具体的には、次のように使用します。  
  
-   64 ビット プラットフォームを対象にし、アプリケーションを 32 ビット マシンで実行した場合、エラー メッセージは、このスイッチを使用しない場合よりも、エラー メッセージがかなり早期に出力され、より絞り込まれた内容になります。  
  
-   オプションに `x86` フラグを設定し、その後、アプリケーションを 64 ビット マシンで実行した場合、アプリケーションはネイティブに実行されず、WOW サブシステムで実行されます。  
  
 64 ビット Windows オペレーティング システムの場合:  
  
-   `/platform:x86` でコンパイルされたアセンブリは、WOW64 の下で動作する 32 ビット CLR で実行されます。  
  
-   `/platform:anycpu` でコンパイルされた実行可能ファイルは、64 ビット CLR で実行されます。  
  
-   `/platform:anycpu` でコンパイルでされた DLL は、ロード先のプロセスと同じ CLR で実行されます。  
  
-   `/platform:anycpu32bitpreferred` でコンパイルされた実行可能ファイルは、32 ビット CLR で実行されます。  
  
 64 ビット バージョンの Windows で動作するアプリケーションを開発する方法の詳細については、「[64 ビット アプリケーション](../Topic/64-bit%20Applications.md)」を参照してください。  
  
### Visual Studio IDE で \/platform を設定するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトを選択し、**\[プロジェクト\]** メニューを開き、**\[プロパティ\]** をクリックします。  
  
     詳細については、「[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/ja-jp/983f3c18-832f-4666-afec-74b716ff3e0e)」を参照してください。  
  
2.  **\[コンパイル\]** タブで、**\[32 ビットを優先\]** チェック ボックスをオンまたはオフにするか、または **\[対象の CPU\]** ボックスの一覧で値を選択します。  
  
     詳細については、「[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)」を参照してください。  
  
## 使用例  
 次の例は、`/platform` コンパイラ オプションを使用する方法を示しています。  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## 参照  
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)