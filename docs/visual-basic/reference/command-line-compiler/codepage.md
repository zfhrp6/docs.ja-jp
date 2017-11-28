---
title: /codepage (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 609373ed0e58eec86a703f33d48d31e27b0b7e3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="codepage-visual-basic"></a><span data-ttu-id="8338d-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8338d-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="8338d-103">コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="8338d-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8338d-104">構文</span><span class="sxs-lookup"><span data-stu-id="8338d-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="8338d-105">引数</span><span class="sxs-lookup"><span data-stu-id="8338d-105">Arguments</span></span>  
  
|<span data-ttu-id="8338d-106">用語</span><span class="sxs-lookup"><span data-stu-id="8338d-106">Term</span></span>|<span data-ttu-id="8338d-107">定義</span><span class="sxs-lookup"><span data-stu-id="8338d-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="8338d-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="8338d-108">Required.</span></span> <span data-ttu-id="8338d-109">コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。</span><span class="sxs-lookup"><span data-stu-id="8338d-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8338d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="8338d-110">Remarks</span></span>  
 <span data-ttu-id="8338d-111">使用することができます、特定のエンコードで保存されたソース コードをコンパイルする`/codepage`するコード ページを使用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="8338d-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="8338d-112">`/codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8338d-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="8338d-113">詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)です。</span><span class="sxs-lookup"><span data-stu-id="8338d-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="8338d-114">`/codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルを保存した場合、オプションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8338d-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="8338d-115">ユーザーで他のエンコーディングを指定しない限りは、既定では、現在の ANSI コード ページですべてのソース コード ファイルを保存、**エンコード** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="8338d-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]<span data-ttu-id="8338d-116">使用して、**エンコード** ダイアログ ボックスを開くにはソース コード ファイルを別のコード ページを保存します。</span><span class="sxs-lookup"><span data-stu-id="8338d-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8338d-117">`/codepage`オプションは内から使用できません、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開発環境は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="8338d-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8338d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8338d-118">See Also</span></span>  
 [<span data-ttu-id="8338d-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="8338d-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
