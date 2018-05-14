---
title: -keycontainer (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: edb50dafa376abe55fbeeb312ca5bb8f34c83e7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# コンパイラ オプション)
暗号化キー コンテナーの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>引数  
 `string`  
 厳密な名前のキー コンテナーの名前です。  
  
## <a name="remarks"></a>コメント  
 **-keycontainer** オプションを指定すると、コンパイラは、指定したコンテナーから公開キーをアセンブリ マニフェストに挿入し、秘密キーで最終アセンブリに署名することで、共有可能なコンポーネントを作成します。 キー ファイルを生成するには、コマンド ラインで「sn -k `file`」と入力します。 sn -i は、キー ペアをコンテナーにインストールします。  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) を指定してコンパイルした場合は、キー ファイルの名前がモジュールに保持され、このモジュールを [-addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) でアセンブリにコンパイルするときに、アセンブリに組み込まれます。  
  
 このオプションは、任意の Microsoft Intermediate Language (MSIL) モジュールのソース コードで、カスタム属性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>) として指定することもできます。  
  
 また、暗号化情報を [-keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) でコンパイラに渡すことができます。 公開キーをアセンブリ マニフェストに追加してだけおき、アセンブリの署名はテスト後まで待って行いたい場合は、[-delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) を使います。  
  
 詳細については、「[厳密な名前付きアセンブリの作成と使用](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)」および「[アセンブリへの遅延署名](../../../framework/app-domains/delay-sign-assembly.md)」をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  このコンパイラ オプションは、Visual Studio 開発環境では使うことができません。  
  
 このコンパイラ オプションには、プログラムで <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A> を使ってアクセスできます。  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
