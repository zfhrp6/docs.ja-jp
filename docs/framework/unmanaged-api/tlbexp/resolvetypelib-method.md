---
title: "ResolveTypeLib メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b668610f50c32373790130def17928b8b3b3d8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="3f38f-102">ResolveTypeLib メソッド</span><span class="sxs-lookup"><span data-stu-id="3f38f-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="3f38f-103">完全修飾パスを返すことによって、タイプ ライブラリの簡易名を解決します。</span><span class="sxs-lookup"><span data-stu-id="3f38f-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f38f-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f38f-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f38f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f38f-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="3f38f-106">[in]A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)タイプ ライブラリの簡易名を格納しています。</span><span class="sxs-lookup"><span data-stu-id="3f38f-106">[in] A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="3f38f-107">[in]レジストリでタイプ ライブラリに割り当てられた GUID です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="3f38f-108">[in]タイプ ライブラリのローカリゼーション ID です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="3f38f-109">[in]タイプ ライブラリのメジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3f38f-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="3f38f-110">たとえば、バージョン*x.y*、メジャー バージョン番号は*x*です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="3f38f-111">[in]タイプ ライブラリのマイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3f38f-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="3f38f-112">たとえば、バージョン*x.y*、マイナー バージョン番号は*y*です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="3f38f-113">[in]A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1)を運用環境を識別するフラグ。</span><span class="sxs-lookup"><span data-stu-id="3f38f-113">[in] A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="3f38f-114">一般的な値は、SYS_WIN32 SYS_WIN64 です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="3f38f-115">[out]ポインター、 [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)という名前で、タイプ ライブラリの完全なパスを含む、`bstrSimpleName`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3f38f-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f38f-116">コメント</span><span class="sxs-lookup"><span data-stu-id="3f38f-116">Remarks</span></span>  
 <span data-ttu-id="3f38f-117">`ResolveTypeLib`メソッドによって呼び出されます、 [LoadTypeLibWithResolver 関数](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)中に[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)を処理します。</span><span class="sxs-lookup"><span data-stu-id="3f38f-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="3f38f-118">このインターフェイスのカスタム実装を返す必要があります、 [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)という名前で、タイプ ライブラリの完全なパスを含む、`bstrSimpleName`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3f38f-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f38f-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="3f38f-119">Requirements</span></span>  
 <span data-ttu-id="3f38f-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3f38f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f38f-121">**ヘッダー:** TlbRef.idl、TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="3f38f-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="3f38f-122">**ライブラリ:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="3f38f-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="3f38f-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f38f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f38f-124">参照</span><span class="sxs-lookup"><span data-stu-id="3f38f-124">See Also</span></span>  
 [<span data-ttu-id="3f38f-125">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="3f38f-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="3f38f-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="3f38f-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/en-us/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
