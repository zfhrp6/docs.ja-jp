---
title: NukeDownloadedCache 関数
ms.date: 03/30/2017
api_name:
- NukeDownloadedCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- NukeDownloadedCache
helpviewer_keywords:
- NukeDownloadedCache function [.NET Framework fusion]
ms.assetid: fac2b1c6-6fa3-4818-805b-b63972024c86
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0436991512713c05e60a3c10d6fbdaa17bb378c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429828"
---
# <a name="nukedownloadedcache-function"></a><span data-ttu-id="59c7b-102">NukeDownloadedCache 関数</span><span class="sxs-lookup"><span data-stu-id="59c7b-102">NukeDownloadedCache Function</span></span>
<span data-ttu-id="59c7b-103">共通言語ランタイム (CLR) のダウンロード キャッシュを削除します。</span><span class="sxs-lookup"><span data-stu-id="59c7b-103">Deletes the common language runtime (CLR) download cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="59c7b-104">Syntax</span></span>  
  
```  
HRESULT NukeDownloadedCache();  
```  
  
## <a name="return-value"></a><span data-ttu-id="59c7b-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="59c7b-105">Return Value</span></span>  
 <span data-ttu-id="59c7b-106">このメソッドは、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="59c7b-106">This method returns standard COM error codes, as defined in WinError.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59c7b-107">コメント</span><span class="sxs-lookup"><span data-stu-id="59c7b-107">Remarks</span></span>  
 <span data-ttu-id="59c7b-108">CLR ダウンロード キャッシュは、再利用できる場合、URL からダウンロードされている厳密な名前のアセンブリが格納領域です。</span><span class="sxs-lookup"><span data-stu-id="59c7b-108">The CLR download cache is the area where strong-named assemblies that are downloaded from a URL are stored for possible reuse.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c7b-109">要件</span><span class="sxs-lookup"><span data-stu-id="59c7b-109">Requirements</span></span>  
 <span data-ttu-id="59c7b-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="59c7b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c7b-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="59c7b-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="59c7b-112">**ライブラリ:** Fusion.dll と Mscorwks.dll です。</span><span class="sxs-lookup"><span data-stu-id="59c7b-112">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="59c7b-113">Mscorwks.dll の代わりに Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="59c7b-113">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="59c7b-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c7b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c7b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="59c7b-115">See Also</span></span>  
 [<span data-ttu-id="59c7b-116">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="59c7b-116">CreateHistoryReader Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 [<span data-ttu-id="59c7b-117">GetHistoryFileDirectory 関数</span><span class="sxs-lookup"><span data-stu-id="59c7b-117">GetHistoryFileDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 [<span data-ttu-id="59c7b-118">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="59c7b-118">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
