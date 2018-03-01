---
title: "OSINFO 構造体"
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
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a><span data-ttu-id="2810a-102">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="2810a-102">OSINFO Structure</span></span>
<span data-ttu-id="2810a-103">アセンブリまたはモジュールのオペレーティング システムに関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2810a-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2810a-104">構文</span><span class="sxs-lookup"><span data-stu-id="2810a-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="2810a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="2810a-105">Members</span></span>  
  
|<span data-ttu-id="2810a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="2810a-106">Member</span></span>|<span data-ttu-id="2810a-107">説明</span><span class="sxs-lookup"><span data-stu-id="2810a-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="2810a-108">Microsoft Windows プラットフォーム関数で定義された識別子の値のいずれかの`GetVersionEx`します。</span><span class="sxs-lookup"><span data-stu-id="2810a-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="2810a-109">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2810a-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="2810a-110">-VER_PLATFORM_WIN32s、つまり 0x0000、Microsoft Windows 3.1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="2810a-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="2810a-111">-VER_PLATFORM_WIN32_WINDOWS、または 0x0001、Windows 95、Windows 98、またはそれらの子とオペレーティング システムを指定します。</span><span class="sxs-lookup"><span data-stu-id="2810a-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="2810a-112">-VER_PLATFORM_WIN32_NT、または 0x0010、Windows NT またはそこから子とオペレーティング システムを指定します。</span><span class="sxs-lookup"><span data-stu-id="2810a-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="2810a-113">オペレーティング システムのメジャー バージョン、または任意のバージョンを示すために NULL 値。</span><span class="sxs-lookup"><span data-stu-id="2810a-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="2810a-114">オペレーティング システムのマイナー バージョン、または任意のバージョンを示すために NULL 値。</span><span class="sxs-lookup"><span data-stu-id="2810a-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2810a-115">コメント</span><span class="sxs-lookup"><span data-stu-id="2810a-115">Remarks</span></span>  
 <span data-ttu-id="2810a-116">`OSINFO`基づく、`OSVERSIONINFOEX`構造体をで使用される関数への呼び出し、Microsoft Windows プラットフォーム`GetVersionEx`です。</span><span class="sxs-lookup"><span data-stu-id="2810a-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="2810a-117">この構造体の使用は、ASSEMBLYMETADATA 構造体によってをそのオペレーティング システムのサポートを示します。</span><span class="sxs-lookup"><span data-stu-id="2810a-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2810a-118">必要条件</span><span class="sxs-lookup"><span data-stu-id="2810a-118">Requirements</span></span>  
 <span data-ttu-id="2810a-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2810a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2810a-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2810a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2810a-121">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="2810a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2810a-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2810a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2810a-123">参照</span><span class="sxs-lookup"><span data-stu-id="2810a-123">See Also</span></span>  
 [<span data-ttu-id="2810a-124">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="2810a-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="2810a-125">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2810a-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
