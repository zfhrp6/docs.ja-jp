---
title: "EmitAssemblyCustomAttribute メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssemblyCustomAttribute
helpviewer_keywords: EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cc7709ef060642f12a8bc7d048e520427a5c674
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="13e62-102">EmitAssemblyCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="13e62-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="13e62-103">アセンブリ レベルのカスタム属性を設定する呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="13e62-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13e62-104">構文</span><span class="sxs-lookup"><span data-stu-id="13e62-104">Syntax</span></span>  
  
```  
HRESULT EmitAssemblyCustomAttribute(  
    mdAssembly   AssemblyID,  
    mdToken      FileToken,  
    mdToken      tkType,  
    void const*  pCustomValue,  
    DWORD        cbCustomValue,  
    BOOL         bSecurity,  
    BOOL         bAllowMulti  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13e62-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13e62-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="13e62-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="13e62-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="13e62-107">属性を定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="13e62-107">File that defiles the attribute.</span></span> <span data-ttu-id="13e62-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="13e62-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="13e62-109">カスタム属性の型。</span><span class="sxs-lookup"><span data-stu-id="13e62-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="13e62-110">カスタム値のデータ。</span><span class="sxs-lookup"><span data-stu-id="13e62-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="13e62-111">カスタム値のデータの長さです。</span><span class="sxs-lookup"><span data-stu-id="13e62-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="13e62-112">カスタム属性がアセンブリの署名に関連する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="13e62-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="13e62-113">複数の属性は、出力する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="13e62-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13e62-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="13e62-114">Return Value</span></span>  
 <span data-ttu-id="13e62-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="13e62-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13e62-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="13e62-116">Requirements</span></span>  
 <span data-ttu-id="13e62-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="13e62-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e62-118">参照</span><span class="sxs-lookup"><span data-stu-id="13e62-118">See Also</span></span>  
 [<span data-ttu-id="13e62-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13e62-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="13e62-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13e62-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="13e62-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="13e62-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
