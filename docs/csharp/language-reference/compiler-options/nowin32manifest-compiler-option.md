---
title: "-nowin32manifest (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7682a3e1ecf483b8495d817ef01e57093ae0f987
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# コンパイラ オプション)
**-nowin32manifest** オプションを利用し、アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指示します。  
  
## <a name="syntax"></a>構文  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>コメント  
 このオプションを使用すると、Win32 リソース ファイルに、あるいは後のビルド ステップでアプリケーション マニフェストを指定しない限り、 Windows Vista で仮想化に従います。  
  
 Visual Studio では、このオプションを **[アプリケーション プロパティ]** ページで設定します。**[マニフェスト]** ドロップダウン リストの **[マニフェストなしでアプリケーションを作成します]** を選択します。 詳しくは、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」をご覧ください。  
  
 マニフェスト作成の詳細については、「[-win32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
