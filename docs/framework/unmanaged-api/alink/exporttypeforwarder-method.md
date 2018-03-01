---
title: "ExportTypeForwarder メソッド"
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
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3fe418b1f8a5d5a6d3c2d36184ca76d5ef9989bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exporttypeforwarder-method"></a><span data-ttu-id="e4313-102">ExportTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="e4313-102">ExportTypeForwarder Method</span></span>
<span data-ttu-id="e4313-103">指定したアセンブリの型のテーブルには型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e4313-103">Adds a type forwarder to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4313-104">構文</span><span class="sxs-lookup"><span data-stu-id="e4313-104">Syntax</span></span>  
  
```  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4313-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4313-105">Parameters</span></span>  
 `tkAssemblyRef`  
 <span data-ttu-id="e4313-106">型フォワーダーが参照するアセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="e4313-106">Reference to the assembly to which the type forwarder refers.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="e4313-107">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="e4313-107">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="e4313-108">`ComType`フラグのように`tdPublic`または`tdNested`です。</span><span class="sxs-lookup"><span data-stu-id="e4313-108">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="e4313-109">この値に渡すことができます[DefineExportedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="e4313-109">This value may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="e4313-110">エクスポートされた型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e4313-110">Receives the token of the exported type.</span></span> <span data-ttu-id="e4313-111">これは、入れ子にされた型の生成にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="e4313-111">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4313-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="e4313-112">Return Value</span></span>  
 <span data-ttu-id="e4313-113">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="e4313-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4313-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="e4313-114">Requirements</span></span>  
 <span data-ttu-id="e4313-115">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="e4313-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4313-116">参照</span><span class="sxs-lookup"><span data-stu-id="e4313-116">See Also</span></span>  
 [<span data-ttu-id="e4313-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4313-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="e4313-118">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4313-118">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="e4313-119">ALink API</span><span class="sxs-lookup"><span data-stu-id="e4313-119">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
