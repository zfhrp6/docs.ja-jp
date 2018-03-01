---
title: "GetScope2 メソッド"
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
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e57ce8fbe0b8e60c9f6f6295e9331c571aedf92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getscope2-method"></a><span data-ttu-id="3be18-102">GetScope2 メソッド</span><span class="sxs-lookup"><span data-stu-id="3be18-102">GetScope2 Method</span></span>
<span data-ttu-id="3be18-103">インポート スコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="3be18-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3be18-104">構文</span><span class="sxs-lookup"><span data-stu-id="3be18-104">Syntax</span></span>  
  
```  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3be18-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3be18-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="3be18-106">ターゲット アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="3be18-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="3be18-107">インポート元のファイルの ID。</span><span class="sxs-lookup"><span data-stu-id="3be18-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="3be18-108">インポートする 0 から始まるスコープです。</span><span class="sxs-lookup"><span data-stu-id="3be18-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="3be18-109">ポインターを受け取る[IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)の指定されたスコープのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3be18-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3be18-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="3be18-110">Return Value</span></span>  
 <span data-ttu-id="3be18-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="3be18-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3be18-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="3be18-112">Requirements</span></span>  
 <span data-ttu-id="3be18-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="3be18-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3be18-114">参照</span><span class="sxs-lookup"><span data-stu-id="3be18-114">See Also</span></span>  
 [<span data-ttu-id="3be18-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3be18-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3be18-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3be18-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3be18-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="3be18-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
