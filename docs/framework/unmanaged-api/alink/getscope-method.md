---
title: GetScope Method1
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
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a><span data-ttu-id="8fec9-102">GetScope Method1</span><span class="sxs-lookup"><span data-stu-id="8fec9-102">GetScope Method1</span></span>
<span data-ttu-id="8fec9-103">インポート スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="8fec9-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fec9-104">構文</span><span class="sxs-lookup"><span data-stu-id="8fec9-104">Syntax</span></span>  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fec9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8fec9-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8fec9-106">インポート先のアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="8fec9-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8fec9-107">インポートするファイルの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="8fec9-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="8fec9-108">インポートする 0 から始まるスコープです。</span><span class="sxs-lookup"><span data-stu-id="8fec9-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="8fec9-109">受信[IMetaDataImport インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)スコープのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8fec9-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8fec9-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="8fec9-110">Return Value</span></span>  
 <span data-ttu-id="8fec9-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="8fec9-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fec9-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="8fec9-112">Requirements</span></span>  
 <span data-ttu-id="8fec9-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="8fec9-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fec9-114">参照</span><span class="sxs-lookup"><span data-stu-id="8fec9-114">See Also</span></span>  
 [<span data-ttu-id="8fec9-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fec9-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8fec9-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fec9-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8fec9-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="8fec9-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
