---
title: "CorTypeAttr 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTypeAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTypeAttr
helpviewer_keywords: CorTypeAttr enumeration [.NET Framework metadata]
ms.assetid: 9bede0ec-5fdf-42a2-b5b7-bee64056acb6
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ab9ce555406dfeb16f99601e6b88af2395c91ae0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="cortypeattr-enumeration"></a><span data-ttu-id="a8e52-102">CorTypeAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="a8e52-102">CorTypeAttr Enumeration</span></span>
<span data-ttu-id="a8e52-103">メタデータ型を示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a8e52-103">Contains values that indicate type metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8e52-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8e52-104">Syntax</span></span>  
  
```  
typedef enum CorTypeAttr {  
  
    tdVisibilityMask        =   0x00000007,  
    tdNotPublic             =   0x00000000,  
    tdPublic                =   0x00000001,  
    tdNestedPublic          =   0x00000002,  
    tdNestedPrivate         =   0x00000003,  
    tdNestedFamily          =   0x00000004,  
    tdNestedAssembly        =   0x00000005,  
    tdNestedFamANDAssem     =   0x00000006,  
    tdNestedFamORAssem      =   0x00000007,  
  
    tdLayoutMask            =   0x00000018,  
    tdAutoLayout            =   0x00000000,  
    tdSequentialLayout      =   0x00000008,  
    tdExplicitLayout        =   0x00000010,  
  
    tdClassSemanticsMask    =   0x00000020,  
    tdClass                 =   0x00000000,  
    tdInterface             =   0x00000020,  
  
    tdAbstract              =   0x00000080,  
    tdSealed                =   0x00000100,  
    tdSpecialName           =   0x00000400,  
  
    tdImport                =   0x00001000,  
    tdSerializable          =   0x00002000,  
    tdWindowsRuntime        =   0x00004000,  
  
    tdStringFormatMask      =   0x00030000,  
    tdAnsiClass             =   0x00000000,  
    tdUnicodeClass          =   0x00010000,  
    tdAutoClass             =   0x00020000,  
    tdCustomFormatClass     =   0x00030000,  
    tdCustomFormatMask      =   0x00C00000,  
  
    tdBeforeFieldInit       =   0x00100000,  
    tdForwarder             =   0x00200000,  
  
    tdReservedMask          =   0x00040800,  
    tdRTSpecialName         =   0x00000800,  
    tdHasSecurity           =   0x00040000,  
  
} CorTypeAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a8e52-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a8e52-105">Members</span></span>  
  
|<span data-ttu-id="a8e52-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a8e52-106">Member</span></span>|<span data-ttu-id="a8e52-107">説明</span><span class="sxs-lookup"><span data-stu-id="a8e52-107">Description</span></span>|  
|------------|-----------------|  
|`tdVisibilityMask`|<span data-ttu-id="a8e52-108">型の可視性の情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-108">Used for type visibility information.</span></span>|  
|`tdNotPublic`|<span data-ttu-id="a8e52-109">型がパブリック スコープでないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-109">Specifies that the type is not in public scope.</span></span>|  
|`tdPublic`|<span data-ttu-id="a8e52-110">型がパブリックのスコープ内であるを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-110">Specifies that the type is in public scope.</span></span>|  
|`tdNestedPublic`|<span data-ttu-id="a8e52-111">型がパブリックの可視性を持つ入れ子になったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-111">Specifies that the type is nested with public visibility.</span></span>|  
|`tdNestedPrivate`|<span data-ttu-id="a8e52-112">型がプライベートの可視性を持つ入れ子になったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-112">Specifies that the type is nested with private visibility.</span></span>|  
|`tdNestedFamily`|<span data-ttu-id="a8e52-113">ファミリの可視性を持つ型が入れ子になったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-113">Specifies that the type is nested with family visibility.</span></span>|  
|`tdNestedAssembly`|<span data-ttu-id="a8e52-114">アセンブリの可視性を持つ型が入れ子になったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-114">Specifies that the type is nested with assembly visibility.</span></span>|  
|`tdNestedFamANDAssem`|<span data-ttu-id="a8e52-115">型が属するファミリとアセンブリの可視性を持つ入れ子になっているを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-115">Specifies that the type is nested with family and assembly visibility.</span></span>|  
|`tdNestedFamORAssem`|<span data-ttu-id="a8e52-116">ファミリまたはアセンブリの可視性を持つ型が入れ子になったことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-116">Specifies that the type is nested with family or assembly visibility.</span></span>|  
|`tdLayoutMask`|<span data-ttu-id="a8e52-117">型のレイアウト情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-117">Gets layout information for the type.</span></span>|  
|`tdAutoLayout`|<span data-ttu-id="a8e52-118">この型のフィールドが自動的にレイアウトされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-118">Specifies that the fields of this type are laid out automatically.</span></span>|  
|`tdSequentialLayout`|<span data-ttu-id="a8e52-119">この型のフィールドが順番にレイアウトするかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-119">Specifies that the fields of this type are laid out sequentially.</span></span>|  
|`tdExplicitLayout`|<span data-ttu-id="a8e52-120">そのフィールドのレイアウトが明示的に指定されたを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-120">Specifies that field layout is supplied explicitly.</span></span>|  
|`tdClassSemanticsMask`|<span data-ttu-id="a8e52-121">型のセマンティクス情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-121">Gets semantic information about the type.</span></span>|  
|`tdClass`|<span data-ttu-id="a8e52-122">型がクラスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-122">Specifies that the type is a class.</span></span>|  
|`tdInterface`|<span data-ttu-id="a8e52-123">型がインターフェイスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-123">Specifies that the type is an interface.</span></span>|  
|`tdAbstract`|<span data-ttu-id="a8e52-124">型が抽象的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-124">Specifies that the type is abstract.</span></span>|  
|`tdSealed`|<span data-ttu-id="a8e52-125">型を拡張できないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-125">Specifies that the type cannot be extended.</span></span>|  
|`tdSpecialName`|<span data-ttu-id="a8e52-126">クラスの名前が特別なことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-126">Specifies that the class name is special.</span></span> <span data-ttu-id="a8e52-127">その名前で記述する方法です。</span><span class="sxs-lookup"><span data-stu-id="a8e52-127">Its name describes how.</span></span>|  
|`tdImport`|<span data-ttu-id="a8e52-128">型がインポートされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-128">Specifies that the type is imported.</span></span>|  
|`tdSerializable`|<span data-ttu-id="a8e52-129">型がシリアル化可能なことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-129">Specifies that the type is serializable.</span></span>|  
|`tdWindowsRuntime`|<span data-ttu-id="a8e52-130">この型があることを指定します、[!INCLUDE[wrt](../../../../includes/wrt-md.md)]型です。</span><span class="sxs-lookup"><span data-stu-id="a8e52-130">Specifies that this type is a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`tdStringFormatMask`|<span data-ttu-id="a8e52-131">文字列のエンコード方法および書式設定方法に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-131">Gets information about how strings are encoded and formatted.</span></span>|  
|`tdAnsiClass`|<span data-ttu-id="a8e52-132">この型が、ANSI として LPTSTR を解釈するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-132">Specifies that this type interprets an LPTSTR as ANSI.</span></span>|  
|`tdUnicodeClass`|<span data-ttu-id="a8e52-133">この型が Unicode として LPTSTR を解釈するように指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-133">Specifies that this type interprets an LPTSTR as Unicode.</span></span>|  
|`tdAutoClass`|<span data-ttu-id="a8e52-134">この型が自動的に LPTSTR を解釈することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-134">Specifies that this type interprets an LPTSTR automatically.</span></span>|  
|`tdCustomFormatClass`|<span data-ttu-id="a8e52-135">型が非標準のエンコーディングを指定して指定されたとおり`CustomFormatMask`です。</span><span class="sxs-lookup"><span data-stu-id="a8e52-135">Specifies that the type has a non-standard encoding, as specified by `CustomFormatMask`.</span></span>|  
|`tdCustomFormatMask`|<span data-ttu-id="a8e52-136">このマスクを使用すると、ネイティブの相互運用機能の非標準のエンコード情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="a8e52-136">Use this mask to get non-standard encoding information for native interop.</span></span> <span data-ttu-id="a8e52-137">これらの 2 つのビット値の意味は、指定されていません。</span><span class="sxs-lookup"><span data-stu-id="a8e52-137">The meaning of the values of these two bits is unspecified.</span></span>|  
|`tdBeforeFieldInit`|<span data-ttu-id="a8e52-138">静的フィールドにアクセスする最初の試行する前に、型を初期化する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-138">Specifies that the type must be initialized before the first attempt to access a static field.</span></span>|  
|`tdForwarder`|<span data-ttu-id="a8e52-139">型がエクスポートになっていることを指定し、型フォワーダーです。</span><span class="sxs-lookup"><span data-stu-id="a8e52-139">Specifies that the type is exported, and a type forwarder.</span></span>|  
|`tdReservedMask`|<span data-ttu-id="a8e52-140">このフラグは、以下のフラグは、共通言語ランタイムによって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a8e52-140">This flag and the flags below are used internally by the common language runtime.</span></span>|  
|`tdRTSpecialName`|<span data-ttu-id="a8e52-141">名前のエンコーディングに共通言語ランタイムが確認する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-141">Specifies that the common language runtime should check the name encoding.</span></span>|  
|`tdHasSecurity`|<span data-ttu-id="a8e52-142">型が関連付けられているセキュリティを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8e52-142">Specifies that the type has security associated with it.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8e52-143">要件</span><span class="sxs-lookup"><span data-stu-id="a8e52-143">Requirements</span></span>  
 <span data-ttu-id="a8e52-144">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a8e52-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8e52-145">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a8e52-145">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a8e52-146">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8e52-146">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e52-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8e52-147">See Also</span></span>  
 [<span data-ttu-id="a8e52-148">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="a8e52-148">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
