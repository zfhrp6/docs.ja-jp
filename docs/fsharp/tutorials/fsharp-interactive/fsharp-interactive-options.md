---
title: "F# Interactive オプション"
description: "F# Interactive でサポートされているコマンド ライン オプションの詳細について fsi.exe です。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="f-interactive-options"></a>F# Interactive オプション

> [!NOTE]
この記事では、現時点の Windows のエクスペリエンスについてのみ説明します。  書き換えられる予定です。

このトピックでは、F# Interactive (`fsi.exe`) でサポートされるコマンド ライン オプションについて説明します。 F# Interactive では、F# コンパイラと同じコマンド ライン オプションを数多く使用できますが、その他にもいくつかのオプションを使用できます。

## <a name="using-f-interactive-for-scripting"></a>F# Interactive を使用したスクリプトの実行
F# Interactive、`fsi.exe`対話形式で起動できる、またはスクリプトを実行するコマンドラインから起動できます。 コマンド ラインの構文は次のとおりです。

```
> fsi.exe [options] [ script-file [arguments] ]
```

F# スクリプト ファイルのファイル拡張子は `.fsx` です。

## <a name="table-of-f-interactive-options"></a>F# Interactive のオプションの表
次の表は、F# Interactive でサポートされるオプションの一覧です。 これらのオプションをコマンド ラインまたは Visual Studio IDE で設定できます。 Visual Studio IDE でこれらのオプションを設定するには、開く、**ツール**メニューの **オプション.**の順に展開、 **f# Tools**ノード**f# Interactive**です。

F# Interactive オプションの引数でリストを指定する場合は、リストの要素をセミコロン (`;`) で区切ります。

|オプション|説明|
|------|-----------|
|**--**|F# Interactive コマンドライン引数として f# のプログラムまたはスクリプトでは、リストを使用してコードでアクセスできる残りの引数を処理するように指示するために使用**fsi.CommandLineArgs**です。|
|**-チェック**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--コードページ:&lt;int&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--crossoptimize**[**+**&#124;**-**]|モジュール間の最適化を有効または無効にします。|
|**--デバッグ**[**+**&#124;**-**]<br /><br />**--デバッグ:**[**完全**&#124;**pdbonly**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**完全**&#124;**pdbonly**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**-定義:&lt;文字列&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--exec**|ファイルを読み込んだ後、またはコマンド ラインで指定したスクリプトを実行した後に F# Interactive を終了するように指示します。|
|**fullpaths--**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--gui**[**+**&#124;**-**]|Windows フォーム イベントのループを有効または無効にします。 既定ではオンです。|
|**-ヘルプ**<br /><br />**-?**|各オプションのコマンド ライン構文と簡単な説明を表示するために使用します。|
|**--lib:&lt;フォルダー一覧&gt;**<br /><br />**-I:&lt;フォルダー一覧&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--読み込む:&lt;ファイル名&gt;**|指定したソース コードを起動時にコンパイルし、コンパイルされた F# の構成要素をセッションに読み込みます。 など、ターゲットのソースにスクリプト ディレクティブが含まれている場合**#use**または**#load**、する必要がありますを使用して**--使用**または**#use** ではなく**--読み込む**または**#load**です。|
|**mlcompatibility--**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**noframework--**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、次を参照してください[コンパイラ オプション。](../../language-reference/compiler-options.md)|
|**nologo--**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--nowarn:&lt;警告リスト&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--最適化**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--非表示**|F# Interactive の出力を抑制する状況、 **stdout**ストリーム。|
|**--引用デバッグ**|追加のデバッグ情報が F# 引用符リテラルとリフレクション定義から派生した式に対して生成されるように指定します。 デバッグ情報は F# 式ツリー ノードのカスタム属性に追加されます。 参照してください[コード クォート](../../language-reference/code-quotations.md)と[Expr.CustomAttributes](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3)です。|
|**--readline**[**+**&#124;**-**]|対話モードでのタブ補完を有効または無効にします。|
|**--参照:&lt;ファイル名&gt;**<br /><br />**-r:&lt;ファイル名&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--tailcalls**[**+**&#124;**-**]|tail IL 命令の使用を有効または無効にします。有効にすると、スタック フレームが tail 再帰関数で再利用されます。 既定では、このオプションは有効になっています。|
|**--使用:&lt;ファイル名&gt;**|指定したファイルを起動時に最初の入力として使用するよう、インタープリターに指示します。|
|**--utf8output**|fsc.exe コンパイラ オプションと同じです。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**-警告:&lt;警告レベル&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--warnaserror**[**+**&#124;**-**]|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|
|**--warnaserror**[**+**&#124;**-** ]:**&lt;int 一覧&gt;**|同じ、 **fsc.exe**コンパイラ オプション。 詳細については、「[コンパイラ オプション](../../language-reference/compiler-options.md)」を参照してください。|

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----|-----------|
|[コンパイラ オプション](../../language-reference/compiler-options.md)|F# コンパイラで使用可能なコマンド ライン オプションについて説明します**fsc.exe**です。|
