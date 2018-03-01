---
title: ICorDebugModule2 Interface1
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
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a3d62619fd83264bdc774cc1f09f4d98492d0a57
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="3e89f-102">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="3e89f-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="3e89f-103">ICorDebugModule インターフェイスを論理的に拡張として機能します。</span><span class="sxs-lookup"><span data-stu-id="3e89f-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e89f-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-104">Methods</span></span>  
  
|<span data-ttu-id="3e89f-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-105">Method</span></span>|<span data-ttu-id="3e89f-106">説明</span><span class="sxs-lookup"><span data-stu-id="3e89f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e89f-107">ApplyChanges メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="3e89f-108">実行中のプロセスにメタデータの変更と Microsoft intermediate language (MSIL) コードの変更を適用します。</span><span class="sxs-lookup"><span data-stu-id="3e89f-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="3e89f-109">GetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="3e89f-110">この・ イン タイム (JIT) コンパイルを制御するフラグを取得`ICorDebugModule2`です。</span><span class="sxs-lookup"><span data-stu-id="3e89f-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="3e89f-111">ResolveAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="3e89f-112">指定したメタデータ トークンによって参照されるアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="3e89f-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="3e89f-113">SetJITCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="3e89f-114">この JIT コンパイルを制御するフラグを設定`ICorDebugModule2`です。</span><span class="sxs-lookup"><span data-stu-id="3e89f-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="3e89f-115">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="3e89f-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="3e89f-116">これですべてのクラスのすべてのメソッドのだけマイ コードのみ (JMC) 状態に設定`ICorDebugModule2`を除き、指定した値を`pTokens`配列で、その逆の値に設定します。</span><span class="sxs-lookup"><span data-stu-id="3e89f-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e89f-117">コメント</span><span class="sxs-lookup"><span data-stu-id="3e89f-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e89f-118">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3e89f-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e89f-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="3e89f-119">Requirements</span></span>  
 <span data-ttu-id="3e89f-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3e89f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e89f-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e89f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e89f-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e89f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e89f-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e89f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e89f-124">参照</span><span class="sxs-lookup"><span data-stu-id="3e89f-124">See Also</span></span>  
 [<span data-ttu-id="3e89f-125">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3e89f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
