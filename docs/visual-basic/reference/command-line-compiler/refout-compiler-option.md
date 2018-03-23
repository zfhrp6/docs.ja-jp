---
title: refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a>refout (Visual Basic)

**-refout** オプションは、参照アセンブリを出力するファイル パスを指定します。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refout:filepath
```

## <a name="arguments"></a>引数

 `filepath` パスと、参照アセンブリのファイル名。 プライマリのアセンブリのサブ フォルダーで一般的になります。 (MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。 すべてのフォルダー`filepath`が存在する必要があります。 コンパイラは作成されません。 

## <a name="remarks"></a>コメント

Visual Basic のサポート、`-refout`バージョン 15.3 と開始を切り替えます。

参照アセンブリはメタデータ コードではなく実装が含まれているメタデータのみのアセンブリです。 匿名型を除くすべての型およびメンバーの情報が含まれます。 メソッドの本体は、1 つに置き換えられます`throw null`ステートメントです。 使用する理由`throw null`(本文のない) ではなく、メソッド本体が PEVerify を実行して (したがって、メタデータの完全性を検証する) を通過できるようにします。

参照アセンブリは、アセンブリ レベル[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性。 この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。 この属性のためのランタイムを実行するための参照アセンブリを読み込む拒否する (ただしリフレクション専用コンテキストに読み込まれていることができます)。 アセンブリに反映するためのツールは、リフレクション専用として参照アセンブリが読み込まれることを確認する必要があります。それ以外の場合、ランタイム、<xref:System.BadImageFormatException>です。

`-refout` オプションと [`-refonly`](refonly-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目
[-refonly](refonly-compiler-option.md)   
[Visual Basic のコマンド ライン コンパイラ](index.md)  
[コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)  

