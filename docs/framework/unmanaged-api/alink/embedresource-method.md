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
ms.openlocfilehash: 98dbd32452184bf4f832bd66ffebb0fcf3d5bb0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="embedresource-method"></a><span data-ttu-id="ea03f-102">EmbedResource メソッド</span><span class="sxs-lookup"><span data-stu-id="ea03f-102">EmbedResource Method</span></span>
<span data-ttu-id="ea03f-103">埋め込みリソースを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ea03f-103">Declares an embedded resource.</span></span> <span data-ttu-id="ea03f-104">このメソッドには、リソースが実際には埋め込まれません。</span><span class="sxs-lookup"><span data-stu-id="ea03f-104">This method does not actually embed the resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea03f-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea03f-105">Syntax</span></span>  
  
```  
HRESULT EmbedResource(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    LPCWSTR     pszResourceName,  
    DWORD       dwOffset,  
    DWORD       dwFlags  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ea03f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea03f-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="ea03f-107">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="ea03f-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="ea03f-108">ファイルのリソースを格納するファイルのトークンまたはアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="ea03f-108">File token or assembly ID of file that contains the resource.</span></span>  
  
 `pszResourceName`  
 <span data-ttu-id="ea03f-109">リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="ea03f-109">Name of the resource.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="ea03f-110">RVA からのリソースのオフセット。</span><span class="sxs-lookup"><span data-stu-id="ea03f-110">Offset of resource from RVA.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="ea03f-111">ユーザー補助機能フラグなど`mrPublic`と`mrPrivate`です。</span><span class="sxs-lookup"><span data-stu-id="ea03f-111">Accessibility flags such as `mrPublic` and `mrPrivate`.</span></span> <span data-ttu-id="ea03f-112">これらのフラグを渡すこと[DefineExportedType メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea03f-112">These flags may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea03f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea03f-113">Return Value</span></span>  
 <span data-ttu-id="ea03f-114">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="ea03f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea03f-115">要件</span><span class="sxs-lookup"><span data-stu-id="ea03f-115">Requirements</span></span>  
 <span data-ttu-id="ea03f-116">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="ea03f-116">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea03f-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea03f-117">See Also</span></span>  
 [<span data-ttu-id="ea03f-118">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea03f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="ea03f-119">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea03f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="ea03f-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="ea03f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
