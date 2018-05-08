---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d682533f96b5fb56430a0826d37a9794dc8c5d8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-keycontainer"></a>-keycontainer
アセンブリに厳密な名前を付けるキー ペアのキー コンテナー名を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`container`|必須。 コンテナー キーを含むファイルです。 ファイル名を引用符で囲みます ("")、名前にスペースが含まれている場合。|  
  
## <a name="remarks"></a>コメント  
 コンパイラは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを含む、最終的なアセンブリを署名することにより、共有可能なコンポーネントを作成します。 キー ファイルを生成する入力`sn -k``file`コマンドライン。 `-i`オプションは、コンテナーにキーのペアをインストールします。 詳細については、[Sn.exe (厳密名ツール)] を参照してください。[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 コンパイルする場合`-target:module`、キー ファイルの名前が、モジュール内に保持しを伴うアセンブリをコンパイルするときに作成されるアセンブリに組み込む[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)です。  
  
 このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute>) として指定することもできます。  
  
 また、暗号化情報を [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 参照してください[作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリに署名する方法についてです。  
  
> [!NOTE]
>  `-keycontainer`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー コンテナーを指定します。  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
