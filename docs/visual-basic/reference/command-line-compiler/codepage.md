---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="-codepage-visual-basic"></a><span data-ttu-id="85797-102">-codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85797-102">-codepage (Visual Basic)</span></span>
<span data-ttu-id="85797-103">コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="85797-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85797-104">構文</span><span class="sxs-lookup"><span data-stu-id="85797-104">Syntax</span></span>  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="85797-105">引数</span><span class="sxs-lookup"><span data-stu-id="85797-105">Arguments</span></span>  
  
|<span data-ttu-id="85797-106">用語</span><span class="sxs-lookup"><span data-stu-id="85797-106">Term</span></span>|<span data-ttu-id="85797-107">定義</span><span class="sxs-lookup"><span data-stu-id="85797-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="85797-108">必須。</span><span class="sxs-lookup"><span data-stu-id="85797-108">Required.</span></span> <span data-ttu-id="85797-109">コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。</span><span class="sxs-lookup"><span data-stu-id="85797-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85797-110">コメント</span><span class="sxs-lookup"><span data-stu-id="85797-110">Remarks</span></span>  
 <span data-ttu-id="85797-111">使用することができます、特定のエンコードで保存されたソース コードをコンパイルする`-codepage`するコード ページを使用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="85797-111">To compile source code saved with a specific encoding, you can use `-codepage` to specify which code page should be used.</span></span> <span data-ttu-id="85797-112">`-codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="85797-112">The `-codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="85797-113">詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)です。</span><span class="sxs-lookup"><span data-stu-id="85797-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="85797-114">`-codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルを保存した場合、オプションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="85797-114">The `-codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> <span data-ttu-id="85797-115">Visual Studio に保存既定では、すべてのソース コード ファイルが現在の ANSI コード ページで、ユーザーで他のエンコーディングを指定しない限り、**エンコード** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="85797-115">Visual Studio saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> <span data-ttu-id="85797-116">Visual Studio を使用して、**エンコード** ダイアログ ボックスを開くにはソース コード ファイルを別のコード ページを保存します。</span><span class="sxs-lookup"><span data-stu-id="85797-116">Visual Studio uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85797-117">`-codepage`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="85797-117">The `-codepage` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85797-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="85797-118">See Also</span></span>  
 [<span data-ttu-id="85797-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="85797-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
