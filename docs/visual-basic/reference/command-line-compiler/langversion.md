---
title: /langversion (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cfe91588471cc8410b25addea8d66a0388c9c5be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="langversion-visual-basic"></a><span data-ttu-id="9b0f7-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0f7-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="9b0f7-103">指定された Visual Basic 言語バージョンに含まれている構文のみを受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b0f7-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b0f7-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b0f7-105">引数</span><span class="sxs-lookup"><span data-stu-id="9b0f7-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="9b0f7-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-106">Required.</span></span> <span data-ttu-id="9b0f7-107">コンパイル時に使用する言語バージョン。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="9b0f7-108">指定できる値は`9`、 `9.0`、 `10`、および`10.0`です。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0f7-109">コメント</span><span class="sxs-lookup"><span data-stu-id="9b0f7-109">Remarks</span></span>  
 <span data-ttu-id="9b0f7-110">`/langversion`オプションは、コンパイラを受け入れるどのような構文を指定します。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="9b0f7-111">たとえば、言語バージョンを 9.0 を指定する場合、コンパイラは、バージョン 10.0 でのみ有効であり、それ以降は、構文エラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="9b0f7-112">.NET Framework の異なるバージョンを対象のアプリケーションを開発する場合は、このオプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="9b0f7-113">たとえば、.NET Framework 3.5 を対象とする場合は、言語バージョン 10.0 から構文を使用しないことを確認するこのオプションを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="9b0f7-114">設定することができます`/langversion`直接コマンドラインを使用してのみです。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="9b0f7-115">詳細については、「[対象となる特定の .NET Framework のバージョンの指定](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-115">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b0f7-116">例</span><span class="sxs-lookup"><span data-stu-id="9b0f7-116">Example</span></span>  
 <span data-ttu-id="9b0f7-117">次のコードのコンパイル`sample.vb`Visual Basic 9.0 のです。</span><span class="sxs-lookup"><span data-stu-id="9b0f7-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b0f7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b0f7-118">See Also</span></span>  
 [<span data-ttu-id="9b0f7-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="9b0f7-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9b0f7-120">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="9b0f7-120">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="9b0f7-121">対象となる特定の .NET Framework バージョンの指定</span><span class="sxs-lookup"><span data-stu-id="9b0f7-121">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
