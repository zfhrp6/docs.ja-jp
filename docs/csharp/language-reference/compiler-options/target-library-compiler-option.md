---
title: "-target:library (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dll
dev_langs:
- CSharp
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: 12
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f739d778e7bada7f34e42ecfd05364e8cae5d453
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="targetlibrary-c-compiler-options"></a>/target:library (C# コンパイラ オプション)
**/target:library** オプションを指定した場合、コンパイラは実行可能ファイル (EXE) ではなく、ダイナミック リンク ライブラリ (DLL) を作成します。  
  
## <a name="syntax"></a>構文  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a>コメント  
 .dll 拡張子の DLL が作成されます。  
  
 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを特に指定しない限り、出力ファイル名は最初の入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **/out** または **/target:module** オプションまでのすべてのファイルが .dll ファイルを作成するために使用されます。  
  
 .dll ファイルを作成する際に、[Main](../../../csharp/programming-guide/main-and-command-args/index.md)メソッドは必要ありません。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **[プロパティ]** ページを開きます。  
  
2.  **[アプリケーション]** プロパティ ページをクリックします。  
  
3.  **[出力の種類]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、`in.dll` を作成するには、次のコードを使用します。  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
