---
title: CorElementType Enumeration1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorElementType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorElementType
helpviewer_keywords: CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 00f4aa4e87c0deb4b1326cb8bf4256a9307b3393
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corelementtype-enumeration1"></a><span data-ttu-id="b5bae-102">CorElementType Enumeration1</span><span class="sxs-lookup"><span data-stu-id="b5bae-102">CorElementType Enumeration1</span></span>
<span data-ttu-id="b5bae-103">共通言語ランタイムを指定<xref:System.Type>、型修飾子、またはメタデータ型シグネチャに型に関する情報。</span><span class="sxs-lookup"><span data-stu-id="b5bae-103">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5bae-104">構文</span><span class="sxs-lookup"><span data-stu-id="b5bae-104">Syntax</span></span>  
  
```  
typedef enum CorElementType {  
    ELEMENT_TYPE_END            = 0x0,  
    ELEMENT_TYPE_VOID           = 0x1,  
    ELEMENT_TYPE_BOOLEAN        = 0x2,  
    ELEMENT_TYPE_CHAR           = 0x3,  
    ELEMENT_TYPE_I1             = 0x4,  
    ELEMENT_TYPE_U1             = 0x5,  
    ELEMENT_TYPE_I2             = 0x6,  
    ELEMENT_TYPE_U2             = 0x7,  
    ELEMENT_TYPE_I4             = 0x8,  
    ELEMENT_TYPE_U4             = 0x9,  
    ELEMENT_TYPE_I8             = 0xa,  
    ELEMENT_TYPE_U8             = 0xb,  
    ELEMENT_TYPE_R4             = 0xc,  
    ELEMENT_TYPE_R8             = 0xd,  
    ELEMENT_TYPE_STRING         = 0xe,  
  
    ELEMENT_TYPE_PTR            = 0xf,  
    ELEMENT_TYPE_BYREF          = 0x10,  
  
    ELEMENT_TYPE_VALUETYPE      = 0x11,  
    ELEMENT_TYPE_CLASS          = 0x12,  
    ELEMENT_TYPE_VAR            = 0x13,  
    ELEMENT_TYPE_ARRAY          = 0x14,  
    ELEMENT_TYPE_GENERICINST    = 0x15,  
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,  
  
    ELEMENT_TYPE_I              = 0x18,  
    ELEMENT_TYPE_U              = 0x19,  
    ELEMENT_TYPE_FNPTR          = 0x1B,  
    ELEMENT_TYPE_OBJECT         = 0x1C,  
    ELEMENT_TYPE_SZARRAY        = 0x1D,  
    ELEMENT_TYPE_MVAR           = 0x1e,  
  
    ELEMENT_TYPE_CMOD_REQD      = 0x1F,  
    ELEMENT_TYPE_CMOD_OPT       = 0x20,  
  
    ELEMENT_TYPE_INTERNAL       = 0x21,  
    ELEMENT_TYPE_MAX            = 0x22,  
  
    ELEMENT_TYPE_MODIFIER       = 0x40,  
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,  
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER  
  
} CorElementType;  
```  
  
## <a name="members"></a><span data-ttu-id="b5bae-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b5bae-105">Members</span></span>  
  
|<span data-ttu-id="b5bae-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b5bae-106">Member</span></span>|<span data-ttu-id="b5bae-107">説明</span><span class="sxs-lookup"><span data-stu-id="b5bae-107">Description</span></span>|  
|------------|-----------------|  
|`ELEMENT_TYPE_END`|<span data-ttu-id="b5bae-108">内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bae-108">Used internally.</span></span>|  
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="b5bae-109">Void 型です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-109">A void type.</span></span>|  
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="b5bae-110">Boolean 型</span><span class="sxs-lookup"><span data-stu-id="b5bae-110">A Boolean type</span></span>|  
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="b5bae-111">文字型。</span><span class="sxs-lookup"><span data-stu-id="b5bae-111">A character type.</span></span>|  
|`ELEMENT_TYPE_I1`|<span data-ttu-id="b5bae-112">1 バイトの符号付き整数の場合。</span><span class="sxs-lookup"><span data-stu-id="b5bae-112">A signed 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_U1`|<span data-ttu-id="b5bae-113">1 バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-113">An unsigned 1-byte integer.</span></span>|  
|`ELEMENT_TYPE_I2`|<span data-ttu-id="b5bae-114">2 バイトの符号付き整数ではします。</span><span class="sxs-lookup"><span data-stu-id="b5bae-114">A signed 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_U2`|<span data-ttu-id="b5bae-115">2 バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-115">An unsigned 2-byte integer.</span></span>|  
|`ELEMENT_TYPE_I4`|<span data-ttu-id="b5bae-116">符号付きの 4 バイト整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-116">A signed 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_U4`|<span data-ttu-id="b5bae-117">4 バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-117">An unsigned 4-byte integer.</span></span>|  
|`ELEMENT_TYPE_I8`|<span data-ttu-id="b5bae-118">符号付き 8 バイト整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-118">A signed 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_U8`|<span data-ttu-id="b5bae-119">8 バイトの符号なし整数。</span><span class="sxs-lookup"><span data-stu-id="b5bae-119">An unsigned 8-byte integer.</span></span>|  
|`ELEMENT_TYPE_R4`|<span data-ttu-id="b5bae-120">4 バイト浮動小数点。</span><span class="sxs-lookup"><span data-stu-id="b5bae-120">A 4-byte floating point.</span></span>|  
|`ELEMENT_TYPE_R8`|<span data-ttu-id="b5bae-121">8 バイト浮動小数点。</span><span class="sxs-lookup"><span data-stu-id="b5bae-121">An 8-byte floating point.</span></span>|  
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="b5bae-122">System.String 型。</span><span class="sxs-lookup"><span data-stu-id="b5bae-122">A System.String type.</span></span>|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="b5bae-123">ポインター型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-123">A pointer type modifier.</span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="b5bae-124">参照の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-124">A reference type modifier.</span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="b5bae-125">値の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-125">A value type modifier.</span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="b5bae-126">クラスの型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-126">A class type modifier.</span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="b5bae-127">クラスの変数の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-127">A class variable type modifier.</span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="b5bae-128">多次元配列の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-128">A multi-dimensional array type modifier.</span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="b5bae-129">ジェネリック型の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-129">A type modifier for generic types.</span></span>|  
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="b5bae-130">型指定された参照。</span><span class="sxs-lookup"><span data-stu-id="b5bae-130">A typed reference.</span></span>|  
|`ELEMENT_TYPE_I`|<span data-ttu-id="b5bae-131">ネイティブの整数のサイズです。</span><span class="sxs-lookup"><span data-stu-id="b5bae-131">Size of a native integer.</span></span>|  
|`ELEMENT_TYPE_U`|<span data-ttu-id="b5bae-132">ネイティブの符号なし整数のサイズです。</span><span class="sxs-lookup"><span data-stu-id="b5bae-132">Size of an unsigned native integer.</span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="b5bae-133">関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b5bae-133">A pointer to a function.</span></span>|  
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="b5bae-134">System.Object 型です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-134">A System.Object type.</span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="b5bae-135">1 次元、0 の配列の下限の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-135">A single-dimensional, zero lower-bound array type modifier.</span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="b5bae-136">メソッドの変数の型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-136">A method variable type modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="b5bae-137">C 言語には、修飾子が必要です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-137">A C language required modifier.</span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="b5bae-138">C 言語の省略可能な修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-138">A C language optional modifier.</span></span>|  
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="b5bae-139">内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bae-139">Used internally.</span></span>|  
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="b5bae-140">無効な型。</span><span class="sxs-lookup"><span data-stu-id="b5bae-140">An invalid type.</span></span>|  
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="b5bae-141">内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bae-141">Used internally.</span></span>|  
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="b5bae-142">可変個のパラメーターの一覧については、sentinel 型修飾子です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-142">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|  
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="b5bae-143">内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5bae-143">Used internally.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b5bae-144">コメント</span><span class="sxs-lookup"><span data-stu-id="b5bae-144">Remarks</span></span>  
 <span data-ttu-id="b5bae-145">型修飾子より複雑な型を表すの基礎を成しています。</span><span class="sxs-lookup"><span data-stu-id="b5bae-145">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="b5bae-146">A`CorElementType`型修飾子の値が型シグネチャに直後にある値に適用します。</span><span class="sxs-lookup"><span data-stu-id="b5bae-146">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="b5bae-147">これに続く値、`CorElementType`型修飾子の値を指定できます、`CorElementType`単純型の値、メタデータ トークン、またはその他の値は、次の表で指定されています。</span><span class="sxs-lookup"><span data-stu-id="b5bae-147">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5bae-148">すべての数値 (*数*、*引数カウント*、*メタデータ トークン*、*ランク*、*カウント*、および*バインド*) 圧縮された整数値として格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5bae-148">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="b5bae-149">参照してください[標準 ECMA 335 - 共通言語基盤 (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487)詳細については、ECMA Web サイトにします。</span><span class="sxs-lookup"><span data-stu-id="b5bae-149">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=116487) on the ECMA Web site for details.</span></span>  
  
|<span data-ttu-id="b5bae-150">型修飾子</span><span class="sxs-lookup"><span data-stu-id="b5bae-150">Type modifier</span></span>|<span data-ttu-id="b5bae-151">形式</span><span class="sxs-lookup"><span data-stu-id="b5bae-151">Format</span></span>|  
|-------------------|------------|  
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="b5bae-152">ELEMENT_TYPE_PTR <、`CorElementType`値 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-152">ELEMENT_TYPE_PTR <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="b5bae-153">ELEMENT_TYPE_BYREF <、`CorElementType`値 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-153">ELEMENT_TYPE_BYREF <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="b5bae-154">ELEMENT_TYPE_VALUETYPE <、`mdTypeDef`メタデータ トークン ></span><span class="sxs-lookup"><span data-stu-id="b5bae-154">ELEMENT_TYPE_VALUETYPE <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="b5bae-155">ELEMENT_TYPE_CLASS <、`mdTypeDef`メタデータ トークン ></span><span class="sxs-lookup"><span data-stu-id="b5bae-155">ELEMENT_TYPE_CLASS <an `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="b5bae-156">ELEMENT_TYPE_VAR\<番号 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-156">ELEMENT_TYPE_VAR \<number></span></span>|  
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="b5bae-157">ELEMENT_TYPE_ARRAY <、`CorElementType`値 >\<ランク > \<count1 > \<bound1 >.\<countN > \<boundN ></span><span class="sxs-lookup"><span data-stu-id="b5bae-157">ELEMENT_TYPE_ARRAY <a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|  
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="b5bae-158">ELEMENT_TYPE_GENERICINST <、`mdTypeDef`メタデータ トークン >\<引数カウント > \<arg1 >.\<argN ></span><span class="sxs-lookup"><span data-stu-id="b5bae-158">ELEMENT_TYPE_GENERICINST <an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|  
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="b5bae-159">ELEMENT_TYPE_FNPTR\<関数では呼び出し規約を含む完全な署名 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-159">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|  
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="b5bae-160">インポートする場合 <、`CorElementType`値 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-160">ELEMENT_TYPE_SZARRAY <a `CorElementType` value></span></span>|  
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="b5bae-161">ELEMENT_TYPE_MVAR\<番号 ></span><span class="sxs-lookup"><span data-stu-id="b5bae-161">ELEMENT_TYPE_MVAR \<number></span></span>|  
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="b5bae-162">ELEMENT_TYPE <、`mdTypeRef`または`mdTypeDef`メタデータ トークン ></span><span class="sxs-lookup"><span data-stu-id="b5bae-162">ELEMENT_TYPE_<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="b5bae-163">E_T_CMOD_OPT <、`mdTypeRef`または`mdTypeDef`メタデータ トークン ></span><span class="sxs-lookup"><span data-stu-id="b5bae-163">E_T_CMOD_OPT <a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5bae-164">必要条件</span><span class="sxs-lookup"><span data-stu-id="b5bae-164">Requirements</span></span>  
 <span data-ttu-id="b5bae-165">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5bae-165">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5bae-166">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b5bae-166">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b5bae-167">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5bae-167">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5bae-168">参照</span><span class="sxs-lookup"><span data-stu-id="b5bae-168">See Also</span></span>  
 [<span data-ttu-id="b5bae-169">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="b5bae-169">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
