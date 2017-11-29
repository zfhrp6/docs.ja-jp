---
title: "#<a name=\"externalsource-directive\"></a>ExternalSource ディレクティブ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
caps.latest.revision: "160"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f90b838e50b65b8652cd9cf6f6ee084e9552f025
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="externalsource-directive"></a><span data-ttu-id="0fed4-102">#ExternalSource ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="0fed4-102">#ExternalSource Directive</span></span>
<span data-ttu-id="0fed4-103">特定のソース コード行と、ソースに外部のテキストの間のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="0fed4-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fed4-104">構文</span><span class="sxs-lookup"><span data-stu-id="0fed4-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="0fed4-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="0fed4-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="0fed4-106">外部ソースへのパス。</span><span class="sxs-lookup"><span data-stu-id="0fed4-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="0fed4-107">外部ソースの最初の行の行番号。</span><span class="sxs-lookup"><span data-stu-id="0fed4-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="0fed4-108">外部ソースでエラーが発生する行。</span><span class="sxs-lookup"><span data-stu-id="0fed4-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="0fed4-109">`#ExternalSource` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="0fed4-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fed4-110">コメント</span><span class="sxs-lookup"><span data-stu-id="0fed4-110">Remarks</span></span>  
 <span data-ttu-id="0fed4-111">このディレクティブは、コンパイラと、デバッガーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fed4-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="0fed4-112">ソース ファイルには、外部ソースのディレクティブには、特定のソース ファイル内のコード行と .aspx ファイルなどのソースに外部のテキストの間のマッピングを示しますが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0fed4-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="0fed4-113">指定されたソース コードでは、コンパイル時にエラーが発生する場合は、外部ソースからのものとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="0fed4-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="0fed4-114">外部ソース ディレクティブでは、コンパイルに影響を与えるありません、入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0fed4-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="0fed4-115">内部使用のみアプリケーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0fed4-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fed4-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fed4-116">See Also</span></span>  
 [<span data-ttu-id="0fed4-117">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="0fed4-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
