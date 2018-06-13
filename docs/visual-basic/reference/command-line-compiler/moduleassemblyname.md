---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8b579c2c3ae22469706326ee17109b8e39dab60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650791"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
このモジュールが一部となるアセンブリの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`assembly_name`|このモジュールの一部となるアセンブリの名前。|  
  
## <a name="remarks"></a>コメント  
 コンパイラ プロセス、`-moduleassemblyname`場合にのみ、オプション、`-target:module`オプションが指定されました。 これにより、コンパイラでモジュールを作成します。 コンパイラによって作成されたモジュールがで指定されたアセンブリに対してのみ有効では、`-moduleassemblyname`オプション。 別のアセンブリでモジュールを配置すると、実行時エラーが発生します。  
  
 `-moduleassemblyname`オプションは、次に当てはまる場合にのみ必要があります。  
  
-   モジュール内のデータ型へのアクセスを必要な`Friend`参照先アセンブリの型。  
  
-   参照アセンブリがモジュールをビルドするアセンブリにフレンド アセンブリへのアクセスを許可します。  
  
 モジュールの作成の詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)です。 フレンド アセンブリの詳細については、次を参照してください。[フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)です。  
  
> [!NOTE]
>  `-moduleassemblyname`オプションは、Visual Studio 開発環境からは利用できません。 使用可能なコマンド プロンプトからコンパイルするときにのみです。  
  
## <a name="see-also"></a>関連項目  
 [方法: マルチファイル アセンブリをビルドする](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [フレンド アセンブリ](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
