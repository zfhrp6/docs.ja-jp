---
title: "C# Compiler Options Listed Alphabetically | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "compiler options [C#], listed alpabetically"
  - "C# language, compiler options listed alphabitically"
  - "Visual C# compiler, options listed alphabetically"
  - "Visual C#, compiler options listed alphabetically"
ms.assetid: 43535ea0-ca47-4a15-b528-615087a86092
caps.latest.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 25
---
# C# Compiler Options Listed Alphabetically
次のコンパイラ オプションは、アルファベット順に並んでいます。  カテゴリ別の一覧については、「[C\# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md)」を参照してください。  
  
|オプション|目的|  
|-----------|--------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|応答ファイルを読み込んで、オプションを追加します。|  
|[\/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|使用法に関する説明を標準出力に表示します。|  
|`/additionalfile`|コードの生成に直接影響はないが、エラーまたは警告を生成するためにアナライザーが使用できる追加のファイルを指定します。|  
|[\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|指定されたモジュールをこのアセンブリにリンクします。|  
|`/analyzer`|このアセンブリからアナライザーを実行します \(短縮形: \/a\)。|  
|[\/appconfig](../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)|アセンブリのバインド時に app.config の場所を指定します。|  
|[\/baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|ビルドするライブラリのベース アドレスを指定します。|  
|[\/bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|"障害報告" ファイルを作成します。  **\/errorreport:prompt** または **\/errorreport:send** と組み合わせて使用した場合、このファイルがクラッシュ情報と共に送信されます。|  
|[\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|オーバーフロー チェックを生成するようコンパイラに指示します。|  
|`/checksumalgorithm:<alg>`|PDB に格納されているソース ファイルのチェックサムを計算するためのアルゴリズムを指定します。  サポートされる値は、SHA1 \(既定値\) または SHA256 です。|  
|[\/codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|ソース ファイルを開くときに使用するコードページを指定します。|  
|[\/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|デバッグ情報を生成します。|  
|[\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|条件付きコンパイル シンボルを定義します。|  
|[\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|厳密名キーのパブリックな部分のみを使ってアセンブリに遅延署名します。|  
|[\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|生成する XML ドキュメント ファイルを指定します。|  
|[\/errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|内部コンパイラ エラーの処理方法 \(prompt、send、none\) を指定します。  既定値は none です。|  
|[\/filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|出力ファイルのセクションで使用する配置を指定します。|  
|[\/fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|完全修飾パスを生成するようコンパイラに指示します。|  
|[\/help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|使用法に関する説明を標準出力に表示します。|  
|[\/highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|高エントロピ ASLR がサポートされていることを指定します。|  
|**\/incremental**|インクリメンタル コンパイルを有効にします \[廃止\]。|  
|[\/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|厳密な名前のキー コンテナーを指定します。|  
|[\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|厳密な名前のキー ファイルを指定します。|  
|[\/langversion:\<string\>](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|言語バージョンのモード \(ISO\-1、ISO\-2、3、4、5、6、または Default\) を指定します。|  
|[\/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|参照を検索する追加のディレクトリを指定します。|  
|[\/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|指定したアセンブリ内の COM 型情報をプロジェクトで使用できるようにします。|  
|[\/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|このアセンブリに指定されたリソースをリンクします。|  
|[\/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|エントリ ポイントを含む型を指定します \(他のエントリ ポイントはすべて無視します\)。|  
|[\/moduleassemblyname](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)|.  netmodule がアクセスできる非パブリック型のアセンブリを指定します。|  
|`/modulename:<string>`|ソース モジュールの名前を指定します。|  
|[\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|CSC.RSP ファイルを自動で含めないようコンパイラに指示します。|  
|[\/nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|コンパイラの著作権メッセージが表示されないようにします。|  
|[\/nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|標準ライブラリ \(mscorlib.dll\) を参照しないようコンパイラに指示します。|  
|[\/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|特定の警告メッセージを無効にします。|  
|[\/nowin32manifest](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)|アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指定します。|  
|[\/optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|最適化を有効または無効にします。|  
|[\/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|出力ファイル名を指定します \(既定では、メイン クラスまたは最初のファイルの基本名\)。|  
|`/parallel[+&#124;-]`|同時実行ビルドを使用する \(\+\) かどうかを指定します。|  
|[\/pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|.pdb ファイルの名前と場所を指定します。|  
|[\/platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|このコードを実行できるプラットフォームを制限します \(x86、Itanium、x64、anycpu、anycpu32bitpreferred\)。  既定は anycpu です。|  
|[\/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|コンパイラの出力に使用する言語を指定します。|  
|[\/recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|ワイルドカードの指定に従い、現在のディレクトリとサブディレクトリ内のすべてのファイルをインクルードします。|  
|[\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|指定されたアセンブリ ファイルからメタデータを参照します。|  
|[\/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|指定したリソースを埋め込みます。|  
|`/ruleset:<file>`|特定の診断を無効にするルールセット ファイルを指定します。|  
|[\/subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|実行可能ファイルが使用できるサブシステムの最低限のバージョンを指定します。|  
|[\/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|4 つのオプション \([\/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)、[\/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)、[\/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)、[\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)、[\/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)、[\/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)\) のいずれかを使用して、出力ファイルの形式を指定します。|  
|[\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|[アンセーフ](../../../csharp/language-reference/keywords/unsafe.md) コードを許可します。|  
|[\/utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|UTF\-8 エンコードでコンパイラのメッセージを出力します。|  
|[\/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|警告レベル \(0 ～ 4\) を設定します。|  
|[\/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|特定の警告をエラーとして報告します。|  
|[\/win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|出力に使用するアイコンを指定します。|  
|[\/win32manifest](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)|カスタム win32 マニフェスト ファイルを指定します。|  
|[\/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|win32 リソース ファイル \(.res\) を指定します。|  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [C\# Compiler Options Listed by Category](../../../csharp/language-reference/compiler-options/listed-by-category.md)   
 [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)   
 [\<compiler\> 要素](../Topic/%3Ccompiler%3E%20Element.md)