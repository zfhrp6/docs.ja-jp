---
title: EmitAssemblyCustomAttribute メソッド
ms.date: 03/30/2017
api_name:
- IALink.EmitAssemblyCustomAttribute
- EmitAssemblyCustomAttribute
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssemblyCustomAttribute
helpviewer_keywords:
- EmitAssemblyCustomAttribute method
ms.assetid: b72f5409-79af-4fa7-90a7-7630eec170f1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: daf2c3dcaf16e949f8770121d8324cbfe6c7d05b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404080"
---
# <a name="emitassemblycustomattribute-method"></a><span data-ttu-id="6a21d-102">EmitAssemblyCustomAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="6a21d-102">EmitAssemblyCustomAttribute Method</span></span>
<span data-ttu-id="6a21d-103">アセンブリ レベルのカスタム属性を設定する呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="6a21d-103">Call to set assembly-level custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a21d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6a21d-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6a21d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a21d-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6a21d-106">アセンブリの ID です。</span><span class="sxs-lookup"><span data-stu-id="6a21d-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6a21d-107">属性を定義するファイルです。</span><span class="sxs-lookup"><span data-stu-id="6a21d-107">File that defiles the attribute.</span></span> <span data-ttu-id="6a21d-108">場合、NULL を指定できます`AssemblyID`はバインドされていない netmodule を示しません。</span><span class="sxs-lookup"><span data-stu-id="6a21d-108">Can be NULL if `AssemblyID` does not indicate an unbound netmodule.</span></span>  
  
 `tkType`  
 <span data-ttu-id="6a21d-109">カスタム属性の型。</span><span class="sxs-lookup"><span data-stu-id="6a21d-109">Type of the custom attribute.</span></span>  
  
 `pCustomValue`  
 <span data-ttu-id="6a21d-110">カスタム値のデータ。</span><span class="sxs-lookup"><span data-stu-id="6a21d-110">Custom value data.</span></span>  
  
 `cbCustomValue`  
 <span data-ttu-id="6a21d-111">カスタム値のデータの長さです。</span><span class="sxs-lookup"><span data-stu-id="6a21d-111">Length of custom value data.</span></span>  
  
 `bSecurity`  
 <span data-ttu-id="6a21d-112">カスタム属性がアセンブリの署名に関連する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="6a21d-112">TRUE if the custom attribute is related to assembly signing.</span></span>  
  
 `bAllowMulti`  
 <span data-ttu-id="6a21d-113">複数の属性は、出力する場合は TRUE。</span><span class="sxs-lookup"><span data-stu-id="6a21d-113">TRUE if multiple attributes are to be emitted.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6a21d-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="6a21d-114">Return Value</span></span>  
 <span data-ttu-id="6a21d-115">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="6a21d-115">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a21d-116">要件</span><span class="sxs-lookup"><span data-stu-id="6a21d-116">Requirements</span></span>  
 <span data-ttu-id="6a21d-117">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="6a21d-117">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a21d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a21d-118">See Also</span></span>  
 [<span data-ttu-id="6a21d-119">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a21d-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="6a21d-120">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a21d-120">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="6a21d-121">ALink API</span><span class="sxs-lookup"><span data-stu-id="6a21d-121">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
