---
title: "ICorRuntimeHost::MapFile メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.MapFile
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::MapFile
helpviewer_keywords:
- ICorRuntimeHost::MapFile method [.NET Framework hosting]
- MapFile method [.NET Framework hosting]
ms.assetid: 45ae0502-0a31-4342-b7e3-f36e1cf738f3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd156aac23cdca446bcf2666ce36e91fef6d5392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="bf6a3-102">ICorRuntimeHost::MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="bf6a3-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="bf6a3-103">メモリに指定されたファイルをマップします。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-103">Maps the specified file into memory.</span></span> <span data-ttu-id="bf6a3-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf6a3-105">構文</span><span class="sxs-lookup"><span data-stu-id="bf6a3-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf6a3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bf6a3-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="bf6a3-107">[in]マップするファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="bf6a3-108">[out]ファイルのマッピングを開始する開始メモリ アドレス。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf6a3-109">要件</span><span class="sxs-lookup"><span data-stu-id="bf6a3-109">Requirements</span></span>  
 <span data-ttu-id="bf6a3-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf6a3-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf6a3-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf6a3-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="bf6a3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf6a3-113">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="bf6a3-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf6a3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bf6a3-114">See Also</span></span>  
 [<span data-ttu-id="bf6a3-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf6a3-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
