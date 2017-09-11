---
title: "-nowin32manifest (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /nowin32manifest
dev_langs:
- CSharp
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: 15
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
ms.openlocfilehash: 8314fd661ccce968238b480b54847abf7cbece74
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="nowin32manifest-c-compiler-options"></a><span data-ttu-id="463fa-102">/nowin32manifest (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="463fa-102">/nowin32manifest (C# Compiler Options)</span></span>
<span data-ttu-id="463fa-103">**/nowin32manifest** オプションを利用し、アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指示します。</span><span class="sxs-lookup"><span data-stu-id="463fa-103">Use the **/nowin32manifest** option to instruct the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="463fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="463fa-104">Syntax</span></span>  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="463fa-105">コメント</span><span class="sxs-lookup"><span data-stu-id="463fa-105">Remarks</span></span>  
 <span data-ttu-id="463fa-106">このオプションを使用すると、Win32 リソース ファイルに、あるいは後のビルド ステップでアプリケーション マニフェストを指定しない限り、 Windows Vista で仮想化に従います。</span><span class="sxs-lookup"><span data-stu-id="463fa-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span>  
  
 <span data-ttu-id="463fa-107">Visual Studio では、このオプションを **[アプリケーション プロパティ]** ページで設定します。**[マニフェスト]** ドロップダウン リストの **[マニフェストなしでアプリケーションを作成します]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="463fa-107">In Visual Studio, set this option in the **Application Property** page by selecting the **Create Application Without a Manifest** option in the **Manifest** drop down list.</span></span> <span data-ttu-id="463fa-108">詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="463fa-108">For more information, see [Application Page, Project Designer (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).</span></span>  
  
 <span data-ttu-id="463fa-109">マニフェスト作成の詳細については、「[/win32manifest (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="463fa-109">For more information about manifest creation, see [/win32manifest (C# Compiler Options)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="463fa-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="463fa-110">See Also</span></span>  
 <span data-ttu-id="463fa-111">[C# コンパイラのオプション](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="463fa-111">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
 [<span data-ttu-id="463fa-112">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="463fa-112">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)

