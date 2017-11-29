---
title: "ExportNestedType メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.ExportNestedType
- ExportNestedType
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedType
helpviewer_keywords: ExportNestedType method
ms.assetid: dec7df60-4d30-47c8-99db-72e0419e5f76
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 378d1e8b21b8d3993377ac08ff7006c420117bfe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtype-method"></a><span data-ttu-id="fb2c7-102">ExportNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="fb2c7-102">ExportNestedType Method</span></span>
<span data-ttu-id="fb2c7-103">入れ子にされた型をエクスポート可能として指定します。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-103">Specifies nested types as exportable.</span></span> <span data-ttu-id="fb2c7-104">[ExportType メソッド](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md)エクスポート入れ子にされた型をこともできますが、このメソッドは高速化します。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-104">The [ExportType Method](../../../../docs/framework/unmanaged-api/alink/exporttype-method.md) can also export nested types, but this method is faster.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2c7-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb2c7-105">Syntax</span></span>  
  
```  
HRESULT ExportNestedType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;   
```  
  
#### <a name="parameters"></a><span data-ttu-id="fb2c7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fb2c7-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fb2c7-107">エクスポートするアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-107">ID of assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="fb2c7-108">ファイルのトークンまたはエクスポート可能にする型を定義するファイルのアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-108">File token or Assembly of file that defines the type to be made exportable.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="fb2c7-109">エクスポート可能にする型のトークンを入力します。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-109">Type token of type to be made exportable.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="fb2c7-110">親の種類のトークンです。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-110">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="fb2c7-111">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-111">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="fb2c7-112">`ComType`フラグのように`tdPublic`または`tdNested`です。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-112">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="fb2c7-113">この値に渡すことができます[DefineExportedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-113">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="fb2c7-114">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-114">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fb2c7-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="fb2c7-115">Return Value</span></span>  
 <span data-ttu-id="fb2c7-116">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb2c7-117">要件</span><span class="sxs-lookup"><span data-stu-id="fb2c7-117">Requirements</span></span>  
 <span data-ttu-id="fb2c7-118">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="fb2c7-118">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2c7-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb2c7-119">See Also</span></span>  
 [<span data-ttu-id="fb2c7-120">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb2c7-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="fb2c7-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fb2c7-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="fb2c7-122">ALink API</span><span class="sxs-lookup"><span data-stu-id="fb2c7-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
