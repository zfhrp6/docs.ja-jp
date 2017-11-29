---
title: "ASSEMBLY_INFO 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLY_INFO
api_location: fusion.dll
api_type: COM
f1_keywords: ASSEMBLY_INFO
helpviewer_keywords: ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d532bbd2d338f942c09c4213620468a3361db5f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyinfo-structure"></a><span data-ttu-id="33da0-102">ASSEMBLY_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="33da0-102">ASSEMBLY_INFO Structure</span></span>
<span data-ttu-id="33da0-103">グローバル アセンブリ キャッシュに登録されているアセンブリに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33da0-103">Contains information about an assembly that is registered in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33da0-104">構文</span><span class="sxs-lookup"><span data-stu-id="33da0-104">Syntax</span></span>  
  
```  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="33da0-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="33da0-105">Members</span></span>  
  
|<span data-ttu-id="33da0-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="33da0-106">Member</span></span>|<span data-ttu-id="33da0-107">説明</span><span class="sxs-lookup"><span data-stu-id="33da0-107">Description</span></span>|  
|------------|-----------------|  
|`cbAssemblyInfo`|<span data-ttu-id="33da0-108">構造体のバイト単位のサイズ。</span><span class="sxs-lookup"><span data-stu-id="33da0-108">The size, in bytes, of the structure.</span></span> <span data-ttu-id="33da0-109">このフィールドは、将来の機能拡張予約されています。</span><span class="sxs-lookup"><span data-stu-id="33da0-109">This field is reserved for future extensibility.</span></span>|  
|`dwAssemblyFlags`|<span data-ttu-id="33da0-110">アセンブリのインストールの詳細を示すフラグです。</span><span class="sxs-lookup"><span data-stu-id="33da0-110">Flags that indicate installation details about the assembly.</span></span> <span data-ttu-id="33da0-111">次の値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="33da0-111">The following values are supported:</span></span><br /><br /> <span data-ttu-id="33da0-112">-ASSEMBLYINFO_FLAG_INSTALLED 値アセンブリがインストールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="33da0-112">-   The ASSEMBLYINFO_FLAG_INSTALLED value, which indicates that the assembly is installed.</span></span> <span data-ttu-id="33da0-113">.NET Framework の現在のバージョンが常に設定`dwAssemblyFlags`この値にします。</span><span class="sxs-lookup"><span data-stu-id="33da0-113">The current version of the .NET Framework always sets `dwAssemblyFlags` to this value.</span></span><br /><span data-ttu-id="33da0-114">-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 値アセンブリが常駐ペイロードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="33da0-114">-   The ASSEMBLYINFO_FLAG_PAYLOADRESIDENT value, which indicates that the assembly is a payload resident.</span></span> <span data-ttu-id="33da0-115">.NET Framework の現在のバージョンを設定しません`dwAssemblyFlags`この値にします。</span><span class="sxs-lookup"><span data-stu-id="33da0-115">The current version of the .NET Framework never sets `dwAssemblyFlags` to this value.</span></span>|  
|`uliAssemblySizeInKB`|<span data-ttu-id="33da0-116">アセンブリに含まれるファイルの合計サイズ。</span><span class="sxs-lookup"><span data-stu-id="33da0-116">The total size, in kilobytes, of the files that the assembly contains.</span></span>|  
|`pszCurrentAssemblyPathBuf`|<span data-ttu-id="33da0-117">マニフェスト ファイルに、現在のパスを格納する文字列バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="33da0-117">A pointer to a string buffer that holds the current path to the manifest file.</span></span> <span data-ttu-id="33da0-118">パスの末尾に null 文字を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="33da0-118">The path must end with a null character.</span></span>|  
|`cchBuf`|<span data-ttu-id="33da0-119">ワイド文字で、null 終端文字の数を`pszCurrentAssemblyPathBuf`が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33da0-119">The number of wide characters, including the null terminator, that `pszCurrentAssemblyPathBuf` contains.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33da0-120">要件</span><span class="sxs-lookup"><span data-stu-id="33da0-120">Requirements</span></span>  
 <span data-ttu-id="33da0-121">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="33da0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33da0-122">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="33da0-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="33da0-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33da0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33da0-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="33da0-124">See Also</span></span>  
 [<span data-ttu-id="33da0-125">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="33da0-125">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [<span data-ttu-id="33da0-126">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="33da0-126">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
