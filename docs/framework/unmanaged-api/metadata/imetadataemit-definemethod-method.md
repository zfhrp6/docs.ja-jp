---
title: IMetaDataEmit::DefineMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 53fd830cdefda58d40f96f8662a80d1888d963dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449200"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="4bb7f-102">IMetaDataEmit::DefineMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="4bb7f-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="4bb7f-103">指定したシグネチャを持つメソッドまたはグローバル関数の定義を作成し、そのメソッドの定義にトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb7f-104">構文</span><span class="sxs-lookup"><span data-stu-id="4bb7f-104">Syntax</span></span>  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bb7f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bb7f-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4bb7f-106">[in]`mdTypedef`親クラスまたはメソッドの親インターフェイスのトークン。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="4bb7f-107">設定`td`に`mdTokenNil`グローバル関数を定義している場合、します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="4bb7f-108">[in]Unicode でメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="4bb7f-109">[in]値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)メソッドまたはグローバル関数の属性を指定する列挙体です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4bb7f-110">[in]メソッドのシグネチャ。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-110">[in] The method signature.</span></span> <span data-ttu-id="4bb7f-111">提供された、署名が保持されます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="4bb7f-112">すべてのパラメーターの追加情報を指定する必要がある場合を使用して、 [imetadataemit::setparamprops](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4bb7f-113">[in]内のバイト数`pvSigBlob`です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="4bb7f-114">[in]コードのアドレス。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="4bb7f-115">[in]値、 [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md)メソッドの実装の機能を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="4bb7f-116">[out]メンバー トークンです。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bb7f-117">コメント</span><span class="sxs-lookup"><span data-stu-id="4bb7f-117">Remarks</span></span>  
 <span data-ttu-id="4bb7f-118">メタデータ API が、呼び出し元を出力に指定された外側のクラスまたはインターフェイスで指定されているのと同じ順序のメソッドを保持するには、`td`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="4bb7f-119">使用に関する追加情報`DefineMethod`し、特定のパラメーターの設定のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="4bb7f-120">V テーブル内のスロット</span><span class="sxs-lookup"><span data-stu-id="4bb7f-120">Slots in the V-table</span></span>  
 <span data-ttu-id="4bb7f-121">ランタイムでは、メソッド定義を使用して、v-table スロットを設定します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="4bb7f-122">1 つまたは複数のスロットがスキップする必要がある場合、COM インターフェイスのレイアウトと同等の機能を保持する場合など、ダミー メソッドが定義されて v テーブル内のスロットを使用して設定、`dwMethodFlags`を`mdRTSpecialName`の値、 [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md)列挙として名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="4bb7f-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="4bb7f-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>  
  
 <span data-ttu-id="4bb7f-124">ここで*SequenceNumber*メソッドのシーケンス番号と*CountOfSlots* v-table でスキップするスロットの数です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="4bb7f-125">場合*CountOfSlots*は省略すると、1 と見なされます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="4bb7f-126">これらのダミー メソッドはマネージまたはアンマネージ コードから呼び出すことであり、これらをマネージまたはアンマネージ コードから呼び出すしようとすると、例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="4bb7f-127">唯一の目的は、COM 統合サービスのランタイムを生成する v テーブルの領域を占有します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="4bb7f-128">重複したメソッド</span><span class="sxs-lookup"><span data-stu-id="4bb7f-128">Duplicate Methods</span></span>  
 <span data-ttu-id="4bb7f-129">重複したメソッドを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-129">You should not define duplicate methods.</span></span> <span data-ttu-id="4bb7f-130">つまり、呼び出す必要はありません`DefineMethod`重複する一連の値の`td`、 `wzName`、および`pvSig`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="4bb7f-131">(これら 3 つのパラメーターを一意にメソッドを定義します。)。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="4bb7f-132">設定されているのいずれかのメソッドの定義で、重複する 3 つの要素を使用するただし、`mdPrivateScope`ビット、`dwMethodFlags`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="4bb7f-133">(、`mdPrivateScope`ビットは、コンパイラはこのメソッドの定義への参照を出力していないことを意味します)。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="4bb7f-134">メソッドの実装について</span><span class="sxs-lookup"><span data-stu-id="4bb7f-134">Method Implementation Information</span></span>  
 <span data-ttu-id="4bb7f-135">メソッドの実装に関する情報は、ほとんどの場合、メソッドの宣言時に呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="4bb7f-136">そのため、必要はありませんで値を渡す、`ulCodeRVA`と`dwImplFlags`パラメーターを呼び出すときに`DefineMethod`です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="4bb7f-137">後でを通じて値を指定することができます[imetadataemit::setmethodimplflags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md)または[imetadataemit::setrva](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="4bb7f-138">プラットフォーム呼び出し (PInvoke) または COM 相互運用のシナリオなど、いくつかの状況で、メソッドの本体は指定しないで、および`ulCodeRVA`を 0 に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="4bb7f-139">これらの状況でメソッドいないタグ付けするか抽象として、ランタイムは、実装を見つけるためです。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="4bb7f-140">PInvoke のメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="4bb7f-141">PInvoke によって呼び出される各アンマネージ関数の場合には、対象のアンマネージ関数を表すマネージ メソッドを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="4bb7f-142">マネージ メソッドを定義するのには、使用`DefineMethod`PInvoke を使用する方法に応じて、特定の値に設定されたパラメーターの一部を。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="4bb7f-143">PInvoke の true - アンマネージ DLL 内にある外部のアンマネージ メソッドの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="4bb7f-144">ローカル PInvoke - には、現在のマネージ モジュールに埋め込まれているネイティブのアンマネージ メソッドの呼び出しが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="4bb7f-145">パラメーターの設定は、次の表で表されます。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="4bb7f-146">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bb7f-146">Parameter</span></span>|<span data-ttu-id="4bb7f-147">True の PInvoke の値</span><span class="sxs-lookup"><span data-stu-id="4bb7f-147">Values for true PInvoke</span></span>|<span data-ttu-id="4bb7f-148">ローカルの PInvoke の値</span><span class="sxs-lookup"><span data-stu-id="4bb7f-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="4bb7f-149">設定`mdStatic`クリア;`mdSynchronized`と`mdAbstract`です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="4bb7f-150">有効な共通言語ランタイム (CLR) メソッドのシグネチャに無効なパラメーターはマネージ型です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="4bb7f-151">有効なパラメーターを持つ有効な CLR メソッドのシグネチャはマネージ型です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="4bb7f-152">0</span><span class="sxs-lookup"><span data-stu-id="4bb7f-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="4bb7f-153">設定`miCil`と`miManaged`です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="4bb7f-154">設定`miNative`と`miUnmanaged`です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bb7f-155">要件</span><span class="sxs-lookup"><span data-stu-id="4bb7f-155">Requirements</span></span>  
 <span data-ttu-id="4bb7f-156">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4bb7f-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb7f-157">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4bb7f-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4bb7f-158">**ライブラリ:** MSCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4bb7f-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bb7f-159">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb7f-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb7f-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bb7f-160">See Also</span></span>  
 [<span data-ttu-id="4bb7f-161">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bb7f-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="4bb7f-162">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bb7f-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
