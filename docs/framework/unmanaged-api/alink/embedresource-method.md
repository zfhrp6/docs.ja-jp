---
title: "EmbedResource メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmbedResource
- EmbedResource
api_location: alink.dll
api_type: COM
f1_keywords: EmbedResource
helpviewer_keywords: EmbedResource method
ms.assetid: 667bd954-6dc6-4020-a3cb-0e8224179993
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 815e4b6abbb56b0998a12c096f0ba7cb678778ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="f3700-102">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="f3700-102">EmbedResource Method</span></span>
<span data-ttu-id="f3700-103">埋め込みリソースを宣言します。</span><span class="sxs-lookup"><span data-stu-id="f3700-103">Declares an embedded resource.</span></span> <span data-ttu-id="f3700-104">このメソッドには、リソースが実際には埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="f3700-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3700-105">構文</span><span class="sxs-lookup"><span data-stu-id="f3700-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3700-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f3700-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f3700-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="f3700-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f3700-108">ファイルのリソースを格納するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="f3700-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="f3700-109">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="f3700-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="f3700-110">RVA からのリソースのオフセット。</span><span class="sxs-lookup"><span data-stu-id="f3700-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f3700-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="f3700-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="f3700-112">これらのフラグを渡すこと[DefineExportedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="f3700-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f3700-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f3700-113">Return Value</span></span>  
 <span data-ttu-id="f3700-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="f3700-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3700-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="f3700-115">Requirements</span></span>  
 <span data-ttu-id="f3700-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="f3700-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3700-117">参照</span><span class="sxs-lookup"><span data-stu-id="f3700-117">See Also</span></span>  
 [<span data-ttu-id="f3700-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3700-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f3700-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f3700-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f3700-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="f3700-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
