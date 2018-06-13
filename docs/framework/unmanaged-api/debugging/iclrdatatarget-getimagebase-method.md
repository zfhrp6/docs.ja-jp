---
title: ICLRDataTarget::GetImageBase メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a79133b117f3a718dd84af6c2144a6098bc79f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407239"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="5f933-102">ICLRDataTarget::GetImageBase メソッド</span><span class="sxs-lookup"><span data-stu-id="5f933-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="5f933-103">指定されたイメージのメモリのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5f933-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f933-104">構文</span><span class="sxs-lookup"><span data-stu-id="5f933-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5f933-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f933-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="5f933-106">[in]パスを含む、画像のファイル名。</span><span class="sxs-lookup"><span data-stu-id="5f933-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="5f933-107">[out]イメージのベース アドレスを格納する CLRDATA_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5f933-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f933-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5f933-108">Remarks</span></span>  
 <span data-ttu-id="5f933-109">イメージ ファイル名では、可能性がありますか、パスがない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5f933-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="5f933-110">パスを指定すると、一致するに対してが実行全体のパスです。それ以外の場合、照合は、ファイル名にのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="5f933-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f933-111">要件</span><span class="sxs-lookup"><span data-stu-id="5f933-111">Requirements</span></span>  
 <span data-ttu-id="5f933-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5f933-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f933-113">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5f933-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5f933-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f933-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f933-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f933-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f933-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f933-116">See Also</span></span>  
 [<span data-ttu-id="5f933-117">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f933-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
