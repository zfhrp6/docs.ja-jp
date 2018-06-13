---
title: ICorDebugProcess7 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess7
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 71aee5f3-5e10-44fa-be69-6d8a475f2c14
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a684a5daa0619b0614ca074b7b1e3b9d0b25882
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421439"
---
# <a name="icordebugprocess7-interface"></a><span data-ttu-id="42518-102">ICorDebugProcess7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42518-102">ICorDebugProcess7 Interface</span></span>
<span data-ttu-id="42518-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="42518-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="42518-104">ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="42518-104">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="42518-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="42518-105">Methods</span></span>  
  
|<span data-ttu-id="42518-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="42518-106">Method</span></span>|<span data-ttu-id="42518-107">説明</span><span class="sxs-lookup"><span data-stu-id="42518-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="42518-108">SetWriteableMetadataUpdateMode メソッド</span><span class="sxs-lookup"><span data-stu-id="42518-108">SetWriteableMetadataUpdateMode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)|<span data-ttu-id="42518-109">デバッガーがメモリ内のメタデータ更新をターゲット プロセスでどのように処理するかを決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="42518-109">Sets a value that determines how the debugger handles in-memory updates to metadata within the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42518-110">コメント</span><span class="sxs-lookup"><span data-stu-id="42518-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42518-111">要件</span><span class="sxs-lookup"><span data-stu-id="42518-111">Requirements</span></span>  
 <span data-ttu-id="42518-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="42518-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42518-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42518-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42518-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42518-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42518-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42518-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42518-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="42518-116">See Also</span></span>  
 [<span data-ttu-id="42518-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42518-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="42518-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="42518-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
