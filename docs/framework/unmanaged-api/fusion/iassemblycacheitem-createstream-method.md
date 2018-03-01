---
title: "IAssemblyCacheItem::CreateStream メソッド"
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
- IAssemblyCacheItem.CreateStream
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCacheItem::CreateStream
helpviewer_keywords:
- CreateStream method [.NET Framework fusion]
- IAsssemblyCacheItem::CreateStream method [.NET Framework fusion]
ms.assetid: 697ab0f4-470c-4baa-a415-4a975c42d0d5
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a24d9732a8e413b3cde0ac1c622743153ff6fd01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="5b6a5-102">IAssemblyCacheItem::CreateStream メソッド</span><span class="sxs-lookup"><span data-stu-id="5b6a5-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="5b6a5-103">指定した名前と形式を使用するストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b6a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b6a5-104">Syntax</span></span>  
  
```  
HRESULT CreateStream (  
    [in]  DWORD dwFlags,  
    [in]  LPCWSTR pszStreamName,  
    [in]  DWORD dwFormat,  
    [in]  DWORD dwFormatFlags,  
    [out] IStream **ppIStream,  
    [in, optional] ULARGE_INTEGER *puliMaxSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b6a5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b6a5-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="5b6a5-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="5b6a5-107">[in]作成されるストリームの名前。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="5b6a5-108">[in]ストリーミングするファイルの形式です。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="5b6a5-109">[in]ファイル形式に固有のものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="5b6a5-110">[out]返されたのアドレスへのポインター<xref:IStream>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-110">[out] A pointer to the address of the returned <xref:IStream> instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="5b6a5-111">[in、省略可能]によって参照されるストリームの最大サイズ`ppIStream`です。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b6a5-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="5b6a5-112">Requirements</span></span>  
 <span data-ttu-id="5b6a5-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5b6a5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b6a5-114">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5b6a5-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5b6a5-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b6a5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b6a5-116">参照</span><span class="sxs-lookup"><span data-stu-id="5b6a5-116">See Also</span></span>  
 [<span data-ttu-id="5b6a5-117">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b6a5-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
