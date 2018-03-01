---
title: "SetAssemblyFile2 メソッド"
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
- IALink2.SetAssemblyFile2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetAssemblyFile2
helpviewer_keywords:
- SetAssemblyFile2 method
ms.assetid: eedb9125-1ef1-4000-abfc-7de86e5a1f17
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 671fb857015a5babd388366066d282cb87462c18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="setassemblyfile2-method"></a><span data-ttu-id="1e799-102">SetAssemblyFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="1e799-102">SetAssemblyFile2 Method</span></span>
<span data-ttu-id="1e799-103">名前と新しいアセンブリのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="1e799-103">Sets the name of and options for a new assembly.</span></span> <span data-ttu-id="1e799-104">非バインド モジュールを作成する際に、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="1e799-104">Do not call this method when you produce unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e799-105">構文</span><span class="sxs-lookup"><span data-stu-id="1e799-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile2(  
    LPCWSTR pszFilename,  
    IMetaDataEmit2* pEmitter,  
    AssemblyFlags   afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e799-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1e799-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="1e799-107">マニフェスト ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="1e799-107">Name of manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="1e799-108">[IMetaDataEmit2 インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)このファイルのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1e799-108">[IMetaDataEmit2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md) interface for this file.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="1e799-109">によって表されるオプション[AssemblyFlags 列挙体](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md)です。</span><span class="sxs-lookup"><span data-stu-id="1e799-109">Options represented by [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="1e799-110">構築されるアセンブリの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="1e799-110">Receives unique ID for the assembly being constructed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e799-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="1e799-111">Return Value</span></span>  
 <span data-ttu-id="1e799-112">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="1e799-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e799-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="1e799-113">Requirements</span></span>  
 <span data-ttu-id="1e799-114">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="1e799-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e799-115">参照</span><span class="sxs-lookup"><span data-stu-id="1e799-115">See Also</span></span>  
 [<span data-ttu-id="1e799-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e799-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1e799-117">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1e799-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1e799-118">ALink API</span><span class="sxs-lookup"><span data-stu-id="1e799-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
