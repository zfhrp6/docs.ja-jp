---
title: -決定論的
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a>-決定論的

コンパイラで同じ入力に対してコンパイルの間でバイトの出力が同じアセンブリを生成します。 

## <a name="syntax"></a>構文

```
-deterministic
```

## <a name="remarks"></a>コメント

既定では、コンパイラは、タイムスタンプおよびランダムな数値から生成される GUID を付加するための入力の特定のセットからコンパイラ出力が一意で。 使用する、`-deterministic`を生成するオプション、*決定的アセンブリ*、1 つの入力が同じ限り、バイナリ コンテンツを持つはコンパイルの間で同じです。

コンパイラは、決定性のために、次の入力を検討します。

- コマンド ライン パラメーターのシーケンス。
- コンパイラの .rsp 応答ファイルの内容。
- これを使用すると、コンパイラの正確なバージョンとその参照先のアセンブリ。
- 現在のディレクトリ パス。
- すべてのファイルのバイナリ コンテンツを明示的に渡すコンパイラに直接または間接的になど。 
    - ソース ファイル
    - 参照アセンブリ
    - 参照されるモジュール
    - リソース
    - 厳密な名前キー ファイル
    - 応答ファイルの @
    - アナライザー
    - Ruleset
    - アナライザーが使用できる追加のファイル
- (診断および例外のメッセージが生成される言語) の現在のカルチャ。
- 既定のエンコーディングなど、現在のコード ページ エンコーディングが指定されていない場合。
- 存在、非存在、およびコンパイラの検索パス上のファイルの内容 (などにより、指定した`/lib`または`/recurse`)。
- コンパイラを実行する CLR プラットフォームです。
- 値`%LIBPATH%`、アナライザー依存関係の読み込みに影響することができます。

ソースがパブリックに使用できる場合は、信頼できるソースからバイナリがコンパイルされたかどうかを確立するため決定論的コンパイルを使用できます。 継続的なビルド システム バイナリへの変更に依存するビルド ステップを実行する必要があるかどうかを決定するために役立つことができます。 

## <a name="see-also"></a>関連項目
[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
[コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
