---
title: "-target:library (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66e2edd86dc4a1302b23dab07226a5d56cb79b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」をご覧ください。  
  
## <a name="example"></a>例  
 `in.cs` をコンパイルし、`in.dll` を作成するには、次のコードを使用します。  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (c# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
