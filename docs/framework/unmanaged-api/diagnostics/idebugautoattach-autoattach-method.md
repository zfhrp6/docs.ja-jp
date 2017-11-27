---
title: "IDebugAutoAttach::AutoAttach メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebugAutoAttach.AutoAttach
api_location: diasymreader.dll
api_type: COM
f1_keywords: IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 359aaf96c42a661657028d508f096f9625d4ba71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="11ea4-102">IDebugAutoAttach::AutoAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="11ea4-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="11ea4-103">サーバー起動デバッガーの自動実行をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="11ea4-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11ea4-104">構文</span><span class="sxs-lookup"><span data-stu-id="11ea4-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="11ea4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11ea4-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="11ea4-106">[in]常に設定`GUID_NULL`です。</span><span class="sxs-lookup"><span data-stu-id="11ea4-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="11ea4-107">[in]プロセス ID を使用して取得する通常、`GetCurrentProcessId`関数。</span><span class="sxs-lookup"><span data-stu-id="11ea4-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="11ea4-108">[in]プログラムの種類: `AUTOATTACH_PROGRAM_WIN32`、 `AUTOATTACH_PROGRAM_COMPLUS`、または`AUTOATTACH_PROGRAM_UNKNOWN`です。</span><span class="sxs-lookup"><span data-stu-id="11ea4-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="11ea4-109">[in]プログラム id。</span><span class="sxs-lookup"><span data-stu-id="11ea4-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="11ea4-110">[in]Debug の動詞によって渡された文字列です。</span><span class="sxs-lookup"><span data-stu-id="11ea4-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11ea4-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="11ea4-111">Return Value</span></span>  
 <span data-ttu-id="11ea4-112">メソッドが成功した場合は S_OK です。</span><span class="sxs-lookup"><span data-stu-id="11ea4-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11ea4-113">要件</span><span class="sxs-lookup"><span data-stu-id="11ea4-113">Requirements</span></span>  
 <span data-ttu-id="11ea4-114">**ヘッダー:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="11ea4-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ea4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="11ea4-115">See Also</span></span>  
 [<span data-ttu-id="11ea4-116">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11ea4-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
