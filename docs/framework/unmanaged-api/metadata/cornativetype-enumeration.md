---
title: CorNativeType 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b28fe8e8fd8b602a01b6358f46f60cdf792ced0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448626"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="f95e6-102">CorNativeType 列挙型</span><span class="sxs-lookup"><span data-stu-id="f95e6-102">CorNativeType Enumeration</span></span>
<span data-ttu-id="f95e6-103">ネイティブのアンマネージ型を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f95e6-103">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f95e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="f95e6-104">Syntax</span></span>  
  
```  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="f95e6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f95e6-105">Members</span></span>  
  
|<span data-ttu-id="f95e6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f95e6-106">Member</span></span>|<span data-ttu-id="f95e6-107">説明</span><span class="sxs-lookup"><span data-stu-id="f95e6-107">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="f95e6-108">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-108">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="f95e6-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="f95e6-110">0 でなく、FALSE、TRUE がここでは、4 バイト ブール値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-110">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="f95e6-111">8 ビット符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-111">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="f95e6-112">符号なし 8 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-112">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="f95e6-113">16 ビット符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-113">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="f95e6-114">符号なし 16 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-114">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="f95e6-115">符号付き 32 ビット整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-115">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="f95e6-116">32 ビットの符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-116">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="f95e6-117">64 ビット符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-117">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="f95e6-118">64 ビットの符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-118">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="f95e6-119">4 バイト浮動小数点数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-119">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="f95e6-120">8 バイト浮動小数点数値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-120">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="f95e6-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-121">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="f95e6-122">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="f95e6-123">マネージに対応する数値の COM 型<xref:System.Decimal>型です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-123">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="f95e6-124">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-124">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="f95e6-125">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="f95e6-126">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="f95e6-127">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-127">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="f95e6-128">LPSTR、文字列値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-128">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="f95e6-129">LPWSTR、文字列値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-129">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="f95e6-130">LPTSTR、文字列値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-130">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="f95e6-131">固定のシステム定義の文字列値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-131">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="f95e6-132">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-132">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="f95e6-133">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-133">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="f95e6-134">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="f95e6-135">ネイティブ構造体の値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-135">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="f95e6-136">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-136">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="f95e6-137">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="f95e6-138">固定長配列値です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-138">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="f95e6-139">ネイティブの 16 ビット符号付き整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-139">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="f95e6-140">ネイティブの 16 ビット符号なし整数値。</span><span class="sxs-lookup"><span data-stu-id="f95e6-140">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="f95e6-141">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="f95e6-141">Obsolete.</span></span><br /><br /> <span data-ttu-id="f95e6-142">NATIVE_TYPE_STRUCT を使用します。</span><span class="sxs-lookup"><span data-stu-id="f95e6-142">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="f95e6-143">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-143">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="f95e6-144">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="f95e6-145">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-145">COM Interop.</span></span><br /><br /> <span data-ttu-id="f95e6-146">プラットフォームによっては、BSTR、ANSIBSTR またはを選択します。</span><span class="sxs-lookup"><span data-stu-id="f95e6-146">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="f95e6-147">2 バイト ブール値、ここで true の場合は、-1、FALSE は 0。</span><span class="sxs-lookup"><span data-stu-id="f95e6-147">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="f95e6-148">関数ポインター。</span><span class="sxs-lookup"><span data-stu-id="f95e6-148">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="f95e6-149">ネイティブ型への参照。</span><span class="sxs-lookup"><span data-stu-id="f95e6-149">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="f95e6-150">指定されていない型のメンバーを含む配列への参照。</span><span class="sxs-lookup"><span data-stu-id="f95e6-150">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="f95e6-151">構造体への 32 ビット整数ポインター。</span><span class="sxs-lookup"><span data-stu-id="f95e6-151">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="f95e6-152">カスタム マーシャラーのネイティブ型です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-152">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="f95e6-153">次の形式の文字列でこの後にする必要があります:「ネイティブ型の名前/0Custom マーシャラーは、0/名前/0Optional cookie をタイプ」または"{ネイティブ種類を表す GUID}/0Custom マーシャラー型の名前/0Optional cookie/0"</span><span class="sxs-lookup"><span data-stu-id="f95e6-153">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="f95e6-154">COM 相互運用。</span><span class="sxs-lookup"><span data-stu-id="f95e6-154">COM Interop.</span></span><br /><br /> <span data-ttu-id="f95e6-155">ELEMENT_TYPE_I4 では、この型は、VT_HRESULT にマップされます。</span><span class="sxs-lookup"><span data-stu-id="f95e6-155">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="f95e6-156">ネイティブ`IInspectable`型です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-156">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="f95e6-157">ネイティブ`HString`です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-157">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="f95e6-158">値が無効です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-158">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f95e6-159">要件</span><span class="sxs-lookup"><span data-stu-id="f95e6-159">Requirements</span></span>  
 <span data-ttu-id="f95e6-160">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f95e6-160">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f95e6-161">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f95e6-161">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f95e6-162">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f95e6-162">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f95e6-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="f95e6-163">See Also</span></span>  
 <xref:System.Runtime.InteropServices.UnmanagedType>  
 [<span data-ttu-id="f95e6-164">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="f95e6-164">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
