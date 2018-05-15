---
title: ICLRMetadataLocator::GetMetadata メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="4e0ed-102">ICLRMetadataLocator::GetMetadata メソッド</span><span class="sxs-lookup"><span data-stu-id="4e0ed-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="4e0ed-103">イメージのメタデータを取得する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e0ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e0ed-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e0ed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e0ed-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="4e0ed-106">[in]イメージ ファイルのパスを指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="4e0ed-107">[in]イメージ ファイルのタイムスタンプ。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="4e0ed-108">[in]イメージ ファイルのサイズ。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="4e0ed-109">[in]イメージのグローバルに一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="4e0ed-110">[in]メタデータの相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="4e0ed-111">イメージのベース アドレスに対する相対パス、アドレスです。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="4e0ed-112">[in]将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="4e0ed-113">[in]メタデータを格納するバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4e0ed-114">[out]メタデータを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="4e0ed-115">[out]返されるメタデータのサイズ。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e0ed-116">コメント</span><span class="sxs-lookup"><span data-stu-id="4e0ed-116">Remarks</span></span>  
 <span data-ttu-id="4e0ed-117">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e0ed-118">要件</span><span class="sxs-lookup"><span data-stu-id="4e0ed-118">Requirements</span></span>  
 <span data-ttu-id="4e0ed-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4e0ed-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e0ed-120">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4e0ed-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4e0ed-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e0ed-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e0ed-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e0ed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e0ed-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e0ed-123">See Also</span></span>  
 [<span data-ttu-id="4e0ed-124">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e0ed-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
