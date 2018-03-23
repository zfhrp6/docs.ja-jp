---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="fb06b-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb06b-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="fb06b-103">コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb06b-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb06b-104">構文</span><span class="sxs-lookup"><span data-stu-id="fb06b-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="fb06b-105">引数</span><span class="sxs-lookup"><span data-stu-id="fb06b-105">Arguments</span></span>  
  
|<span data-ttu-id="fb06b-106">用語</span><span class="sxs-lookup"><span data-stu-id="fb06b-106">Term</span></span>|<span data-ttu-id="fb06b-107">定義</span><span class="sxs-lookup"><span data-stu-id="fb06b-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="fb06b-108">必須。</span><span class="sxs-lookup"><span data-stu-id="fb06b-108">Required.</span></span> <span data-ttu-id="fb06b-109">コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。</span><span class="sxs-lookup"><span data-stu-id="fb06b-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb06b-110">コメント</span><span class="sxs-lookup"><span data-stu-id="fb06b-110">Remarks</span></span>  
 <span data-ttu-id="fb06b-111">使用することができます、特定のエンコードで保存されたソース コードをコンパイルする`-codepage`するコード ページを使用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb06b-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="fb06b-112">`-codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="fb06b-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="fb06b-113">詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)です。</span><span class="sxs-lookup"><span data-stu-id="fb06b-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="fb06b-114">`-codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルを保存した場合、オプションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fb06b-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="fb06b-115"> ユーザーで他のエンコーディングを指定しない限りは、既定では、現在の ANSI コード ページですべてのソース コード ファイルを保存、**エンコード** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="fb06b-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="fb06b-116"> 使用して、**エンコード** ダイアログ ボックスを開くにはソース コード ファイルを別のコード ページを保存します。</span><span class="sxs-lookup"><span data-stu-id="fb06b-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb06b-117">`-codepage`オプションは内から使用できません、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開発環境は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="fb06b-117">The `-codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb06b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb06b-118">See Also</span></span>  
 [<span data-ttu-id="fb06b-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="fb06b-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
