---
title: ICorDebugStepper2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4652bcb00d3437350b5fd3e1071b3c538403cfe3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418690"
---
# <a name="icordebugstepper2-interface1"></a><span data-ttu-id="58600-102">ICorDebugStepper2 Interface1</span><span class="sxs-lookup"><span data-stu-id="58600-102">ICorDebugStepper2 Interface1</span></span>
<span data-ttu-id="58600-103">だけマイ コード (のみ JMC) デバッグのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="58600-103">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="58600-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="58600-104">Methods</span></span>  
  
|<span data-ttu-id="58600-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="58600-105">Method</span></span>|<span data-ttu-id="58600-106">説明</span><span class="sxs-lookup"><span data-stu-id="58600-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58600-107">SetJMC メソッド</span><span class="sxs-lookup"><span data-stu-id="58600-107">SetJMC Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-setjmc-method.md)|<span data-ttu-id="58600-108">アプリケーションの開発者によって作成されたコードでのみこの ICorDebugStepper が手順かどうかを指定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="58600-108">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58600-109">コメント</span><span class="sxs-lookup"><span data-stu-id="58600-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58600-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="58600-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58600-111">要件</span><span class="sxs-lookup"><span data-stu-id="58600-111">Requirements</span></span>  
 <span data-ttu-id="58600-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="58600-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58600-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58600-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58600-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58600-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58600-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58600-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58600-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="58600-116">See Also</span></span>  
 [<span data-ttu-id="58600-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58600-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
