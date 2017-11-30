---
title: "COR_PRF_CODEGEN_FLAGS 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODEGEN_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODEGEN_FLAGS
helpviewer_keywords: COR_PRF_CODEGEN_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 3e184022-0247-4824-a23d-6b29593d8d01
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c2c97510077fefd730827ac00326d267fd1c62ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodegenflags-enumeration"></a><span data-ttu-id="db2cd-102">COR_PRF_CODEGEN_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="db2cd-102">COR_PRF_CODEGEN_FLAGS Enumeration</span></span>
<span data-ttu-id="db2cd-103">コード生成フラグを設定することができますを定義、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="db2cd-103">Defines the code generation flags that can be set with the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db2cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="db2cd-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CODEGEN_DISABLE_INLINING =          0x0001,  
    COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS = 0x0002,  
} COR_PRF_CODEGEN_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="db2cd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="db2cd-105">Members</span></span>  
  
|<span data-ttu-id="db2cd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="db2cd-106">Member</span></span>|<span data-ttu-id="db2cd-107">説明</span><span class="sxs-lookup"><span data-stu-id="db2cd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_CODEGEN_DISABLE_INLINING`|<span data-ttu-id="db2cd-108">関数はこの関数の本体にインライン展開できません。</span><span class="sxs-lookup"><span data-stu-id="db2cd-108">No functions will be inlined into this function’s body.</span></span> <span data-ttu-id="db2cd-109">ただし、関数自体は、呼び出し元にインラインでない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="db2cd-109">However, the function itself may be inlined into its callers.</span></span>|  
|`COR_PRF_CODEGEN_DISABLE_ALL_OPTIMIZATIONS`|<span data-ttu-id="db2cd-110">この関数の本体には、すべての最適化を無効にしてがあります。</span><span class="sxs-lookup"><span data-stu-id="db2cd-110">All optimizations will be disabled for this function’s body.</span></span> <span data-ttu-id="db2cd-111">ただし、関数自体はまだいません、呼び出し元にインライン化します。</span><span class="sxs-lookup"><span data-stu-id="db2cd-111">However, the function itself may still be inlined into its callers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db2cd-112">コメント</span><span class="sxs-lookup"><span data-stu-id="db2cd-112">Remarks</span></span>  
 <span data-ttu-id="db2cd-113">`COR_PRF_CODEGEN_FLAGS`列挙型を使用して、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)プロファイラーが JIT 再コンパイルされた関数のコード生成を制御するを有効にするメソッド。</span><span class="sxs-lookup"><span data-stu-id="db2cd-113">The `COR_PRF_CODEGEN_FLAGS` enumeration is used by the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) method to enable the profiler to control the code generation for the JIT-recompiled function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db2cd-114">要件</span><span class="sxs-lookup"><span data-stu-id="db2cd-114">Requirements</span></span>  
 <span data-ttu-id="db2cd-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="db2cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db2cd-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="db2cd-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="db2cd-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db2cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db2cd-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db2cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db2cd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="db2cd-119">See Also</span></span>  
 [<span data-ttu-id="db2cd-120">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="db2cd-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)