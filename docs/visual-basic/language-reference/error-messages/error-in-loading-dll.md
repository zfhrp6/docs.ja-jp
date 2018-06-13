---
title: DLL 読み込み時のエラーです。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584684"
---
# <a name="error-in-loading-dll-visual-basic"></a><span data-ttu-id="546c8-102">DLL 読み込み時のエラーです。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="546c8-102">Error in loading DLL (Visual Basic)</span></span>
<span data-ttu-id="546c8-103">ダイナミック リンク ライブラリ (DLL) で指定したライブラリは、`Lib`の句、`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="546c8-103">A dynamic-link library (DLL) is a library specified in the `Lib` clause of a `Declare` statement.</span></span> <span data-ttu-id="546c8-104">このエラーの考えられる原因は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="546c8-104">Possible causes for this error include:</span></span>  
  
-   <span data-ttu-id="546c8-105">ファイルは、DLL の実行可能ファイルではありません。</span><span class="sxs-lookup"><span data-stu-id="546c8-105">The file is not DLL executable.</span></span>  
  
-   <span data-ttu-id="546c8-106">ファイルは、Microsoft Windows DLL ではありません。</span><span class="sxs-lookup"><span data-stu-id="546c8-106">The file is not a Microsoft Windows DLL.</span></span>  
  
-   <span data-ttu-id="546c8-107">DLL が存在しない別の DLL を参照します。</span><span class="sxs-lookup"><span data-stu-id="546c8-107">The DLL references another DLL that is not present.</span></span>  
  
-   <span data-ttu-id="546c8-108">DLL または参照される DLL がパスに指定されたディレクトリではありません。</span><span class="sxs-lookup"><span data-stu-id="546c8-108">The DLL or referenced DLL is not in a directory specified in the path.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="546c8-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="546c8-109">To correct this error</span></span>  
  
-   <span data-ttu-id="546c8-110">ファイルが、ソース テキスト ファイルであり、DLL が実行可能の場合は、コンパイルされ、DLL の実行可能ファイルのフォームにリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="546c8-110">If the file is a source-text file and therefore not DLL executable, it must be compiled and linked to a DLL-executable form.</span></span>  
  
-   <span data-ttu-id="546c8-111">ファイルが Microsoft Windows DLL でない場合は、同等の Microsoft Windows を入手します。</span><span class="sxs-lookup"><span data-stu-id="546c8-111">If the file is not a Microsoft Windows DLL, obtain the Microsoft Windows equivalent.</span></span>  
  
-   <span data-ttu-id="546c8-112">DLL が存在しない別の DLL を参照する場合は、参照される DLL を入手して使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="546c8-112">If the DLL references another DLL that is not present, obtain the referenced DLL and make it available.</span></span>  
  
-   <span data-ttu-id="546c8-113">DLL または参照される DLL がパスで指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="546c8-113">If the DLL or referenced DLL is not in a directory specified by the path, move the DLL to a referenced directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="546c8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="546c8-114">See Also</span></span>  
 [<span data-ttu-id="546c8-115">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="546c8-115">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
