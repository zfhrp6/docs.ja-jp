---
title: refonly (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5135ef4d33ddde27416e48c28425aa5b029237b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="-refonly-visual-basic"></a>refonly (Visual Basic)

**- Refonly**オプションは、コンパイル時のプライマリ出力が、実装のアセンブリではなく参照アセンブリであることを示します。 `-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>構文

```console
-refonly
```

## <a name="remarks"></a>コメント

Visual Basic のサポート、`-refout`バージョン 15.3 と開始を切り替えます。

参照アセンブリはメタデータ コードではなく実装が含まれているメタデータのみのアセンブリです。 匿名型を除くすべての型およびメンバーの情報が含まれます。 (本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。

参照アセンブリは、アセンブリ レベル[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性。 この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。 この属性のためのランタイムが実行の参照アセンブリの読み込みが拒否されます (ただしリフレクション専用コンテキストに読み込まれていることができます)。 アセンブリに反映するためのツールは、リフレクション専用として参照アセンブリが読み込まれることを確認する必要があります。それ以外の場合、ランタイム、<xref:System.BadImageFormatException>です。

`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。

## <a name="see-also"></a>関連項目
[-refout](refout-compiler-option.md)   
[Visual Basic のコマンド ライン コンパイラ](index.md)  
[コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)   
