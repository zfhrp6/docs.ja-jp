---
title: "/codepage (Visual Basic) |Microsoft ドキュメント"
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
- /codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
caps.latest.revision: 17
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
ms.openlocfilehash: 6f4919bc4fc8eda700edbd80fead5b5d9fe0dba1
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="codepage-visual-basic"></a><span data-ttu-id="d3a66-102">/codepage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3a66-102">/codepage (Visual Basic)</span></span>
<span data-ttu-id="d3a66-103">コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="d3a66-103">Specifies the code page to use for all source-code files in the compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a66-104">構文</span><span class="sxs-lookup"><span data-stu-id="d3a66-104">Syntax</span></span>  
  
```  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="d3a66-105">引数</span><span class="sxs-lookup"><span data-stu-id="d3a66-105">Arguments</span></span>  
  
|<span data-ttu-id="d3a66-106">用語</span><span class="sxs-lookup"><span data-stu-id="d3a66-106">Term</span></span>|<span data-ttu-id="d3a66-107">定義</span><span class="sxs-lookup"><span data-stu-id="d3a66-107">Definition</span></span>|  
|---|---|  
|`id`|<span data-ttu-id="d3a66-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="d3a66-108">Required.</span></span> <span data-ttu-id="d3a66-109">コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。</span><span class="sxs-lookup"><span data-stu-id="d3a66-109">The compiler uses the code page specified by `id` to interpret the encoding of the source files.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3a66-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d3a66-110">Remarks</span></span>  
 <span data-ttu-id="d3a66-111">使用できる特定のエンコーディングで保存されたソース コードをコンパイルする`/codepage`を指定するコード ページを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3a66-111">To compile source code saved with a specific encoding, you can use `/codepage` to specify which code page should be used.</span></span> <span data-ttu-id="d3a66-112">`/codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d3a66-112">The `/codepage` option applies to all source-code files in your compilation.</span></span> <span data-ttu-id="d3a66-113">詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)します。</span><span class="sxs-lookup"><span data-stu-id="d3a66-113">For more information, see [Character Encoding in the .NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9).</span></span>  
  
 <span data-ttu-id="d3a66-114">`/codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルが保存された場合、オプションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d3a66-114">The `/codepage` option is not needed if the source-code files were saved using the current ANSI code page, Unicode, or UTF-8 with a signature.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="d3a66-115">他のエンコーディングを指定しない限り、既定では、現在の ANSI コード ページですべてのソース コード ファイルを保存、**エンコード** ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="d3a66-115"> saves all source-code files with the current ANSI code page by default, unless the user specifies another encoding in the **Encoding** dialog box.</span></span> [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]<span data-ttu-id="d3a66-116">使用して、**エンコード**異なるコード ページで保存されたソース コード ファイルを開く ダイアログ ボックス。</span><span class="sxs-lookup"><span data-stu-id="d3a66-116"> uses the **Encoding** dialog box to open source-code files saved with a different code page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3a66-117">`/codepage`内から使用可能オプションは、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]開発環境には、コマンドラインからコンパイルする場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="d3a66-117">The `/codepage` option is not available from within the [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a66-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3a66-118">See Also</span></span>  
 [<span data-ttu-id="d3a66-119">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="d3a66-119">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
