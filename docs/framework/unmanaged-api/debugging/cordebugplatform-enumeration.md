---
title: CorDebugPlatform 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d3b8f1e869e90fd3388cc0844e608b7ff40fc89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407093"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="e2b90-102">CorDebugPlatform 列挙型</span><span class="sxs-lookup"><span data-stu-id="e2b90-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="e2b90-103">使用されるターゲット プラットフォームの値を提供、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e2b90-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2b90-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2b90-104">Syntax</span></span>  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="e2b90-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e2b90-105">Members</span></span>  
  
|<span data-ttu-id="e2b90-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e2b90-106">Member</span></span>|<span data-ttu-id="e2b90-107">説明</span><span class="sxs-lookup"><span data-stu-id="e2b90-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="e2b90-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="e2b90-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="e2b90-109">ターゲット プラットフォームは、Intel x86 ハードウェア上で稼動する Windows です。</span><span class="sxs-lookup"><span data-stu-id="e2b90-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="e2b90-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="e2b90-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="e2b90-111">ターゲット プラットフォームは、AMD64 または Intel EM64T ハードウェア上で稼動する 64 ビット Windows です。</span><span class="sxs-lookup"><span data-stu-id="e2b90-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="e2b90-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="e2b90-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="e2b90-113">ターゲット プラットフォームは、Intel IA-64 ハードウェア上で稼動する 32 ビット Windows です。</span><span class="sxs-lookup"><span data-stu-id="e2b90-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="e2b90-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="e2b90-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="e2b90-115">ターゲット プラットフォームは、PowerPC ハードウェア上で稼動する Macintosh オペレーティング システムです。</span><span class="sxs-lookup"><span data-stu-id="e2b90-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="e2b90-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="e2b90-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="e2b90-117">ターゲット プラットフォームは、Intel x86 ハードウェア上で稼動する Macintosh オペレーティング システムです。</span><span class="sxs-lookup"><span data-stu-id="e2b90-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="e2b90-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="e2b90-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="e2b90-119">ターゲット プラットフォームは、Windows ARM ハードウェア上で稼動する Macintosh オペレーティング システムです。</span><span class="sxs-lookup"><span data-stu-id="e2b90-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="e2b90-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="e2b90-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="e2b90-121">ターゲット プラットフォームは、amd 64 ハードウェアで実行されている Macintosh オペレーティング システムです。</span><span class="sxs-lookup"><span data-stu-id="e2b90-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e2b90-122">要件</span><span class="sxs-lookup"><span data-stu-id="e2b90-122">Requirements</span></span>  
 <span data-ttu-id="e2b90-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e2b90-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2b90-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2b90-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2b90-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2b90-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2b90-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2b90-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="e2b90-127">`CORDB_PLATFORM_WINDOWS_ARM` および `CORDB_PLATFORM_MAC_AMD64` メンバーは、.NET Framework 4.5.2 以降のバージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2b90-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b90-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2b90-128">See Also</span></span>  
 [<span data-ttu-id="e2b90-129">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e2b90-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
