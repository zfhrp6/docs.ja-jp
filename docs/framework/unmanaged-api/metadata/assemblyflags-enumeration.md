---
title: "AssemblyFlags 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91760b6d16b663257bf3d89915da3bd88b3411bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="9a3ba-102">AssemblyFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="9a3ba-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="9a3ba-103">アセンブリの実行時の機能を記述する値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a3ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a3ba-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="9a3ba-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="9a3ba-105">Members</span></span>  
  
|<span data-ttu-id="9a3ba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="9a3ba-106">Member</span></span>|<span data-ttu-id="9a3ba-107">説明</span><span class="sxs-lookup"><span data-stu-id="9a3ba-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="9a3ba-108">アセンブリを構成するファイル内で暗黙的な型定義のエクスポートを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="9a3ba-109">.NET Framework バージョン 1.0 および 1.1 では、この値は常に設定されると想定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="9a3ba-110">リソース定義がアセンブリを構成するファイル内で暗黙的なことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="9a3ba-111">.NET Framework 1.0 および 1.1 では、この値は常に設定されると想定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="9a3ba-112">同じアプリケーション ドメインで実行されている場合に、アセンブリが他のバージョンは実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="9a3ba-113">アセンブリはその他のバージョンが同じプロセスで実行されている場合に実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="9a3ba-114">アセンブリはその他のバージョンが同じコンピューターで実行されている場合に実行できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a3ba-115">コメント</span><span class="sxs-lookup"><span data-stu-id="9a3ba-115">Remarks</span></span>  
 <span data-ttu-id="9a3ba-116">参照されたアセンブリのサイド バイ サイド互換性機能を記述する 0x0010 ~ 0x0070、包括的な値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="9a3ba-117">これらの値のいずれも設定されている場合、アセンブリがサイド バイ サイド互換性のあると見なされます。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a3ba-118">要件</span><span class="sxs-lookup"><span data-stu-id="9a3ba-118">Requirements</span></span>  
 <span data-ttu-id="9a3ba-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a3ba-120">**ヘッダー:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a3ba-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="9a3ba-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a3ba-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a3ba-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a3ba-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3ba-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a3ba-123">See Also</span></span>  
 [<span data-ttu-id="9a3ba-124">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="9a3ba-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="9a3ba-125">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a3ba-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
