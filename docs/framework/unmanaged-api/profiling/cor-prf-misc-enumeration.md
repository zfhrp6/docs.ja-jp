---
title: "COR_PRF_MISC 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_MISC
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_MISC
helpviewer_keywords: COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75e740a6ca17135a3de2e945e205f4581b2f32e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corprfmisc-enumeration"></a><span data-ttu-id="89371-102">COR_PRF_MISC 列挙型</span><span class="sxs-lookup"><span data-stu-id="89371-102">COR_PRF_MISC Enumeration</span></span>
<span data-ttu-id="89371-103">特殊な識別子を指定する定数値を含めます。</span><span class="sxs-lookup"><span data-stu-id="89371-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89371-104">構文</span><span class="sxs-lookup"><span data-stu-id="89371-104">Syntax</span></span>  
  
```  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="89371-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="89371-105">Members</span></span>  
  
|<span data-ttu-id="89371-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="89371-106">Member</span></span>|<span data-ttu-id="89371-107">説明</span><span class="sxs-lookup"><span data-stu-id="89371-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="89371-108">によって使用される既定の識別子[icorprofilerinfo::getmoduleinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)モジュールのアセンブリにアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="89371-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="89371-109">クラスに属していないグローバル定数の既定のクラス識別子。</span><span class="sxs-lookup"><span data-stu-id="89371-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="89371-110">モジュールに属していないグローバル オブジェクトの既定のモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="89371-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89371-111">要件</span><span class="sxs-lookup"><span data-stu-id="89371-111">Requirements</span></span>  
 <span data-ttu-id="89371-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="89371-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89371-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89371-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89371-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89371-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89371-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89371-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89371-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="89371-116">See Also</span></span>  
 [<span data-ttu-id="89371-117">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="89371-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
