---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a><span data-ttu-id="a7273-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7273-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="a7273-103">コンパイル時に著作権画面を表示および情報メッセージの表示を抑制します。</span><span class="sxs-lookup"><span data-stu-id="a7273-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7273-104">構文</span><span class="sxs-lookup"><span data-stu-id="a7273-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="a7273-105">コメント</span><span class="sxs-lookup"><span data-stu-id="a7273-105">Remarks</span></span>  
 <span data-ttu-id="a7273-106">指定した場合`/nologo`コンパイラでは、著作権の見出しは表示されません。</span><span class="sxs-lookup"><span data-stu-id="a7273-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="a7273-107">既定では、`/nologo` は無効です。</span><span class="sxs-lookup"><span data-stu-id="a7273-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7273-108">`/nologo`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="a7273-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7273-109">例</span><span class="sxs-lookup"><span data-stu-id="a7273-109">Example</span></span>  
 <span data-ttu-id="a7273-110">次のコードのコンパイル`T2.vb`著作権の見出しは表示されません。</span><span class="sxs-lookup"><span data-stu-id="a7273-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7273-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7273-111">See Also</span></span>  
 [<span data-ttu-id="a7273-112">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="a7273-112">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a7273-113">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="a7273-113">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
