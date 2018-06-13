---
title: -warnaserror (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 762db1b3d72b5b4c3d606f3517f0b384f466d231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218947"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# コンパイラ オプション)
**-warnaserror+** オプションは、すべての警告をエラーとして扱います  
  
## <a name="syntax"></a>構文  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>コメント  
 通常は警告として報告されるすべてのメッセージが、代わりにエラーとして報告され、ビルド プロセスが停止します (出力ファイルはビルドされません)。  
  
 既定では、**-warnaserror-** が有効になっているため、警告により出力ファイルの生成が妨げられることはありません。 **-warnaserror** は **-warnaserror+** と同じで、警告がエラーとして扱われます。  
  
 必要に応じて、いくつかの特定の警告のみをエラーとして扱う場合は、エラーとして扱う警告番号のコンマ区切りのリストを指定できます。  
  
 コンパイラで表示する警告のレベルを指定するには、[-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) を使用します。 特定の警告を無効にするには、[-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) を使用します。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[ビルド]** プロパティ ページをクリックします。  
  
3.  **警告をエラーとして扱う**プロパティを変更します。  
  
 このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>」を参照してください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルして、コンパイラで警告を表示させないようにします。  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
