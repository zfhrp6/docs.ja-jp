---
title: AddImport Method1
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
- AddImport
- IALink.AddImport
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AddImport
helpviewer_keywords:
- AddImport method
ms.assetid: 4fedf8a0-08c8-43d0-aa00-20f2a521c991
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d8827821deaeda311a42855737ecf53ab635a02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="addimport-method1"></a><span data-ttu-id="2a0ba-102">AddImport Method1</span><span class="sxs-lookup"><span data-stu-id="2a0ba-102">AddImport Method1</span></span>
<span data-ttu-id="2a0ba-103">アセンブリにインポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-103">Adds imports to the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a0ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="2a0ba-104">Syntax</span></span>  
  
```  
HRESULT AddImport(  
    mdAssembly      AssemblyID,  
    mdToken         ImportToken,  
    DWORD           dwFlags,  
    mdFile*         pFileToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a0ba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a0ba-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2a0ba-106">追加する対象のアセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-106">Unique ID of assembly to be augmented.</span></span>  
  
 `ImportToken`  
 <span data-ttu-id="2a0ba-107">一意の ID から取得[ImportFile メソッド](../../../../docs/framework/unmanaged-api/alink/importfile-method.md)ファイルをインポートするのです。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-107">Unique ID, retrieved from [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), of file to be imported.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2a0ba-108">COM + FileDef フラグなど`ffContainsNoMetaData`と`ffWriteable`です。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-108">COM+ FileDef flags such as `ffContainsNoMetaData` and `ffWriteable`.</span></span> <span data-ttu-id="2a0ba-109">`dwFlags`渡される[DefineFile メソッド](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-109">`dwFlags` is passed to [DefineFile Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
 `pFileToken`  
 <span data-ttu-id="2a0ba-110">トークンへのポインターは、結果のファイルの ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-110">Pointer to token that receives the ID for the resulting file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2a0ba-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="2a0ba-111">Return Value</span></span>  
 <span data-ttu-id="2a0ba-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a0ba-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="2a0ba-113">Requirements</span></span>  
 <span data-ttu-id="2a0ba-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="2a0ba-114">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a0ba-115">参照</span><span class="sxs-lookup"><span data-stu-id="2a0ba-115">See Also</span></span>  
 [<span data-ttu-id="2a0ba-116">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a0ba-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="2a0ba-117">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a0ba-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="2a0ba-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="2a0ba-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
