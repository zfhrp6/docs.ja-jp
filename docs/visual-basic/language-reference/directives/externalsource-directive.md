---
title: '#ExternalSource ディレクティブ'
ms.date: 07/20/2015
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586592"
---
# <a name="externalsource-directive"></a><span data-ttu-id="4239c-102">#ExternalSource ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="4239c-102">#ExternalSource Directive</span></span>
<span data-ttu-id="4239c-103">特定のソース コード行と、ソースに外部のテキストの間のマッピングを示します。</span><span class="sxs-lookup"><span data-stu-id="4239c-103">Indicates a mapping between specific lines of source code and text external to the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4239c-104">構文</span><span class="sxs-lookup"><span data-stu-id="4239c-104">Syntax</span></span>  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a><span data-ttu-id="4239c-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="4239c-105">Parts</span></span>  
 `StringLiteral`  
 <span data-ttu-id="4239c-106">外部ソースへのパス。</span><span class="sxs-lookup"><span data-stu-id="4239c-106">The path to the external source.</span></span>  
  
 `IntLiteral`  
 <span data-ttu-id="4239c-107">外部ソースの最初の行の行番号。</span><span class="sxs-lookup"><span data-stu-id="4239c-107">The line number of the first line of the external source.</span></span>  
  
 `LogicalLine`  
 <span data-ttu-id="4239c-108">外部ソースでエラーが発生する行。</span><span class="sxs-lookup"><span data-stu-id="4239c-108">The line where the error occurs in the external source.</span></span>  
  
 `#End ExternalSource`  
 <span data-ttu-id="4239c-109">`#ExternalSource` ブロックを終了します。</span><span class="sxs-lookup"><span data-stu-id="4239c-109">Terminates the `#ExternalSource` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4239c-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4239c-110">Remarks</span></span>  
 <span data-ttu-id="4239c-111">このディレクティブは、コンパイラと、デバッガーでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="4239c-111">This directive is used only by the compiler and the debugger.</span></span>  
  
 <span data-ttu-id="4239c-112">ソース ファイルには、外部ソースのディレクティブには、特定のソース ファイル内のコード行と .aspx ファイルなどのソースに外部のテキストの間のマッピングを示しますが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4239c-112">A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file.</span></span> <span data-ttu-id="4239c-113">指定されたソース コードでは、コンパイル時にエラーが発生する場合は、外部ソースからのものとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="4239c-113">If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.</span></span>  
  
 <span data-ttu-id="4239c-114">外部ソース ディレクティブでは、コンパイルに影響を与えるありません、入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="4239c-114">External source directives have no effect on compilation and cannot be nested.</span></span> <span data-ttu-id="4239c-115">内部使用のみアプリケーションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4239c-115">They are intended for internal use by the application only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4239c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4239c-116">See Also</span></span>  
 [<span data-ttu-id="4239c-117">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="4239c-117">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
