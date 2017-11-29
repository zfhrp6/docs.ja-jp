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
ms.openlocfilehash: 1d397995266d6063164510a4b563ba94f7f54950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="131ec-102">ICLRDataTarget::GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="131ec-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="131ec-103">指定されたイメージのメモリのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="131ec-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="131ec-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="131ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="131ec-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="131ec-106">[in]パスを含む、画像のファイル名。</span><span class="sxs-lookup"><span data-stu-id="131ec-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="131ec-107">[out]イメージのベース アドレスを格納する CLRDATA_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="131ec-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="131ec-108">コメント</span><span class="sxs-lookup"><span data-stu-id="131ec-108">Remarks</span></span>  
 <span data-ttu-id="131ec-109">イメージ ファイル名では、可能性がありますか、パスがない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="131ec-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="131ec-110">パスを指定すると、一致するに対してが実行全体のパスです。それ以外の場合、照合は、ファイル名にのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="131ec-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131ec-111">要件</span><span class="sxs-lookup"><span data-stu-id="131ec-111">Requirements</span></span>  
 <span data-ttu-id="131ec-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="131ec-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="131ec-113">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="131ec-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="131ec-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="131ec-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="131ec-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="131ec-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131ec-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="131ec-116">See Also</span></span>  
 [<span data-ttu-id="131ec-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="131ec-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
