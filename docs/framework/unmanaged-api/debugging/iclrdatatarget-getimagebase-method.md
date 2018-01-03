---
title: "ICLRDataTarget::GetImageBase メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetImageBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 504c3ce7115cbab11d0510eaa2ebb0fdd9f1888b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="cfb9c-102">ICLRDataTarget::GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="cfb9c-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="cfb9c-103">指定されたイメージのメモリのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfb9c-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfb9c-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cfb9c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfb9c-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="cfb9c-106">[in]パスを含む、画像のファイル名。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="cfb9c-107">[out]イメージのベース アドレスを格納する CLRDATA_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfb9c-108">コメント</span><span class="sxs-lookup"><span data-stu-id="cfb9c-108">Remarks</span></span>  
 <span data-ttu-id="cfb9c-109">イメージ ファイル名では、可能性がありますか、パスがない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="cfb9c-110">パスを指定すると、一致するに対してが実行全体のパスです。それ以外の場合、照合は、ファイル名にのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfb9c-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="cfb9c-111">Requirements</span></span>  
 <span data-ttu-id="cfb9c-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="cfb9c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfb9c-113">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cfb9c-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cfb9c-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfb9c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfb9c-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfb9c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfb9c-116">参照</span><span class="sxs-lookup"><span data-stu-id="cfb9c-116">See Also</span></span>  
 [<span data-ttu-id="cfb9c-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cfb9c-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
