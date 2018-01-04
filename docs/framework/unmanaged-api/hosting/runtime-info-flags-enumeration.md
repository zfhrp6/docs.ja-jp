---
title: "RUNTIME_INFO_FLAGS 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="62d5e-102">RUNTIME_INFO_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="62d5e-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="62d5e-103">共通言語ランタイム (CLR) に関する情報を返す必要がありますを示す値を含みます。</span><span class="sxs-lookup"><span data-stu-id="62d5e-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="62d5e-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="62d5e-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="62d5e-105">Members</span></span>  
  
|<span data-ttu-id="62d5e-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="62d5e-106">Member</span></span>|<span data-ttu-id="62d5e-107">説明</span><span class="sxs-lookup"><span data-stu-id="62d5e-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="62d5e-108">ディレクトリ情報を含める必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="62d5e-109">バージョン情報を含める必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="62d5e-110">エラー発生時にエラー ダイアログ ボックスを表示しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="62d5e-111">示します呼び出しの影響、 [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS フラグを持つ関数をオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d5e-111">Indicates that the effects of calling the [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="62d5e-112">抑制されるのではなく、障害発生時にインストール ダイアログ ボックスを表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d5e-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="62d5e-113">AMD 64 互換性のあるバージョンのランタイムに関する情報を要求を示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="62d5e-114">IA 64 互換性のあるバージョンのランタイムに関する情報を要求を示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="62d5e-115">X86 と互換性のあるバージョンのランタイムに関する情報を要求を示します。</span><span class="sxs-lookup"><span data-stu-id="62d5e-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="62d5e-116">含めることを示すバージョン情報をアップグレードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d5e-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62d5e-117">コメント</span><span class="sxs-lookup"><span data-stu-id="62d5e-117">Remarks</span></span>  
 <span data-ttu-id="62d5e-118">次のプラットフォーム アーキテクチャ フラグは、一度に 1 つのみ指定でき、組み合わせることができません。</span><span class="sxs-lookup"><span data-stu-id="62d5e-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="62d5e-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="62d5e-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="62d5e-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="62d5e-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="62d5e-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="62d5e-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d5e-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="62d5e-122">Requirements</span></span>  
 <span data-ttu-id="62d5e-123">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62d5e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d5e-124">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62d5e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62d5e-125">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62d5e-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62d5e-126">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d5e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d5e-127">参照</span><span class="sxs-lookup"><span data-stu-id="62d5e-127">See Also</span></span>  
 [<span data-ttu-id="62d5e-128">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="62d5e-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
