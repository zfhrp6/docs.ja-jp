---
title: OSINFO 構造体
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6c5bc63da7ebe86b653c9bef7caeb1cf28d3a7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450051"
---
# <a name="osinfo-structure"></a><span data-ttu-id="c880c-102">OSINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="c880c-102">OSINFO Structure</span></span>
<span data-ttu-id="c880c-103">アセンブリまたはモジュールのオペレーティング システムに関する詳細情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c880c-103">Contains details about the operating system for an assembly or module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c880c-104">構文</span><span class="sxs-lookup"><span data-stu-id="c880c-104">Syntax</span></span>  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c880c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c880c-105">Members</span></span>  
  
|<span data-ttu-id="c880c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c880c-106">Member</span></span>|<span data-ttu-id="c880c-107">説明</span><span class="sxs-lookup"><span data-stu-id="c880c-107">Description</span></span>|  
|------------|-----------------|  
|`dwOSPlatformId`|<span data-ttu-id="c880c-108">Microsoft Windows プラットフォーム関数で定義された識別子の値のいずれかの`GetVersionEx`します。</span><span class="sxs-lookup"><span data-stu-id="c880c-108">One of the identifier values defined by the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="c880c-109">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c880c-109">The following values are supported:</span></span><br /><br /> <span data-ttu-id="c880c-110">-VER_PLATFORM_WIN32s、つまり 0x0000、Microsoft Windows 3.1 を指定します。</span><span class="sxs-lookup"><span data-stu-id="c880c-110">-   VER_PLATFORM_WIN32s, or 0x0000, to specify Microsoft Windows 3.1.</span></span><br /><span data-ttu-id="c880c-111">-VER_PLATFORM_WIN32_WINDOWS、または 0x0001、Windows 95、Windows 98、またはそれらの子とオペレーティング システムを指定します。</span><span class="sxs-lookup"><span data-stu-id="c880c-111">-   VER_PLATFORM_WIN32_WINDOWS, or 0x0001, to specify Windows 95, Windows 98, or operating systems descended from them.</span></span><br /><span data-ttu-id="c880c-112">-VER_PLATFORM_WIN32_NT、または 0x0010、Windows NT またはそこから子とオペレーティング システムを指定します。</span><span class="sxs-lookup"><span data-stu-id="c880c-112">-   VER_PLATFORM_WIN32_NT, or 0x0010, to specify Windows NT or operating systems descended from it.</span></span>|  
|`dwOSMajorVersion`|<span data-ttu-id="c880c-113">オペレーティング システムのメジャー バージョン、または任意のバージョンを示すために NULL 値。</span><span class="sxs-lookup"><span data-stu-id="c880c-113">The operating system major version, or a NULL value to indicate any version.</span></span>|  
|`dwOSMinorVersion`|<span data-ttu-id="c880c-114">オペレーティング システムのマイナー バージョン、または任意のバージョンを示すために NULL 値。</span><span class="sxs-lookup"><span data-stu-id="c880c-114">The operating system minor version, or a NULL value to indicate any version.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c880c-115">コメント</span><span class="sxs-lookup"><span data-stu-id="c880c-115">Remarks</span></span>  
 <span data-ttu-id="c880c-116">`OSINFO` 基づく、`OSVERSIONINFOEX`構造体をで使用される関数への呼び出し、Microsoft Windows プラットフォーム`GetVersionEx`です。</span><span class="sxs-lookup"><span data-stu-id="c880c-116">`OSINFO` is based on the `OSVERSIONINFOEX` structure that is used in calls to the Microsoft Windows platform function `GetVersionEx`.</span></span> <span data-ttu-id="c880c-117">この構造体の使用は、ASSEMBLYMETADATA 構造体によってをそのオペレーティング システムのサポートを示します。</span><span class="sxs-lookup"><span data-stu-id="c880c-117">This structure is used by the ASSEMBLYMETADATA structure to indicate its operating system support.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c880c-118">要件</span><span class="sxs-lookup"><span data-stu-id="c880c-118">Requirements</span></span>  
 <span data-ttu-id="c880c-119">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c880c-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c880c-120">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c880c-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c880c-121">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="c880c-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c880c-122">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c880c-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c880c-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c880c-123">See Also</span></span>  
 [<span data-ttu-id="c880c-124">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="c880c-124">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="c880c-125">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c880c-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
