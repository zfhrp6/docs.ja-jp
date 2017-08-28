---
title: "カテゴリ別の C# コンパイラ オプションの一覧"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- Visual C# compiler, options listed by category
- compiler options [C#], listed by category
- Visual C#, compiler options listed by category
ms.assetid: 96437ecc-6502-4cd3-b070-e9386a298e83
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bf0b4a4130fe69a15e6db438ac1d58b676c9ee8b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="c-compiler-options-listed-by-category"></a>カテゴリ別の C# コンパイラ オプションの一覧
次のコンパイラ オプションは、カテゴリ別に並んでいます。 アルファベット順の一覧については、「[アルファベット順の C# コンパイラ オプションの一覧](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)」を参照してください。  
  
### <a name="optimization"></a>最適化  
  
|オプション|目的|  
|------------|-------------|  
|[/filealign](../../../csharp/language-reference/compiler-options/filealign-compiler-option.md)|出力ファイル内のセクションのサイズを指定します。|  
|[/optimize](../../../csharp/language-reference/compiler-options/optimize-compiler-option.md)|最適化を有効または無効にします。|  
  
### <a name="output-files"></a>出力ファイル  
  
|オプション|目的|  
|------------|-------------|  
|[/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)|処理されたドキュメントのコメントが書き込まれる XML ファイルを指定します。|  
|[/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md)|出力ファイルを指定します。|  
|[/pdb](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)|.pdb ファイルの名前と場所を指定します。|  
|[/platform](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)|出力プラットフォームを指定します。|  
|[/preferreduilang](../../../csharp/language-reference/compiler-options/preferreduilang-compiler-option.md)|コンパイラ出力用の言語を指定します。|  
|[/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md)|6 つのオプション ([/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)、[/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)、[/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)、[/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)、[/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)、[/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)) のいずれかを使用して、出力ファイルの形式を指定します。|  
|/modulename:\<文字列>|ソース モジュールの名前を指定します。|  
  
### <a name="net-framework-assemblies"></a>.NET Framework アセンブリ  
  
|オプション|目的|  
|------------|-------------|  
|[/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md)|このアセンブリを構成する 1 つ以上のモジュールを指定します。|  
|[/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)|公開キーを追加し、アセンブリには署名しないでおくようコンパイラに指示します。|  
|[/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md)|暗号化キー コンテナーの名前を指定します。|  
|[/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md)|暗号化キーを格納するファイル名を指定します。|  
|[/lib](../../../csharp/language-reference/compiler-options/lib-compiler-option.md)|[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) で参照されるアセンブリの場所を指定します。|  
|[/nostdlib](../../../csharp/language-reference/compiler-options/nostdlib-compiler-option.md)|標準ライブラリ (mscorlib.dll) をインポートしないようコンパイラに指示します。|  
|[/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)|アセンブリが格納されているファイルからメタデータをインポートします。|  
|/analyzer|このアセンブリからアナライザーを実行します (短縮形: /a)。|  
|/additionalfile|コードの生成に直接影響はないが、エラーまたは警告を生成するためにアナライザーが使用できる追加のファイルを指定します。|  
  
### <a name="debuggingerror-checking"></a>デバッグ/エラー チェック  
  
|オプション|目的|  
|------------|-------------|  
|[/bugreport](../../../csharp/language-reference/compiler-options/bugreport-compiler-option.md)|バグを簡単に報告するための情報を含むファイルを作成します。|  
|[/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md)|データ型の境界をオーバーフローする整数演算で、実行時に例外を発生させるかどうかを指定します。|  
|[/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md)|デバッグ情報を生成するようコンパイラに指示します。|  
|[/errorreport](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)|エラー報告の動作を設定します。|  
|[/fullpaths](../../../csharp/language-reference/compiler-options/fullpaths-compiler-option.md)|コンパイラ出力に含まれるファイルの絶対パスを指定します。|  
|[/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md)|指定した警告がコンパイラで生成されないようにします。|  
|[/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md)|警告レベルを設定します。|  
|[/warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md)|警告をエラーに昇格します。|  
|/ruleset:\<ファイル>|特定の診断を無効にするルールセット ファイルを指定します。|  
  
### <a name="preprocessor"></a>プリプロセッサ  
  
|オプション|目的|  
|------------|-------------|  
|[/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md)|プリプロセッサ シンボルを定義します。|  
  
### <a name="resources"></a>リソース  
  
|オプション|目的|  
|------------|-------------|  
|[/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md)|指定したアセンブリ内の COM 型情報をプロジェクトで使用できるようにします。|  
|[/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)|マネージ リソースへのリンクを作成します。|  
|[/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)|.NET Framework のリソースを出力ファイルに埋め込みます。|  
|[/win32icon](../../../csharp/language-reference/compiler-options/win32icon-compiler-option.md)|出力ファイルに挿入する .ico ファイルを指定します。|  
|[/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md)|出力ファイルに挿入する Win32 リソースを指定します。|  
  
### <a name="miscellaneous"></a>その他の指定  
  
|オプション|目的|  
|------------|-------------|  
|[@](../../../csharp/language-reference/compiler-options/response-file-compiler-option.md)|応答ファイルを指定します。|  
|[/?](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|stdout にコンパイラ オプションの一覧を表示します。|  
|[/baseaddress](../../../csharp/language-reference/compiler-options/baseaddress-compiler-option.md)|DLL を読み込む位置に推奨されるベース アドレスを指定します。|  
|[/codepage](../../../csharp/language-reference/compiler-options/codepage-compiler-option.md)|コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。|  
|[/help](../../../csharp/language-reference/compiler-options/help-compiler-option.md)|stdout にコンパイラ オプションの一覧を表示します。|  
|[/highentropyva](../../../csharp/language-reference/compiler-options/highentropyva-compiler-option.md)|実行可能ファイルが ASLR (Address Space Layout Randomization) をサポートするように指定します。|  
|[/langversion](../../../csharp/language-reference/compiler-options/langversion-compiler-option.md)|言語バージョンのモード: Default、ISO-1、ISO-2、3、4、5、6、7、7.1、または Latest を指定します。 |  
|[/main](../../../csharp/language-reference/compiler-options/main-compiler-option.md)|**Main** メソッドの場所を指定します。|  
|[/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)|csc.rsp でコンパイルにしないようコンパイラに指示します。|  
|[/nologo](../../../csharp/language-reference/compiler-options/nologo-compiler-option.md)|コンパイラの著作権情報が表示されないようにします。|  
|[/recurse](../../../csharp/language-reference/compiler-options/recurse-compiler-option.md)|コンパイルするソース ファイルをサブディレクトリで検索します。|  
|[/subsystemversion](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)|実行可能ファイルが使用できるサブシステムの最低限のバージョンを指定します。|  
|[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)|[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用するコードのコンパイルを有効にします。|  
|[/utf8output](../../../csharp/language-reference/compiler-options/utf8output-compiler-option.md)|UTF-8 エンコードを使用してコンパイラ出力を表示します。|  
|/parallel[+&#124;-]|同時実行ビルドを使用する (+) かどうかを指定します。|  
|/checksumalgorithm:\<alg>|PDB に格納されているソース ファイルのチェックサムを計算するためのアルゴリズムを指定します。  サポートされる値は、SHA1 (既定値) または SHA256 です。|  
  
## <a name="obsolete-options"></a>廃止されたオプション  
  
|オプション|目的|  
|---|---|  
|/incremental|インクリメンタル コンパイルを有効にします。|  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [アルファベット順の C# コンパイラ オプションの一覧](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)   
 [方法: Visual Studio のコマンドラインのための環境変数を設定する](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)

