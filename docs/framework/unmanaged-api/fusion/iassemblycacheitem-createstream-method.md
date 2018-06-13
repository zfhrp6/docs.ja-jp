---
title: IAssemblyCacheItem::CreateStream メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8057406552525be19f8e6457de9faf841edc6e68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429502"
---
# <a name="iassemblycacheitemcreatestream-method"></a><span data-ttu-id="696e2-102">IAssemblyCacheItem::CreateStream メソッド</span><span class="sxs-lookup"><span data-stu-id="696e2-102">IAssemblyCacheItem::CreateStream Method</span></span>
<span data-ttu-id="696e2-103">指定した名前と形式を使用するストリームを作成します。</span><span class="sxs-lookup"><span data-stu-id="696e2-103">Creates a stream with the specified name and format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696e2-104">構文</span><span class="sxs-lookup"><span data-stu-id="696e2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="696e2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="696e2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="696e2-106">[in]ものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="696e2-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszStreamName`  
 <span data-ttu-id="696e2-107">[in]作成されるストリームの名前。</span><span class="sxs-lookup"><span data-stu-id="696e2-107">[in] The name of the stream to be created.</span></span>  
  
 `dwFormat`  
 <span data-ttu-id="696e2-108">[in]ストリーミングするファイルの形式です。</span><span class="sxs-lookup"><span data-stu-id="696e2-108">[in] The format of the file to be streamed.</span></span>  
  
 `dwFormatFlags`  
 <span data-ttu-id="696e2-109">[in]ファイル形式に固有のものがありますで定義されているフラグです。</span><span class="sxs-lookup"><span data-stu-id="696e2-109">[in] Format-specific flags defined in Fusion.idl.</span></span>  
  
 `ppIStream`  
 <span data-ttu-id="696e2-110">[out]返されたのアドレスへのポインター [IStream](https://msdn.microsoft.com/library/aa380034.aspx)インスタンス。</span><span class="sxs-lookup"><span data-stu-id="696e2-110">[out] A pointer to the address of the returned [IStream](https://msdn.microsoft.com/library/aa380034.aspx) instance.</span></span>  
  
 `puliMaxSize`  
 <span data-ttu-id="696e2-111">[in、省略可能]によって参照されるストリームの最大サイズ`ppIStream`です。</span><span class="sxs-lookup"><span data-stu-id="696e2-111">[in, optional] The maximum size of the stream referenced by `ppIStream`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696e2-112">要件</span><span class="sxs-lookup"><span data-stu-id="696e2-112">Requirements</span></span>  
 <span data-ttu-id="696e2-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="696e2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696e2-114">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="696e2-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="696e2-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696e2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="696e2-116">See Also</span></span>  
 [<span data-ttu-id="696e2-117">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="696e2-117">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
