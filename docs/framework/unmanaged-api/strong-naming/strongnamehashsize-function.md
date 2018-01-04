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
ms.workload: dotnet
ms.openlocfilehash: 20a0d5fc284dde7b127f1f177a448a95701ac8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamehashsize-function"></a><span data-ttu-id="73041-102">StrongNameHashSize 関数</span><span class="sxs-lookup"><span data-stu-id="73041-102">StrongNameHashSize Function</span></span>
<span data-ttu-id="73041-103">指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="73041-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="73041-104">この関数は廃止されました。</span><span class="sxs-lookup"><span data-stu-id="73041-104">This function has been deprecated.</span></span> <span data-ttu-id="73041-105">使用して、 [iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)メソッド代わりにします。</span><span class="sxs-lookup"><span data-stu-id="73041-105">Use the [ICLRStrongName::StrongNameHashSize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73041-106">構文</span><span class="sxs-lookup"><span data-stu-id="73041-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73041-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="73041-107">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="73041-108">[in]バッファー サイズを計算するために使用するハッシュ アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="73041-108">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="73041-109">[out]返されたバッファーのサイズ (バイト)。</span><span class="sxs-lookup"><span data-stu-id="73041-109">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73041-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="73041-110">Return Value</span></span>  
 <span data-ttu-id="73041-111">`true`正常に終了します。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="73041-111">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73041-112">コメント</span><span class="sxs-lookup"><span data-stu-id="73041-112">Remarks</span></span>  
 <span data-ttu-id="73041-113">場合、`StrongNameHashSize`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。</span><span class="sxs-lookup"><span data-stu-id="73041-113">If the `StrongNameHashSize` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73041-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="73041-114">Requirements</span></span>  
 <span data-ttu-id="73041-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="73041-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73041-116">**ヘッダー:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="73041-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="73041-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="73041-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="73041-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73041-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73041-119">参照</span><span class="sxs-lookup"><span data-stu-id="73041-119">See Also</span></span>  
 [<span data-ttu-id="73041-120">StrongNameHashSize メソッド</span><span class="sxs-lookup"><span data-stu-id="73041-120">StrongNameHashSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [<span data-ttu-id="73041-121">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="73041-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
