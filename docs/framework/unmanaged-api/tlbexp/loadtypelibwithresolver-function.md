---
title: "LoadTypeLibWithResolver 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadTypeLibWithResolver
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: LoadTypeLibWithResolver
helpviewer_keywords: LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0241745396ab01a777eef6e3b88e4c12bdd8b429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="62eab-102">LoadTypeLibWithResolver 関数</span><span class="sxs-lookup"><span data-stu-id="62eab-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="62eab-103">タイプ ライブラリの読み込みを使用して、指定された[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)内部的に参照されるタイプ ライブラリを解決するのには。</span><span class="sxs-lookup"><span data-stu-id="62eab-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62eab-104">構文</span><span class="sxs-lookup"><span data-stu-id="62eab-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62eab-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62eab-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="62eab-106">[in]タイプ ライブラリのファイル パス。</span><span class="sxs-lookup"><span data-stu-id="62eab-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="62eab-107">[in]A [REGKIND 列挙](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx)タイプ ライブラリを登録する方法を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="62eab-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="62eab-108">その有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="62eab-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="62eab-109">`REGKIND_DEFAULT`: 既定の登録の動作を使用します。</span><span class="sxs-lookup"><span data-stu-id="62eab-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="62eab-110">`REGKIND_REGISTER`: このタイプ ライブラリを登録します。</span><span class="sxs-lookup"><span data-stu-id="62eab-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="62eab-111">`REGKIND_NONE`: このタイプ ライブラリを登録できませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="62eab-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="62eab-112">[in]実装へのポインター、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="62eab-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="62eab-113">[out]読み込まれているタイプ ライブラリへの参照。</span><span class="sxs-lookup"><span data-stu-id="62eab-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62eab-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="62eab-114">Return Value</span></span>  
 <span data-ttu-id="62eab-115">次の表に、HRESULT 値の 1 つ。</span><span class="sxs-lookup"><span data-stu-id="62eab-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="62eab-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="62eab-116">Return value</span></span>|<span data-ttu-id="62eab-117">説明</span><span class="sxs-lookup"><span data-stu-id="62eab-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="62eab-118">成功。</span><span class="sxs-lookup"><span data-stu-id="62eab-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="62eab-119">メモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="62eab-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="62eab-120">1 つ以上のポインターが有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="62eab-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="62eab-121">1 つ以上の引数が有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="62eab-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="62eab-122">関数は、ファイルに書き込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="62eab-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="62eab-123">システムの登録データベースは開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="62eab-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="62eab-124">タイプ ライブラリを開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="62eab-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="62eab-125">タイプ ライブラリまたは DLL を読み込むことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="62eab-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62eab-126">コメント</span><span class="sxs-lookup"><span data-stu-id="62eab-126">Remarks</span></span>  
 <span data-ttu-id="62eab-127">[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)呼び出し、`LoadTypeLibWithResolver`アセンブリをタイプ ライブラリへの変換処理中に機能します。</span><span class="sxs-lookup"><span data-stu-id="62eab-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="62eab-128">この関数は、レジストリに最小限のアクセス権を持つ指定したタイプ ライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="62eab-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="62eab-129">関数は、内部的に参照されるタイプ ライブラリ、それぞれが読み込まれ、親のタイプ ライブラリに追加する必要がありますのタイプ ライブラリを調べます。</span><span class="sxs-lookup"><span data-stu-id="62eab-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="62eab-130">参照タイプ ライブラリを読み込むことができます、前に、ファイルの完全パスにファイルのパスを参照を解決する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62eab-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="62eab-131">これを使用、 [ResolveTypeLib メソッド](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)はによって提供される、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)に渡される、`pTlbResolver`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="62eab-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="62eab-132">参照タイプ ライブラリの完全ファイル パスがわかっている場合、`LoadTypeLibWithResolver`関数を読み込んで、参照されるタイプ ライブラリ、親の種類をライブラリに追加、組み合わされたマスター型ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="62eab-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="62eab-133">解決されたマスター タイプ ライブラリへの参照を解決してすべての内部で参照されているタイプ ライブラリを読み込むと、関数を返します、`pptlib`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="62eab-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="62eab-134">`LoadTypeLibWithResolver`関数一般に、 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、独自の内部を供給する[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)での実装、 `pTlbResolver`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="62eab-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="62eab-135">呼び出す場合`LoadTypeLibWithResolver`を直接指定する必要あります独自[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)実装します。</span><span class="sxs-lookup"><span data-stu-id="62eab-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62eab-136">要件</span><span class="sxs-lookup"><span data-stu-id="62eab-136">Requirements</span></span>  
 <span data-ttu-id="62eab-137">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="62eab-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62eab-138">**ヘッダー:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="62eab-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="62eab-139">**ライブラリ:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="62eab-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="62eab-140">**.NET framework のバージョン:** 3.5、3.0、2.0</span><span class="sxs-lookup"><span data-stu-id="62eab-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62eab-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="62eab-141">See Also</span></span>  
 [<span data-ttu-id="62eab-142">Tlbexp ヘルパー関数します。</span><span class="sxs-lookup"><span data-stu-id="62eab-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="62eab-143">[LoadTypeLibEx 関数](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="62eab-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>
