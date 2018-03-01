---
title: "ICLRStrongName::StrongNameSignatureSize メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a961cca6bba24ac8a2428a20c616a2ee074b8abf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="48d3f-102">ICLRStrongName::StrongNameSignatureSize メソッド</span><span class="sxs-lookup"><span data-stu-id="48d3f-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="48d3f-103">厳密な名前の署名のサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="48d3f-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="48d3f-104">このメソッドは遅延署名アセンブリを作成するときに、ファイルに予約する領域の量を決定するコンパイラで通常使用されます。</span><span class="sxs-lookup"><span data-stu-id="48d3f-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48d3f-105">構文</span><span class="sxs-lookup"><span data-stu-id="48d3f-105">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="48d3f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="48d3f-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="48d3f-107">[in]型の構造体[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)厳密な名前の署名を生成するためのキー ペアの公開部分を格納しています。</span><span class="sxs-lookup"><span data-stu-id="48d3f-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="48d3f-108">[in]サイズをバイト単位での`pbPublicKeyBlob`します。</span><span class="sxs-lookup"><span data-stu-id="48d3f-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="48d3f-109">[in]厳密な名前の署名を格納するために必要なバイト数。</span><span class="sxs-lookup"><span data-stu-id="48d3f-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48d3f-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="48d3f-110">Return Value</span></span>  
 <span data-ttu-id="48d3f-111">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="48d3f-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48d3f-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="48d3f-112">Requirements</span></span>  
 <span data-ttu-id="48d3f-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="48d3f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48d3f-114">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="48d3f-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="48d3f-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="48d3f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48d3f-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48d3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d3f-117">参照</span><span class="sxs-lookup"><span data-stu-id="48d3f-117">See Also</span></span>  
 [<span data-ttu-id="48d3f-118">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="48d3f-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
