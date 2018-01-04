---
title: "LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPOVERLAPPED_COMPLETION_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords: LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b1846cf8fff5c41fc54ddeec5b495b50c63581c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="c75b6-102">LPOVERLAPPED_COMPLETION_ROUTINE 関数ポインター</span><span class="sxs-lookup"><span data-stu-id="c75b6-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="c75b6-103">デバイスに対する重複 I/O (非同期 I/O) が完了したときに、ホストに通知する関数を指します。</span><span class="sxs-lookup"><span data-stu-id="c75b6-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="c75b6-104">この関数ポインターが削除されて、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="c75b6-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c75b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="c75b6-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c75b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c75b6-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="c75b6-107">[in]値は、デバイスが閉じられた場合に、エラー コードです。それ以外の場合、この値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="c75b6-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="c75b6-108">デバイスを閉じる I/O デバイスが保留中のすべてをすぐに完了するとします。</span><span class="sxs-lookup"><span data-stu-id="c75b6-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="c75b6-109">[in]I/O 操作で転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="c75b6-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="c75b6-110">[in]I/O 要求を完了するために使用する情報を格納する構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c75b6-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c75b6-111">コメント</span><span class="sxs-lookup"><span data-stu-id="c75b6-111">Remarks</span></span>  
 <span data-ttu-id="c75b6-112">関数`LPOVERLAPPED_COMPLETION_ROUTINE`ポイントはコールバック関数であり、ホスト アプリケーションの作成者によって実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c75b6-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="c75b6-113">コールバック関数は、完了した I/O 要求を処理するホストを許可します。</span><span class="sxs-lookup"><span data-stu-id="c75b6-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c75b6-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="c75b6-114">Requirements</span></span>  
 <span data-ttu-id="c75b6-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c75b6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c75b6-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c75b6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c75b6-117">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="c75b6-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="c75b6-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c75b6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75b6-119">参照</span><span class="sxs-lookup"><span data-stu-id="c75b6-119">See Also</span></span>  
 [<span data-ttu-id="c75b6-120">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="c75b6-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
