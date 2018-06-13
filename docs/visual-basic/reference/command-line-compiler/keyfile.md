---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 12895e4a18203a0d6c409a3b2117abbc59fab7a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653482"
---
# <a name="-keyfile"></a>-keyfile
アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 必須。 キーを含むファイルです。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。  
  
## <a name="remarks"></a>コメント  
 コンパイラは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを使用し、最終的なアセンブリを署名します。 キー ファイルを生成する入力`sn -k file`コマンドライン。 詳細については、[Sn.exe (厳密名ツール)] を参照してください。[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 コンパイルする場合`-target:module`、キー ファイルの名前が、モジュール内に保持しを伴うアセンブリをコンパイルするときに作成されるアセンブリに組み込む[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)です。  
  
 また、暗号化情報を [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) を使います。  
  
 カスタム属性としては、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyFileAttribute>)、Microsoft intermediate language モジュールのソース コードにします。  
  
 場合両方`-keyfile`と[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)がで指定された (コマンド ライン オプションまたはカスタム属性によって)、同じコンパイル時に、コンパイラにより、キー コンテナーを最初に試行します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 指定されたファイルを試みますが、コンパイラが、キー コンテナーを見つけられない場合`-keyfile`です。 これが成功した、キーのファイルの情報と、アセンブリは署名およびキー コンテナーにキー情報がインストールされている場合 (に似て`sn -i`) 次のコンパイル時に、キー コンテナーが有効になるようにします。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 参照してください[作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリに署名する方法についてです。  
  
> [!NOTE]
>  `-keyfile`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー ファイルを指定します。  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
