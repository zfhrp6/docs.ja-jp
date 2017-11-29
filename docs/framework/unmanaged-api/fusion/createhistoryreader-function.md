---
title: "CreateHistoryReader 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateHistoryReader
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateHistoryReader
helpviewer_keywords: CreateHistoryReader function [.NET Framework fusion]
ms.assetid: 66a89acf-8c32-44c0-8787-960c99c7b3ec
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4f4b09f592a27b7d3d25b2dbe13be7e261023bf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="createhistoryreader-function"></a><span data-ttu-id="5187e-102">CreateHistoryReader 関数</span><span class="sxs-lookup"><span data-stu-id="5187e-102">CreateHistoryReader Function</span></span>
<span data-ttu-id="5187e-103">指定したファイルの履歴のリーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="5187e-103">Creates a history reader for the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5187e-104">構文</span><span class="sxs-lookup"><span data-stu-id="5187e-104">Syntax</span></span>  
  
```  
HRESULT CreateHistoryReader (  
    [in]  LPCWSTR        wzFilePath,  
    [out] IHistoryReader **ppHistoryReader  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5187e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5187e-105">Parameters</span></span>  
 `wzFilePath`  
 <span data-ttu-id="5187e-106">[in]ファイルのパス。</span><span class="sxs-lookup"><span data-stu-id="5187e-106">[in] The file path.</span></span>  
  
 `ppHistoryReader`  
 <span data-ttu-id="5187e-107">[out]正常に完了すると、履歴リーダーへのポインターを格納します。</span><span class="sxs-lookup"><span data-stu-id="5187e-107">[out] On successful completion, contains a pointer to the history reader.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5187e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5187e-108">Return Value</span></span>  
 <span data-ttu-id="5187e-109">このメソッドは、次の表で説明する値に加えて、WinError.h で定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="5187e-109">This method returns standard COM error codes as defined in WinError.h, in addition to the values described in the following table.</span></span>  
  
|<span data-ttu-id="5187e-110">リターン コード</span><span class="sxs-lookup"><span data-stu-id="5187e-110">Return code</span></span>|<span data-ttu-id="5187e-111">説明</span><span class="sxs-lookup"><span data-stu-id="5187e-111">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="5187e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="5187e-112">S_OK</span></span>|<span data-ttu-id="5187e-113">メソッドが正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5187e-113">Indicates that the method completed successfully.</span></span>|  
|<span data-ttu-id="5187e-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="5187e-114">E_INVALIDARG</span></span>|<span data-ttu-id="5187e-115">示します`wzFilePath`または`ppHistoryReader`の参照を null に設定されます。</span><span class="sxs-lookup"><span data-stu-id="5187e-115">Indicates that `wzFilePath` or `ppHistoryReader` are set to a null reference.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5187e-116">要件</span><span class="sxs-lookup"><span data-stu-id="5187e-116">Requirements</span></span>  
 <span data-ttu-id="5187e-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5187e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5187e-118">**ライブラリ:** Fusion.dll</span><span class="sxs-lookup"><span data-stu-id="5187e-118">**Library:** Fusion.dll</span></span>  
  
 <span data-ttu-id="5187e-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5187e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5187e-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5187e-120">See Also</span></span>  
 [<span data-ttu-id="5187e-121">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="5187e-121">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
