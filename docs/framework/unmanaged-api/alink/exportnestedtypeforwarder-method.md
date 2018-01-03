---
title: "ExportNestedTypeForwarder メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportNestedTypeForwarder
api_location: alink.dll
api_type: COM
f1_keywords: ExportNestedTypeForwarder
helpviewer_keywords: ExportNestedTypeForwarder method
ms.assetid: 886ea6c5-6b26-4b88-8bf6-448d6d191950
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eee41e9f71d600a74cc9f74b538ad9e215f0d905
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="1609e-102">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="1609e-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="1609e-103">指定したアセンブリの型のテーブルを入れ子にされた型の型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="1609e-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1609e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1609e-104">Syntax</span></span>  
  
```  
HRESULT ExportNestedTypeForwarder(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    mdExportedType  ParentType,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1609e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1609e-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1609e-106">エクスポートするアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="1609e-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1609e-107">ファイルの種類を定義するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="1609e-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="1609e-108">型のトークンです。</span><span class="sxs-lookup"><span data-stu-id="1609e-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="1609e-109">親の種類のトークンです。</span><span class="sxs-lookup"><span data-stu-id="1609e-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="1609e-110">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="1609e-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1609e-111">`ComType`フラグのように`tdPublic`または`tdNested`です。</span><span class="sxs-lookup"><span data-stu-id="1609e-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="1609e-112">エクスポート型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1609e-112">Receives token of export type.</span></span> <span data-ttu-id="1609e-113">これは、入れ子にされた型の生成にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="1609e-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1609e-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="1609e-114">Return Value</span></span>  
 <span data-ttu-id="1609e-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="1609e-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1609e-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="1609e-116">Requirements</span></span>  
 <span data-ttu-id="1609e-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="1609e-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1609e-118">参照</span><span class="sxs-lookup"><span data-stu-id="1609e-118">See Also</span></span>  
 [<span data-ttu-id="1609e-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1609e-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1609e-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1609e-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1609e-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="1609e-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
