---
title: "-keyfile (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keyfile
dev_langs:
- CSharp
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 4f9ccbfe7126aac3214ccf08015353eec0490cd4
ms.contentlocale: ja-jp
ms.lasthandoff: 05/10/2017

---
# <a name="keyfile-c-compiler-options"></a>/keyfile (C# コンパイラ オプション)
暗号化キーを格納するファイル名を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
/keyfile:file  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|----------|----------------|  
|`file`|厳密な名前のキーを格納するファイルの名前。|  
  
## <a name="remarks"></a>コメント  
 このオプションを指定すると、コンパイラは、指定したファイルからアセンブリ マニフェストに公開キーを挿入し、最終的なアセンブリに秘密キーで署名します。 キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。  
  
 **/target:module** を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、[/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) でアセンブリをコンパイルすると作成されるアセンブリに組み込まれます。  
  
 また、暗号化情報を [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) でコンパイラに渡すことができます。 部分的に署名されたアセンブリを作成する場合は、[/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使います。  
  
 同じコンパイルで (コマンド ライン オプションまたはカスタム属性によって) /keyfile と /keycontainer を両方とも指定すると、コンパイラは最初にキー コンテナーを試します。 それが成功すると、アセンブリはキー コンテナーの情報で署名されます。 キー コンテナーが見つからない場合、コンパイラは /keyfile で指定されたファイルを検索します。 ファイルが検出された場合、アセンブリはキー ファイルの情報で署名され、キー情報はキー コンテナーにインストールされるため (sn -i と同様)、次のコンパイル時にはキー コンテナーが有効になります。  
  
 キー ファイルには公開キーだけが含まれる場合があることに注意してください。  
  
 詳しくは、「[厳密な名前付きアセンブリの作成と使用](https://msdn.microsoft.com/library/xwb8f617)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[署名]** プロパティ ページをクリックします。  
  
3.  **[厳密な名前のキー ファイルを選択してください]** プロパティを変更します。  
  
 このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A> を使ってアクセスできます。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 方法: プロジェクト プロパティと構成設定を変更する](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
