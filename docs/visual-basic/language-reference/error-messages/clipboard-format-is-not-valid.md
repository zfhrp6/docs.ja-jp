---
title: "クリップボードの形式が有効ではありません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a><span data-ttu-id="c9a8d-102">クリップボードの形式が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-102">Clipboard format is not valid</span></span>
<span data-ttu-id="c9a8d-103">指定されたクリップボードの形式は、実行中のメソッドと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-103">The specified Clipboard format is incompatible with the method being executed.</span></span> <span data-ttu-id="c9a8d-104">このエラーの考えられる原因には。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="c9a8d-105">クリップボードを使用して`GetText`または`SetText`メソッド以外のクリップボード形式を`vbCFText`または`vbCFLink`です。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-105">Using the Clipboard's `GetText` or `SetText` method with a Clipboard format other than `vbCFText` or `vbCFLink`.</span></span>  
  
-   <span data-ttu-id="c9a8d-106">クリップボードを使用して`GetData`または`SetData`メソッド以外のクリップボード形式を`vbCFBitmap`、 `vbCFDIB`、または`vbCFMetafile`です。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-106">Using the Clipboard's `GetData` or `SetData` method with a Clipboard format other than `vbCFBitmap`, `vbCFDIB`, or `vbCFMetafile`.</span></span>  
  
-   <span data-ttu-id="c9a8d-107">使用して、`DataObject``GetData`メソッドまたは`SetData`登録されている形式 (& HC000 - & HFFFF)、Microsoft Windows によって予約されている範囲内でのクリップボード形式を持つメソッドとそのクリップボードの形式が登録されていない Microsoft Windows と一緒にします。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-107">Using the `DataObject``GetData` method or `SetData` method with a Clipboard format in the range reserved by Microsoft Windows for registered formats (&HC000-&HFFFF), when that Clipboard format has not been registered with Microsoft Windows.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9a8d-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c9a8d-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c9a8d-109">無効な形式を削除し、有効なものを指定します。</span><span class="sxs-lookup"><span data-stu-id="c9a8d-109">Remove the invalid format and specify a valid one.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9a8d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9a8d-110">See Also</span></span>  
 [<span data-ttu-id="c9a8d-111">クリップボード: その他のデータ形式の追加</span><span class="sxs-lookup"><span data-stu-id="c9a8d-111">Clipboard: Adding Other Formats</span></span>](/cpp/mfc/clipboard-adding-other-formats)
