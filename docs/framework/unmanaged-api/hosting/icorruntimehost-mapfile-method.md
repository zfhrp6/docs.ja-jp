---
title: "ICorRuntimeHost::MapFile メソッド"
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
- ICorRuntimeHost.MapFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3047a473f36762ec57ae4ea87067e941ac568c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="ffe51-102">ICorRuntimeHost::MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="ffe51-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="ffe51-103">メモリに指定されたファイルをマップします。</span><span class="sxs-lookup"><span data-stu-id="ffe51-103">Maps the specified file into memory.</span></span> <span data-ttu-id="ffe51-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="ffe51-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe51-105">構文</span><span class="sxs-lookup"><span data-stu-id="ffe51-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ffe51-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ffe51-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ffe51-107">[in]マップするファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="ffe51-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="ffe51-108">[out]ファイルのマッピングを開始する開始メモリ アドレス。</span><span class="sxs-lookup"><span data-stu-id="ffe51-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe51-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="ffe51-109">Requirements</span></span>  
 <span data-ttu-id="ffe51-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ffe51-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffe51-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ffe51-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ffe51-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ffe51-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffe51-113">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="ffe51-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffe51-114">参照</span><span class="sxs-lookup"><span data-stu-id="ffe51-114">See Also</span></span>  
 [<span data-ttu-id="ffe51-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ffe51-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
