---
title: "-win32icon (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32icon
dev_langs:
- CSharp
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: 18
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
ms.openlocfilehash: af5b9c3a44163167d932d378cbac4976e07eacbf
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="win32icon-c-compiler-options"></a>/win32icon (C# コンパイラ オプション)
**/win32icon** オプションは、エクスプローラーで出力ファイルを適切に表示する .ico ファイルを出力ファイルに挿入します。  
  
## <a name="syntax"></a>構文  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに追加する .ico ファイル。  
  
## <a name="remarks"></a>コメント  
 .ico ファイルは[リソース コンパイラ](http://go.microsoft.com/fwlink/?LinkId=148370)で作成できます。 リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。.ico ファイルは .rc ファイルから作成されます。  
  
 .NET Framework リソース ファイルの [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (参照) または [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (アタッチ) をご覧ください。 .res ファイルのインポートについては、[/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[アプリケーション アイコン]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、.ico ファイル `rf.ico` をアタッチし、`in.exe` を作成します。  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

