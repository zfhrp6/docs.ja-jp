---
title: "-warnaserror (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0127f8982d4b8c487a7e243025052e3eb9a5ff75
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (C# コンパイラ オプション)
**-warnaserror+** オプションは、すべての警告をエラーとして扱います  
  
## <a name="syntax"></a>構文  
  
```console  
-warnaserror[<U>+</U> | -][:warning-list]  
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
  
     このコンパイラ オプションをプログラムによって設定するには、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>」を参照してください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルして、コンパイラで警告を表示させないようにします。  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
