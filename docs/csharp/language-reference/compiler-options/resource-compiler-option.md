---
title: "-resource (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
dev_langs:
- CSharp
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fdb7be630300e11c2e63d88bd6add7d229714bfa
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="resource-c-compiler-options"></a>/resource (C# コンパイラ オプション)
指定されたリソースを出力ファイルに埋め込みます。  
  
## <a name="syntax"></a>構文  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに埋め込む .NET Framework リソース ファイルです。  
  
 `identifier` (省略可能)  
 リソースの論理名。リソースを読み込むために使われる名前です。 既定値はファイル名です。  
  
 `accessibility-modifier` (省略可能)  
 リソースのアクセシビリティ。パブリックまたはプライベートです。 既定値はパブリックです。  
  
## <a name="remarks"></a>コメント  
 [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) を使用すると、リソースがアセンブリにリンクされ、リソース ファイルは出力ファイルに追加されません。  
  
 既定では、リソースは、C# コンパイラを使用して作成されるときにアセンブリ内でパブリックになります。 リソースをプライベートにするには、アクセシビリティ修飾子として `private` を指定します。 `public` と `private` 以外のアクセシビリティは使用できません。  
  
 `filename` が [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) や開発環境などで作成された .NET Framework リソース ファイルである場合は、<xref:System.Resources> 名前空間のメンバーを使ってそのファイルにアクセスできます。 詳細については、「<xref:System.Resources.ResourceManager?displayProperty=fullName>」を参照してください。 それ以外のすべてのリソースについては、<xref:System.Reflection.Assembly> クラスの `GetManifestResource`* メソッドを使って、実行時にリソースにアクセスします。  
  
 **/res** は **/resource** の省略形です。  
  
 出力ファイルにおけるリソースの順序は、コマンド ラインでの指定順序に基づいて決定されます。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトにリソース ファイルを追加します。  
  
2.  **ソリューション エクスプローラー**で、埋め込むファイルを選択します。  
  
3.  選択したファイルの **[プロパティ]** ウィンドウで、**[ビルド アクション]** を選択します。  
  
4.  **[ビルド アクション]** を **[埋め込まれたリソース]**に設定します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.FileProperties2.BuildAction%2A>」を参照してください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、リソース ファイル `rf.resource` をアタッチします。  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

