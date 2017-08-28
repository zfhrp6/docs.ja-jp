---
title: "-win32res (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32res
dev_langs:
- CSharp
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
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
ms.openlocfilehash: 4552b526767584e62106b2b10f8a1e6394a23b46
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="win32res-c-compiler-options"></a>/win32res (C# コンパイラ オプション)
**/win32res** オプションは、Win32 リソースを出力ファイルに挿入します。  
  
## <a name="syntax"></a>構文  
  
```console  
/win32res:filename  
```  
  
## <a name="arguments"></a>引数  
 `filename`  
 出力ファイルに追加するリソース ファイル。  
  
## <a name="remarks"></a>コメント  
 Win32 リソース ファイルは、[リソース コンパイラ](http://go.microsoft.com/fwlink/?LinkId=148370)を使用して作成できます。 リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。.res ファイルは .rc ファイルから作成されます。  
  
 Win32 リソースは、バージョンまたはビットマップ (アイコン) 情報を格納できます。エクスプローラーでアプリケーションを識別するのに役立ちます。 **/win32res** を指定しない場合、コンパイラはアセンブリ バージョンに基づいてバージョン情報を生成します。  
  
 .NET Framework リソース ファイルの [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (参照) または [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (アタッチ) をご覧ください。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[リソース ファイル]** ボタンをクリックし、コンボ ボックスを利用してファイルを選択します。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、Win32 リソース ファイル `rf.res` をアタッチし、`in.exe` を作成します。  
  
```console  
csc /win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md)   
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)

