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
ms.openlocfilehash: 41c0984e4439b89ddee2b55bbca7a098075d6bd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="exportnestedtypeforwarder-method"></a><span data-ttu-id="471f1-102">ExportNestedTypeForwarder メソッド</span><span class="sxs-lookup"><span data-stu-id="471f1-102">ExportNestedTypeForwarder Method</span></span>
<span data-ttu-id="471f1-103">指定したアセンブリの型のテーブルを入れ子にされた型の型フォワーダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="471f1-103">Adds a type forwarder for a nested type to the type table of the given assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="471f1-104">構文</span><span class="sxs-lookup"><span data-stu-id="471f1-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="471f1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="471f1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="471f1-106">エクスポートするアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="471f1-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="471f1-107">ファイルの種類を定義するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="471f1-107">File token or assembly ID of file that defines the type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="471f1-108">型のトークンです。</span><span class="sxs-lookup"><span data-stu-id="471f1-108">Token for the type.</span></span>  
  
 `ParentType`  
 <span data-ttu-id="471f1-109">親の種類のトークンです。</span><span class="sxs-lookup"><span data-stu-id="471f1-109">Token of parent type.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="471f1-110">エクスポートする完全修飾型名。</span><span class="sxs-lookup"><span data-stu-id="471f1-110">Fully qualified type name to export.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="471f1-111">`ComType`フラグのように`tdPublic`または`tdNested`です。</span><span class="sxs-lookup"><span data-stu-id="471f1-111">`ComType` flags such as `tdPublic` or `tdNested`.</span></span>  
  
 `pType`  
 <span data-ttu-id="471f1-112">エクスポート型のトークンを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="471f1-112">Receives token of export type.</span></span> <span data-ttu-id="471f1-113">これは、入れ子にされた型の生成にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="471f1-113">This is necessary only for emitting nested types.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="471f1-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="471f1-114">Return Value</span></span>  
 <span data-ttu-id="471f1-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="471f1-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="471f1-116">要件</span><span class="sxs-lookup"><span data-stu-id="471f1-116">Requirements</span></span>  
 <span data-ttu-id="471f1-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="471f1-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="471f1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="471f1-118">See Also</span></span>  
 [<span data-ttu-id="471f1-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="471f1-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="471f1-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="471f1-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="471f1-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="471f1-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
