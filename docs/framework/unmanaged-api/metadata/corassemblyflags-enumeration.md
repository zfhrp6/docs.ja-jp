---
title: "CorAssemblyFlags 列挙型"
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
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 059d896842c285bb071a25990ae9178c34ab802a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="b784f-102">CorAssemblyFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="b784f-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="b784f-103">アセンブリ コンパイルに適用されるメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b784f-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b784f-104">構文</span><span class="sxs-lookup"><span data-stu-id="b784f-104">Syntax</span></span>  
  
```  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="b784f-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b784f-105">Members</span></span>  
  
|<span data-ttu-id="b784f-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b784f-106">Member</span></span>|<span data-ttu-id="b784f-107">説明</span><span class="sxs-lookup"><span data-stu-id="b784f-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="b784f-108">アセンブリ参照が、完全、ハッシュされていないパブリック キーを保持していることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="b784f-109">関数は指定されたプロセッサのアーキテクチャを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="b784f-110">プロセッサ アーキテクチャがニュートラルであることを示します (PE32)。</span><span class="sxs-lookup"><span data-stu-id="b784f-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="b784f-111">プロセッサ アーキテクチャが x86 (PE32) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="b784f-112">プロセッサ アーキテクチャが Itanium (pe 32 +) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="b784f-113">プロセッサ アーキテクチャが AMD X64 (pe 32 +) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="b784f-114">プロセッサ アーキテクチャが ARM (PE32) であることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="b784f-115">アセンブリが参照アセンブリであることを示しますつまり、すべてのアーキテクチャに適用されますが、すべてのアーキテクチャでは実行できません。</span><span class="sxs-lookup"><span data-stu-id="b784f-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="b784f-116">したがって、フラグが同じ`afPA_Mask`です。</span><span class="sxs-lookup"><span data-stu-id="b784f-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="b784f-117">プロセッサ アーキテクチャのフラグに反映させるかを示す、`AssemblyRef`レコード。</span><span class="sxs-lookup"><span data-stu-id="b784f-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="b784f-118">プロセッサ アーキテクチャを記述するマスク。</span><span class="sxs-lookup"><span data-stu-id="b784f-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="b784f-119">プロセッサ アーキテクチャの説明が含まれることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b784f-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="b784f-120">プロセッサ アーキテクチャのフラグとインデックスの間でシフト数を示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="b784f-121">対応する値を示す、<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>の<xref:System.Diagnostics.DebuggableAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="b784f-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="b784f-122">対応する値を示す、<xref:System.Diagnostics.DebuggableAttribute.DebuggingModes>の<xref:System.Diagnostics.DebuggableAttribute>です。</span><span class="sxs-lookup"><span data-stu-id="b784f-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="b784f-123">実行時に、別のパブリッシャーからのアセンブリにアセンブリを再ターゲットできることを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="b784f-124">コンテンツの種類を説明するマスクです。</span><span class="sxs-lookup"><span data-stu-id="b784f-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="b784f-125">既定のコンテンツ タイプを示します。</span><span class="sxs-lookup"><span data-stu-id="b784f-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="b784f-126">示します、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]コンテンツの種類。</span><span class="sxs-lookup"><span data-stu-id="b784f-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b784f-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="b784f-127">Requirements</span></span>  
 <span data-ttu-id="b784f-128">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b784f-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b784f-129">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b784f-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b784f-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b784f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b784f-131">参照</span><span class="sxs-lookup"><span data-stu-id="b784f-131">See Also</span></span>  
 [<span data-ttu-id="b784f-132">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="b784f-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
