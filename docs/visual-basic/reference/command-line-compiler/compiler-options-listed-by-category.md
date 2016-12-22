---
title: "Visual Basic Compiler Options Listed by Category | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic compiler, options"
ms.assetid: fbe36f7a-7cfa-4f77-a8d4-2be5958568e3
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic Compiler Options Listed by Category
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コマンド ライン コンパイラは、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) 内からプログラムをコンパイルする方法の代替手段として提供されています。  機能のカテゴリ順に並べ替えた [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コマンド ライン コンパイラ オプションの一覧を次に示します。  
  
## コンパイラ出力  
  
|||  
|-|-|  
|オプション|目的|  
|[\/nologo](../../../visual-basic/reference/command-line-compiler/nologo.md)|コンパイラの著作権情報が表示されないようにします。|  
|[\/utf8output](../../../visual-basic/reference/command-line-compiler/utf8output.md)|UTF\-8 エンコードを使用してコンパイラ出力を表示します。|  
|[\/verbose](../../../visual-basic/reference/command-line-compiler/verbose.md)|コンパイル中に追加の情報を出力します。|  
|`/modulename:<string>`|ソース モジュールの名前を指定します。|  
|[\/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|コンパイラ出力用の言語を指定します。|  
  
## 最適化  
  
|||  
|-|-|  
|オプション|目的|  
|[\/filealign](../../../visual-basic/reference/command-line-compiler/filealign.md)|出力ファイルでセクションをアラインするサイズを指定します。|  
|[\/optimize](../../../visual-basic/reference/command-line-compiler/optimize.md)|最適化を有効または無効にします。|  
  
## 出力ファイル  
  
|||  
|-|-|  
|オプション|目的|  
|[\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)|ドキュメント コメントを XML ファイルに出力します。|  
|[\/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)|[!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] が対象になるようにコンパイラを設定します。|  
|[\/out](../../../visual-basic/reference/command-line-compiler/out.md)|出力ファイルを指定します。|  
|[\/target](../../../visual-basic/reference/command-line-compiler/target.md)|出力の形式を指定します。|  
  
## .NET アセンブリ  
  
|||  
|-|-|  
|オプション|目的|  
|[\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)|指定ファイル内のすべての型情報を現在のコンパイル対象のプロジェクトで使用できるようにします。|  
|[\/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)|アセンブリに完全に署名するか、部分的に署名するかを指定します。|  
|[\/imports](../../../visual-basic/reference/command-line-compiler/imports.md)|指定したアセンブリから名前空間をインポートします。|  
|[\/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)|アセンブリに厳密な名前を付けるキー ペアのキー コンテナー名を指定します。|  
|[\/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)|アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。|  
|[\/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)|[\/reference](../../../visual-basic/reference/command-line-compiler/reference.md) オプションにより参照されるアセンブリの場所を指定します。|  
|[\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)|アセンブリからメタデータをインポートします。|  
|[\/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)|モジュールが一部となるアセンブリの名前を指定します。|  
|`/analyzer`|このアセンブリからアナライザーを実行します \(短縮形: \/a\)。|  
|`/additionalfile`|コードの生成に直接影響はないが、エラーまたは警告を生成するためにアナライザーが使用できる追加のファイルを指定します。|  
  
## デバッグ\/エラー チェック  
  
|||  
|-|-|  
|オプション|目的|  
|[\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)|バグを簡単に報告するための情報を含むファイルを作成します。|  
|[\/debug](../../../visual-basic/reference/command-line-compiler/debug.md)|デバッグ情報を生成します。|  
|[\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)|警告を生成するコンパイラの機能を無効にします。|  
|[\/quiet](../../../visual-basic/reference/command-line-compiler/quiet.md)|コンパイラで構文関連のエラーと警告のコードが表示されないようにします。|  
|[\/removeintchecks](../../../visual-basic/reference/command-line-compiler/removeintchecks.md)|整数オーバーフローのチェックを無効にします。|  
|[\/warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)|警告をエラーに昇格します。|  
|`/ruleset:<file>`|特定の診断を無効にするルールセット ファイルを指定します。|  
  
## ヘルプ  
  
|||  
|-|-|  
|オプション|目的|  
|[\/?](../../../visual-basic/reference/command-line-compiler/help.md)|コンパイラ オプションを出力します。  このコマンドは、`/help` オプションの指定と同じです。  コンパイルは発生しません。|  
|[\/help](../../../visual-basic/reference/command-line-compiler/help.md)|コンパイラ オプションを出力します。  このコマンドは、`/?` オプションの指定と同じです。  コンパイルは発生しません。|  
  
## 言語  
  
|||  
|-|-|  
|オプション|目的|  
|[\/langversion](../../../visual-basic/reference/command-line-compiler/langversion.md)|言語バージョンを指定します: 9&#124;9.0&#124;10&#124;10.0&#124;11&#124;11.0。|  
|[\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)|変数の明示的な宣言を強制的に適用します。|  
|[\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)|厳密な型のセマンティクスを強制的に適用します。|  
|[\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)|文字列比較をバイナリにするか、ロケール固有のテキストのセマンティクスを使用するかどうかを指定します。|  
|[\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)|変数宣言でローカル型推論を使用できるようにします。|  
  
## プリプロセッサ  
  
|||  
|-|-|  
|オプション|目的|  
|[\/define](../../../visual-basic/reference/command-line-compiler/define.md)|条件付きコンパイルのシンボルを定義します。|  
  
## リソース  
  
|||  
|-|-|  
|オプション|目的|  
|[\/linkresource](../../../visual-basic/reference/command-line-compiler/linkresource.md)|マネージ リソースへのリンクを作成します。|  
|[\/resource](../../../visual-basic/reference/command-line-compiler/resource.md)|マネージ リソースをアセンブリに埋め込みます。|  
|[\/win32icon](../../../visual-basic/reference/command-line-compiler/win32icon.md)|.ico ファイルを出力ファイルに挿入します。|  
|[\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)|Win32 リソースを出力ファイルに挿入します。|  
  
## その他の指定  
  
|||  
|-|-|  
|オプション|目的|  
|[@ \(応答ファイルの指定\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)|応答ファイルを指定します。|  
|[\/baseaddress](../../../visual-basic/reference/command-line-compiler/baseaddress.md)|DLL のベース アドレスを指定します。|  
|[\/codepage](../../../visual-basic/reference/command-line-compiler/codepage.md)|コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。|  
|[\/errorreport](../../../visual-basic/reference/command-line-compiler/errorreport.md)|[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラで内部コンパイル エラーを報告するかどうかを指定します。|  
|[\/highentropyva](../../../visual-basic/reference/command-line-compiler/highentropyva.md)|特定の実行可能ファイルで高エントロピ ASLR \(Address Space Layout Randomization\) をサポートするかどうかを Windows カーネルに示します。|  
|[\/main](../../../visual-basic/reference/command-line-compiler/main.md)|起動時に使用する `Sub``Main` プロシージャを含むクラスを指定します。|  
|[\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)|コンパイルに Vbc.rsp が使用されないようにします。|  
|[\/nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)|コンパイラが標準ライブラリを参照しないようにします。|  
|[\/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)|アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指定します。|  
|[\/platform](../../../visual-basic/reference/command-line-compiler/platform.md)|コンパイラによる出力ファイルの対象となるプロセッサ プラットフォームを指定します。|  
|[\/recurse](../../../visual-basic/reference/command-line-compiler/recurse.md)|コンパイルするソース ファイルをサブディレクトリで検索します。|  
|[\/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md)|すべての型宣言に対して名前空間を指定します。|  
|[\/sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)|Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。|  
|[\/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)|コンパイラが Visual Basic Runtime Library を参照せずにコンパイルするか、特定のランタイム ライブラリを参照してコンパイルするかを指定します。|  
|[\/win32manifest](../../../visual-basic/reference/command-line-compiler/win32manifest.md)|プロジェクトのポータブル実行可能 \(PE\) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。|  
|`/parallel[+&#124;-]`|同時実行ビルドを使用する \(\+\) かどうかを指定します。|  
|`/checksumalgorithm:<alg>`|PDB に格納されているソース ファイルのチェックサムを計算するためのアルゴリズムを指定します。  サポートされる値は、SHA1 \(既定値\) または SHA256 です。|  
  
## 参照  
 [Visual Basic Compiler Options Listed Alphabetically](../../../visual-basic/reference/command-line-compiler/compiler-options-listed-alphabetically.md)   
 [Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)   
 [C\# Compiler Options Listed Alphabetically](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [C\# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md)