---
title: "/langversion (Visual Basic) |Microsoft ドキュメント"
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
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
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
ms.openlocfilehash: 56411df907bd5ff0416e6d0539cbe46df3b34947
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="langversion-visual-basic"></a><span data-ttu-id="ba7f5-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba7f5-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="ba7f5-103">コンパイラが指定された Visual Basic の言語バージョンに含まれている構文のみを受け入れるようにします。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba7f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba7f5-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba7f5-105">引数</span><span class="sxs-lookup"><span data-stu-id="ba7f5-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="ba7f5-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-106">Required.</span></span> <span data-ttu-id="ba7f5-107">コンパイル時に使用する言語バージョン。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="ba7f5-108">許容値は`9`、 `9.0`、 `10`、および`10.0`です。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba7f5-109">コメント</span><span class="sxs-lookup"><span data-stu-id="ba7f5-109">Remarks</span></span>  
 <span data-ttu-id="ba7f5-110">`/langversion`オプションは、コンパイラはどのような構文を指定します。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="ba7f5-111">たとえば、9.0 インストールされている言語バージョンを指定する場合、コンパイラは、バージョン 10.0 でのみ有効ですし、後では、構文のエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="ba7f5-112">.NET Framework の異なるバージョンを対象のアプリケーションを開発する場合は、このオプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="ba7f5-113">たとえば、.NET Framework 3.5 を対象とする場合は、言語バージョン 10.0 から構文を使用しないことを確認するこのオプションを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="ba7f5-114">設定する`/langversion`直接、コマンドラインを使用してのみです。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="ba7f5-115">詳細については、「[対象となる特定の .NET Framework のバージョンの指定](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-115">For more information, see [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba7f5-116">例</span><span class="sxs-lookup"><span data-stu-id="ba7f5-116">Example</span></span>  
 <span data-ttu-id="ba7f5-117">次のコードのコンパイル`sample.vb`Visual Basic 9.0 のです。</span><span class="sxs-lookup"><span data-stu-id="ba7f5-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba7f5-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba7f5-118">See Also</span></span>  
 <span data-ttu-id="ba7f5-119">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="ba7f5-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="ba7f5-120"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="ba7f5-120"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="ba7f5-121"> [対象となる特定の .NET Framework バージョンの指定](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span><span class="sxs-lookup"><span data-stu-id="ba7f5-121"> [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span></span>
