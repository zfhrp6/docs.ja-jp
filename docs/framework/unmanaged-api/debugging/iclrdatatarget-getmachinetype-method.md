---
title: "ICLRDataTarget::GetMachineType メソッド"
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
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 56fabfd2bb929e40c60903ad7b5e86e2b18d7d93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="84dec-102">ICLRDataTarget::GetMachineType メソッド</span><span class="sxs-lookup"><span data-stu-id="84dec-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="84dec-103">ターゲット プロセスを使用している命令セットの種類の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="84dec-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84dec-104">構文</span><span class="sxs-lookup"><span data-stu-id="84dec-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84dec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84dec-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="84dec-106">[out]命令セットをターゲット プロセスを示す値を指すポインターが使用されています。</span><span class="sxs-lookup"><span data-stu-id="84dec-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="84dec-107">返された`machineType`WinNT.h ヘッダー ファイルで定義されている IMAGE_FILE_MACHINE 定数のいずれか。</span><span class="sxs-lookup"><span data-stu-id="84dec-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84dec-108">必要条件</span><span class="sxs-lookup"><span data-stu-id="84dec-108">Requirements</span></span>  
 <span data-ttu-id="84dec-109">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="84dec-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84dec-110">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="84dec-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="84dec-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84dec-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84dec-112">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84dec-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84dec-113">参照</span><span class="sxs-lookup"><span data-stu-id="84dec-113">See Also</span></span>  
 [<span data-ttu-id="84dec-114">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84dec-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
