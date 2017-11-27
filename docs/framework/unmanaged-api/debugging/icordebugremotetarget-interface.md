---
title: "ICorDebugRemoteTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38357072b3a6e8e8a326a16600b2d7ed56cdcb2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="dffc1-102">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dffc1-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="dffc1-103">開発者が共通言語ランタイム (CLR: Common Language Runtime) 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="dffc1-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffc1-104">構文</span><span class="sxs-lookup"><span data-stu-id="dffc1-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dffc1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="dffc1-105">Methods</span></span>  
  
|<span data-ttu-id="dffc1-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="dffc1-106">Method</span></span>|<span data-ttu-id="dffc1-107">説明</span><span class="sxs-lookup"><span data-stu-id="dffc1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dffc1-108">Icordebugremotetarget::gethostname メソッド</span><span class="sxs-lookup"><span data-stu-id="dffc1-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="dffc1-109">リモート マシンのホスト名または IP アドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="dffc1-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dffc1-110">コメント</span><span class="sxs-lookup"><span data-stu-id="dffc1-110">Remarks</span></span>  
 <span data-ttu-id="dffc1-111">Windows 95、Windows 98、Windows ME、または x86 以外のプラットフォーム (IA-64、AMD64 など) では、混合モード (つまり、マネージ コードとネイティブ コード) デバッグはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dffc1-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffc1-112">要件</span><span class="sxs-lookup"><span data-stu-id="dffc1-112">Requirements</span></span>  
 <span data-ttu-id="dffc1-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dffc1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dffc1-114">**ヘッダー:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="dffc1-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="dffc1-115">**ライブラリ:** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dffc1-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="dffc1-116">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="dffc1-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffc1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="dffc1-117">See Also</span></span>  
 [<span data-ttu-id="dffc1-118">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dffc1-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="dffc1-119">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dffc1-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="dffc1-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="dffc1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
