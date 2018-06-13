---
title: クリップボードの形式が有効ではありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
ms.openlocfilehash: eef16096b269902dbaca6a344abf4c5f6a504fb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586222"
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="742ef-102">クリップボードの形式が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="742ef-102">Clipboard format is not valid</span></span>
<span data-ttu-id="742ef-103">指定されたクリップボードの形式は、実行中のメソッドと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="742ef-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="742ef-104">このエラーの考えられる原因には。</span><span class="sxs-lookup"><span data-stu-id="742ef-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="742ef-105">クリップボードを使用して`GetText`または`SetText`メソッド以外のクリップボード形式を`vbCFText`または`vbCFLink`です。</span><span class="sxs-lookup"><span data-stu-id="742ef-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="742ef-106">クリップボードを使用して`GetData`または`SetData`メソッド以外のクリップボード形式を`vbCFBitmap`、 `vbCFDIB`、または`vbCFMetafile`です。</span><span class="sxs-lookup"><span data-stu-id="742ef-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="742ef-107">使用して、`DataObject``GetData`メソッドまたは`SetData`登録されている形式 (& HC000 - & HFFFF)、Microsoft Windows によって予約されている範囲内でのクリップボード形式を持つメソッドとそのクリップボードの形式が登録されていない Microsoft Windows と一緒にします。</span><span class="sxs-lookup"><span data-stu-id="742ef-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="742ef-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="742ef-108">To correct this error</span></span>  
  
-   <span data-ttu-id="742ef-109">無効な形式を削除し、有効なものを指定します。</span><span class="sxs-lookup"><span data-stu-id="742ef-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742ef-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="742ef-110">See Also</span></span>  
 [<span data-ttu-id="742ef-111">クリップボード: その他のデータ形式の追加</span><span class="sxs-lookup"><span data-stu-id="742ef-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
