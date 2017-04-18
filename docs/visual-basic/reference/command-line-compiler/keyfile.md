---
title: "/keyfile |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c36eac96ac6302db0b567e8249af726c807c2c6c
ms.lasthandoff: 03/13/2017

---
# <a name="keyfile"></a>T:System.Reflection.AssemblyKeyFileAttribute
アセンブリに厳密な名前を付けるキーまたはキー ペアを含むファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a>引数  
 `file`  
 必須です。 キーを含むファイルです。 ファイル名にスペースが含まれている場合は、名前を引用符で囲みます ("") です。  
  
## <a name="remarks"></a>コメント  
 コンパイラでは、アセンブリ マニフェストに公開キーを挿入し、秘密キーを含む、最終的なアセンブリを署名します。 キー ファイルを生成する入力`sn -k file`コマンドライン。 詳細については、「[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)」を参照してください。  
  
 コンパイルする場合は、 `/target:module`、キー ファイルの名前がモジュールに保持され、使用してアセンブリをコンパイルするときに作成されるアセンブリに組み込む[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)します。  
  
 コンパイラに暗号化情報を渡すことができます[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)します。 使用[/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)部分署名されているアセンブリを作成する場合。  
  
 カスタム属性として、このオプションを指定することもできます (<xref:System.Reflection.AssemblyKeyFileAttribute>)、Microsoft 中間言語のモジュールのソース コードにします</xref:System.Reflection.AssemblyKeyFileAttribute>。  
  
 例では両方とも`/keyfile`と[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)がで指定された (コマンド ライン オプションまたはカスタム属性によって)、同じコンパイル時に、コンパイラは、まず、キー コンテナーです。 成功すると、アセンブリがキー コンテナー内の情報で署名します。 指定されたファイルを試みる場合は、コンパイラでは、キー コンテナーが見つからない、`/keyfile`です。 正常に実行する場合、キー ファイルの情報と、アセンブリが署名、キー コンテナーにキーの情報がインストールされている場合 (のような`sn -i`) 次のコンパイル時に、キー コンテナーが有効になるようにします。  
  
 キー ファイルが公開キーのみを含めることがありますに注意してください。  
  
 参照してください[の作成と using strong-named Assemblies](https://msdn.microsoft.com/library/xwb8f617)アセンブリへの署名の詳細についてです。  
  
> [!NOTE]
>  `/keyfile`内から使用可能オプションは、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開発環境には、コマンドラインからコンパイルする場合にのみ使用します。  
  
## <a name="example"></a>例  
 次のコードは、ソース ファイルをコンパイル`Input.vb`し、キー ファイルを指定します。  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
