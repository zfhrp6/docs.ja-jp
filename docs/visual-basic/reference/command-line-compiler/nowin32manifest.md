---
title: -nowin32manifest (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /nowin32manifest compiler option [Visual Basic]
- nowin32manifest compiler option [Visual Basic]
- -nowin32manifest compiler option [Visual Basic]
ms.assetid: c0528aae-83b3-4425-99f0-19448e9843e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c539f7833c86215a1b0f8102f9fc46419636bc7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-nowin32manifest-visual-basic"></a><span data-ttu-id="a1875-102">-nowin32manifest (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1875-102">-nowin32manifest (Visual Basic)</span></span>
<span data-ttu-id="a1875-103">アプリケーション マニフェストを実行可能ファイルに埋め込まないようコンパイラに指定します。</span><span class="sxs-lookup"><span data-stu-id="a1875-103">Instructs the compiler not to embed any application manifest into the executable file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1875-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1875-104">Syntax</span></span>  
  
```  
-nowin32manifest  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1875-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a1875-105">Remarks</span></span>  
 <span data-ttu-id="a1875-106">このオプションを使用すると、Win32 リソース ファイルに、あるいは後のビルド ステップでアプリケーション マニフェストを指定しない限り、 Windows Vista で仮想化に従います。</span><span class="sxs-lookup"><span data-stu-id="a1875-106">When this option is used, the application will be subject to virtualization on Windows Vista unless you provide an application manifest in a Win32 Resource file or during a later build step.</span></span> <span data-ttu-id="a1875-107">仮想化の詳細については、次を参照してください。 [Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)です。</span><span class="sxs-lookup"><span data-stu-id="a1875-107">For more information about virtualization, see [ClickOnce Deployment on Windows Vista](/visualstudio/deployment/clickonce-deployment-on-windows-vista).</span></span>  
  
 <span data-ttu-id="a1875-108">マニフェストの作成の詳細については、次を参照してください。 [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md)です。</span><span class="sxs-lookup"><span data-stu-id="a1875-108">For more information about manifest creation, see [-win32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/win32manifest.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1875-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1875-109">See Also</span></span>  
 [<span data-ttu-id="a1875-110">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a1875-110">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 <span data-ttu-id="a1875-111">[[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="a1875-111">[Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)</span></span>
