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
ms.openlocfilehash: 1e0d4697e0e14c84c4bc642521cf4f9cdf6a4ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="2852c-102">/nowin32manifest (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="2852c-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="2852c-103">**/nowin32manifest** オプションを利用し、アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="2852c-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2852c-104">構文</span><span class="sxs-lookup"><span data-stu-id="2852c-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="2852c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="2852c-105">Remarks</span></span>  
 <span data-ttu-id="2852c-106">このオプションを使用すると、Win32 リソース ファイルに、あるいは後のビルド ステップでアプリケーション マニフェストを指定しない限り、 Windows Vista で仮想化に従います。</span><span class="sxs-lookup"><span data-stu-id="2852c-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="2852c-107">Visual Studio では、このオプションを **[アプリケーション プロパティ]** ページで設定します。**[マニフェスト]** ドロップダウン リストの **[マニフェストなしでアプリケーションを作成します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2852c-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="2852c-108">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2852c-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="2852c-109">マニフェスト作成の詳細については、「[/win32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2852c-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2852c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="2852c-110">See Also</span></span>  
 [<span data-ttu-id="2852c-111">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="2852c-111">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="2852c-112">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="2852c-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
