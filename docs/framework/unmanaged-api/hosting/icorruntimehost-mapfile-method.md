---
title: ICorRuntimeHost::MapFile メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b88758c339cd77bc7e17e0c29969f8783555f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436625"
---
# <a name="icorruntimehostmapfile-method"></a><span data-ttu-id="e2394-102">ICorRuntimeHost::MapFile メソッド</span><span class="sxs-lookup"><span data-stu-id="e2394-102">ICorRuntimeHost::MapFile Method</span></span>
<span data-ttu-id="e2394-103">メモリに指定されたファイルをマップします。</span><span class="sxs-lookup"><span data-stu-id="e2394-103">Maps the specified file into memory.</span></span> <span data-ttu-id="e2394-104">このメソッドは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="e2394-104">This method is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2394-105">構文</span><span class="sxs-lookup"><span data-stu-id="e2394-105">Syntax</span></span>  
  
```  
HRESULT MapFile(  
    [in]  HANDLE    hFile,  
    [out] HMODULE*  hMapAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e2394-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2394-106">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="e2394-107">[in]マップするファイルのハンドル。</span><span class="sxs-lookup"><span data-stu-id="e2394-107">[in] The handle of the file to be mapped.</span></span>  
  
 `hMapAddress`  
 <span data-ttu-id="e2394-108">[out]ファイルのマッピングを開始する開始メモリ アドレス。</span><span class="sxs-lookup"><span data-stu-id="e2394-108">[out] The starting memory address at which to begin mapping the file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2394-109">要件</span><span class="sxs-lookup"><span data-stu-id="e2394-109">Requirements</span></span>  
 <span data-ttu-id="e2394-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2394-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2394-111">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e2394-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2394-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="e2394-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2394-113">**.NET framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="e2394-113">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2394-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2394-114">See Also</span></span>  
 [<span data-ttu-id="e2394-115">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2394-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
