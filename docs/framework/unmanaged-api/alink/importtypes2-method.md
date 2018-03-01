---
title: "ImportTypes2 メソッド"
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
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 47c49253a1e2839939ef4e671f155e4a44d07529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="importtypes2-method"></a><span data-ttu-id="8c4aa-102">ImportTypes2 メソッド</span><span class="sxs-lookup"><span data-stu-id="8c4aa-102">ImportTypes2 Method</span></span>
<span data-ttu-id="8c4aa-103">種類のインポートを開始します。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-103">Initiates the import of types.</span></span> <span data-ttu-id="8c4aa-104">使用してインポートする各スコープの種類のインポートを開始するには、このメソッドを呼び出す[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-104">Call this method to begin importing types from each scope imported via [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c4aa-105">構文</span><span class="sxs-lookup"><span data-stu-id="8c4aa-105">Syntax</span></span>  
  
```  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8c4aa-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c4aa-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="8c4aa-107">インポート先のアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="8c4aa-108">インポート元のファイルの ID です。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="8c4aa-109">インポート元の 0 から始まるスコープです。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="8c4aa-110">特定のスコープの種類の列挙子のハンドルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="8c4aa-111">必要に応じて受信[IMetaDataImport2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-111">Optionally receives [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="8c4aa-112">必要に応じて指定したスコープの種類の数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c4aa-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c4aa-113">Return Value</span></span>  
 <span data-ttu-id="8c4aa-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c4aa-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="8c4aa-115">Requirements</span></span>  
 <span data-ttu-id="8c4aa-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="8c4aa-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c4aa-117">参照</span><span class="sxs-lookup"><span data-stu-id="8c4aa-117">See Also</span></span>  
 [<span data-ttu-id="8c4aa-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c4aa-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="8c4aa-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c4aa-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="8c4aa-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="8c4aa-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
