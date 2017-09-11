---
title: "/nologo (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners, suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: fe03c36f46717248269c9aaec13b40569161b0e0
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="nologo-visual-basic"></a><span data-ttu-id="e4c68-102">/nologo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e4c68-102">/nologo (Visual Basic)</span></span>
<span data-ttu-id="e4c68-103">コンパイル時に著作権画面を表示および情報メッセージの表示を抑制します。</span><span class="sxs-lookup"><span data-stu-id="e4c68-103">Suppresses display of the copyright banner and informational messages during compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c68-104">構文</span><span class="sxs-lookup"><span data-stu-id="e4c68-104">Syntax</span></span>  
  
```  
/nologo  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4c68-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e4c68-105">Remarks</span></span>  
 <span data-ttu-id="e4c68-106">指定した場合`/nologo`コンパイラでは、著作権画面は表示されません。</span><span class="sxs-lookup"><span data-stu-id="e4c68-106">If you specify `/nologo`, the compiler does not display a copyright banner.</span></span> <span data-ttu-id="e4c68-107">既定では、`/nologo` は無効です。</span><span class="sxs-lookup"><span data-stu-id="e4c68-107">By default, `/nologo` is not in effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4c68-108">`/nologo`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="e4c68-108">The `/nologo` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4c68-109">例</span><span class="sxs-lookup"><span data-stu-id="e4c68-109">Example</span></span>  
 <span data-ttu-id="e4c68-110">次のコードのコンパイル`T2.vb`著作権バナーに表示されていません。</span><span class="sxs-lookup"><span data-stu-id="e4c68-110">The following code compiles `T2.vb` and does not display a copyright banner.</span></span>  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4c68-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4c68-111">See Also</span></span>  
 <span data-ttu-id="e4c68-112">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="e4c68-112">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="e4c68-113"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="e4c68-113"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
