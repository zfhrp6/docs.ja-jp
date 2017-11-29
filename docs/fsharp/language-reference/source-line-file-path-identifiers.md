---
title: "ソース行、ファイル、およびパスの識別子 (F#)"
description: "組み込み f# 識別子の値を使用すると、ソースの行番号、ディレクトリ、およびコード内のファイル名へのアクセスを使用する方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a>ソース行、ファイル、およびパスの識別子

識別子`__LINE__`、`__SOURCE_DIRECTORY__`と`__SOURCE_FILE__`ソース行番号、ディレクトリおよびファイル名をコードにアクセスできるようにする組み込みの値は、します。


## <a name="syntax"></a>構文

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>コメント
型を持つこれらの各値`string`です。

次の表では、ソース行、ファイル、および f# で使用可能なパスの識別子をまとめたものです。 これらの識別子はプリプロセッサ マクロではありません。これらは、コンパイラで認識される組み込みの値です。

|事前定義の識別子|説明|
|---------------------|-----------|
|`__LINE__`|現在の行番号に評価される検討`#line`ディレクティブです。|
|`__SOURCE_DIRECTORY__`|ソース ディレクトリの現在の完全パスに評価される検討`#line`ディレクティブです。|
|`__SOURCE_FILE__`|現在のソース ファイル名とそのパスに評価される検討`#line`ディレクティブです。|
詳細については、`#line`ディレクティブを参照してください[コンパイラ ディレクティブ](compiler-directives.md)です。

## <a name="example"></a>例

次のコード例では、これらの値の使用を示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Output:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>関連項目
[コンパイラ ディレクティブ](compiler-directives.md)

[F# 言語リファレンス](index.md)
