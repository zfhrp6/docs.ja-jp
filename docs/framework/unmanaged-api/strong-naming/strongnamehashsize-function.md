---
title: "StrongNameHashSize 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameHashSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameHashSize
helpviewer_keywords: StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: baf9c9b2219ff3fb784972b1f54a2b50dcd8657d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="548e8-102">StrongNameHashSize 関数</span><span class="sxs-lookup"><span data-stu-id="548e8-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="548e8-103">指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="548e8-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="548e8-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="548e8-104">This function has been deprecated.</span></span> <span data-ttu-id="548e8-105">使用して、 [iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="548e8-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="548e8-106">構文</span><span class="sxs-lookup"><span data-stu-id="548e8-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="548e8-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="548e8-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="548e8-108">[in]バッファー サイズを計算するために使用するハッシュ アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="548e8-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="548e8-109">[out]返されたバッファーのサイズ (バイト)。</span><span class="sxs-lookup"><span data-stu-id="548e8-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="548e8-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="548e8-110">Return Value</span></span>  
 <span data-ttu-id="548e8-111">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="548e8-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="548e8-112">コメント</span><span class="sxs-lookup"><span data-stu-id="548e8-112">Remarks</span></span>  
 <span data-ttu-id="548e8-113">場合、`StrongNameHashSize`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="548e8-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="548e8-114">要件</span><span class="sxs-lookup"><span data-stu-id="548e8-114">Requirements</span></span>  
 <span data-ttu-id="548e8-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="548e8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="548e8-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="548e8-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="548e8-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="548e8-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="548e8-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="548e8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="548e8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="548e8-119">See Also</span></span>  
 [<span data-ttu-id="548e8-120">StrongNameHashSize メソッド</span><span class="sxs-lookup"><span data-stu-id="548e8-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="548e8-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="548e8-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
