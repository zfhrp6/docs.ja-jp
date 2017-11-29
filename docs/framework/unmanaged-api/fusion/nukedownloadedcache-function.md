---
title: "NukeDownloadedCache 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type: DLLExport
f1_keywords: NukeDownloadedCache
helpviewer_keywords: NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ff24cf46ab24fe94ab19cee04d9e32ed1a34b53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="90118-102">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="90118-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="90118-103">共通言語ランタイム (CLR) のダウンロード キャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="90118-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90118-104">構文</span><span class="sxs-lookup"><span data-stu-id="90118-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="90118-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="90118-105">Return Value</span></span>  
 <span data-ttu-id="90118-106">このメソッドは、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="90118-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90118-107">コメント</span><span class="sxs-lookup"><span data-stu-id="90118-107">Remarks</span></span>  
 <span data-ttu-id="90118-108">CLR ダウンロード キャッシュは、再利用できる場合、URL からダウンロードされている厳密な名前のアセンブリが格納領域です。</span><span class="sxs-lookup"><span data-stu-id="90118-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90118-109">要件</span><span class="sxs-lookup"><span data-stu-id="90118-109">Requirements</span></span>  
 <span data-ttu-id="90118-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="90118-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90118-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="90118-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="90118-112">**ライブラリ:** Fusion.dll と Mscorwks.dll です。</span><span class="sxs-lookup"><span data-stu-id="90118-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="90118-113">Mscorwks.dll の代わりに Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="90118-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="90118-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90118-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90118-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="90118-115">See Also</span></span>  
 [<span data-ttu-id="90118-116">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="90118-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="90118-117">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="90118-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="90118-118">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="90118-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
