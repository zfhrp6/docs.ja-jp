---
title: "/bugreport | Microsoft Docs"
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
  - "-bugreport compiler option [Visual Basic]"
  - "bugreport compiler option [Visual Basic]"
  - "/bugreport compiler option [Visual Basic]"
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# /bugreport
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

バグ レポートの提出時に使用するファイルを作成します。  
  
## 構文  
  
```  
/bugreport:file  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`file`|必ず指定します。  バグ レポートを作成するファイルの名前。  ファイル名に空白が含まれている場合は、二重引用符 \(" "\) で囲みます。|  
  
## 解説  
 `file` には次の情報が追加されます。  
  
-   コンパイル時のすべてのソース コード ファイルのコピー。  
  
-   コンパイルで使用されたコンパイラ オプションの一覧。  
  
-   コンパイラ、共通言語ランタイム、およびオペレーティング システムのバージョン情報。  
  
-   コンパイラの出力 \(指定されている場合\)。  
  
-   問題の説明。プロンプトが表示されます。  
  
-   問題の修正方法の説明。プロンプトが表示されます。  
  
 すべてのソース コード ファイルのコピーが `file` に収められるため、問題があると思われるコードをできるだけ小さなプログラムとして再生成できます。  
  
> [!IMPORTANT]
>  `/bugreport` オプションにより、機密性の高い情報を格納するファイルが作成されます。  これには、現在時刻、コンパイラのバージョン、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のバージョン、オペレーティング システムのバージョン、ユーザー名、コンパイラを起動したコマンド ライン引数、すべてのソース コード、参照されるアセンブリのバイナリ形式が含まれます。  このオプションを設定するには、[!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] アプリケーションのサーバー側のコンパイルに使用する web.config ファイル内のコマンド ライン オプションを指定します。  これを回避するには、Machine.config ファイルを変更して、ユーザーがサーバーでコンパイルすることを許可しないようにします。  
  
 このオプションを `/errorreport:prompt`、`/errorreport:queue`、または `/errorreport:send` と組み合わせて使用しているときに、アプリケーションで内部コンパイラ エラーが発生すると、`file` 内の情報がマイクロソフトに送信されます。  マイクロソフトのエンジニアは、この情報を基にエラーの原因を特定し、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の次のリリースの改善に役立てます。  既定では、マイクロソフトに情報は送信されません。  ただし、`/errorreport:queue` を使用してアプリケーションをコンパイルする \(既定で有効になっています\) ときに、このアプリケーションはエラー レポートを収集します。  そして、コンピューターの管理者がログインすると、エラー レポート システムが、ログオン以降に発生したエラー レポートをマイクロソフトに送信できるポップアップ ウィンドウを表示します。  
  
> [!NOTE]
>  `/bugreport` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 使用例  
 `T2.vb` をコンパイルし、すべてのバグ レポート情報を `Problem.txt` ファイルに出力する場合のコード例です。  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [\/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [securityPolicy の trustLevel 要素 \(ASP.NET 設定スキーマ\)](http://msdn.microsoft.com/ja-jp/729ab04c-03da-4ee5-86b1-be9d08a09369)